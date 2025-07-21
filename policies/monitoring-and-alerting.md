# Monitoring and Alerting

We are currently using Pushover and UptimeKuma for server & service monitoring

## Pushover

| **Alert Type** | **Notification**                      |
| -------------- | ------------------------------------- |
| -2             | No notification, displays in app      |
| -1             | No notification, displays in app      |
| 0              | Notification during active hours only |
| 1              | Always notify                         |
| 2              | Always notify                         |

If the service can integrate with Pushover;

* Configure 2 notifiers if possible
  * Low priority
  * High priority (if only 1 possible, configure high priority)
* Set up alerts for notifiers
  * Low priority can be used for
    * Services that will cause minimal impact
    * Low urgency alerts
    * Alerts that are good to have, but may be common
  * High priority can be used for
    * Services with public impact
    * Services that will cause an outage (eg DNS)
    * Outages

_Some services can integrate with Pushover via other methods, such as the text message API or SMTP. These should only be used for priority 0 and above._

#### Why?

This allows alerts to be sent to my mobile phone and categorizes them. Depending on the time, some alerts will be silent and others will make sound

***

## UptimeKuma

All UptimeKuma monitors should be set as below. This reduces spam to Pushover as well as resource load

| **Setting**              | **Value**                |
| ------------------------ | ------------------------ |
| Time in Seconds          | 120                      |
| Retry count before error | 3                        |
| Pushover                 | Priority based on impact |

### Status Pages

We currently have 3 status pages,

* [LatteMedia](https://status.lattemedia.tv)
* [A Gamers Grind](https://status.agamersgrind.com)
* [XFGN](https://xfgn.dev)

### Maintenance Periods

Maintenance periods should be set before the potential service outage, with the relevant monitors selected

Consistent maintenance periods, like the 4:30PM daily update schedule, can be scheduled and automated in Kuma

#### Why?

Consistent approach to notifications and monitoring

Display the right data on the right status page

***

## Email Notifications

Email notifications should be set up using SMTP, please refer to the below generic config

```
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
EMAIL_SENDER_ADDRESS=                          #Refer to the list of emails below
EMAIL_SENDER_NAME=
SMTP_SECURE=starttls
SMTP_USERNAME=lattemediadottv@gmail.com        #generic gmail account for SMTP
SMTP_PASSWORD=                                 #creds in BW
```

<table><thead><tr><th>LatteMedia Services</th><th width="238">XFGN Services</th><th>AGG Services</th></tr></thead><tbody><tr><td>noreply@lattemedia.tv</td><td>noreply@xfgn.dev</td><td>noreply@agamersgrind.com</td></tr></tbody></table>

#### Why?

This allows us to email users from a single account. Per the email address, it also notifies them that they will not recieve a response.

***

## NetData

Netdata is a distributed real-time, health monitoring platform for systems, hardware, containers & applications, collecting metrics.

Netdata alerts are sent to Pushover

#### Why?

This is to allow us to keep ahead of issues in the network and resolve them before they affect any public facing services
