# Port Forwarding or Tunneling a Service

This guide will step you through Port Forwarding or Tunneling a service

## Required Knowledge

[external-access-to-systems.md](../policies/external-access-to-systems.md "mention")

[monitoring-and-alerting.md](../policies/monitoring-and-alerting.md "mention")

[authentication-access-and-accounts.md](../policies/authentication-access-and-accounts.md "mention")

## Process

There are 2 solutions for making a service accessible externally - a CF Tunnel or Port Forwarding.

## Cloudflare Tunnel

### Creating a 'public host'

1. Log into [Cloudflare's Zero Trust](https://one.dash.cloudflare.com/7d52087ea953fbe2fa5d873636173e63/home?tab=24h)
2. On the left, select Access > Tunnels
3. Select the relevant tunnel and click on 'Configure'
4. Click on the Public Hostname tab
5.  Click on 'Add Public Hostname' and input the relevant data, eg

    <figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption><p>cool.xfgn.dev will proxy to http://coolserver:123</p></figcaption></figure>
6. Click on Save hostname
7. Naigate to the url and confirm it is working

Note: If the internal service is on HTTPS you may need to disable TLS verify,

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

### Adding Authentication

Authentication is applied as an 'Application' and allows you to limit services to specific users, IP address, countries etc.

1. Log into [Cloudflare's Zero Trust](https://one.dash.cloudflare.com/7d52087ea953fbe2fa5d873636173e63/home?tab=24h)
2. On the left, select Access > Applications
3. Click on 'Add an application' and select Self Hosted
4. Configure the Application&#x20;
   *   Application Configuration block\
       Input the name and URLs you wish to configure\


       <figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption><p>This application will secure cool.xfgn.dev, cooltest.xfgn.dev and test.xfgn.dev/cool (but test.xfgn.dev will not be secured)</p></figcaption></figure>
   * Application Appearance block\
     Select custom logo and provide a URL to an image, such as the logo of the app
   * Tags\
     Apply any relevant tags, such as 'test', 'xfgn' etc
5. Click on OK / Save / Next
6. Create a policy using the information outlined in [#cloudflare-authentication](../policies/authentication-access-and-accounts.md#cloudflare-authentication "mention")and hit OK / Save / Next
7. Under the settings tab, tick 'Enable automatic cloudflared authentication'
8. Click on OK / Save / Next

## Port Forward

### Enable Firewall

As port forwarding opens the server to direct access via the internet, we require the firewall to be enabled.

#### **Ubuntu**

1.  SSH into server and input the below commands

    ```
    ufw allow ssh
    ufw enable
    ```
2.  Run the below command to get a list of active ports on the server and take note of anything that may need to be allowed through. Take note of anything with 'docker', as these will be containers running on the host (you can compare this data against Portainer)

    ```
    lsof -i -P -n | grep LISTEN
    ```
3.  Use the below command to allow ports through the firewall

    ```
    ufw allow PORT
    ```
4. Ensure that the [Crowdsec Firewall bouncer ](crowdsec-modules.md)is enabled and configured

Generic "allow list", applicable to all our servers

```
ufw allow 8080 #crowdsec
ufw allow ssh #allow SSH
```

### Port Forward in UniFi

1. Navigate to the [UniFi site manager ](https://unifi.ubnt.com/)and select Rigatoni
2. Click on the settings cog in the bottom left
3. Select Security > Port Forwarding
4. Click on Create Entry

Please ensure the port forward rule is named using the below scheme

<table><thead><tr><th width="152">Forwarding to</th><th width="383">Purpose</th><th>Firewall Rule Name</th></tr></thead><tbody><tr><td>Lungo</td><td>API to allow remote devices to connect to Wazuh</td><td><strong>Lungo - Wazuh API</strong></td></tr><tr><td>Latte</td><td>Ports to make Plex available externally</td><td><strong>Latte - Plex Ports</strong></td></tr><tr><td>Espresso</td><td>Portainer Edge Agent connection to Portainer main instance</td><td><strong>Espresso - Edge Agent</strong></td></tr></tbody></table>

Where possible, limit the 'From' IP to the relevant client (eg VPS), though this isn't possible for most use cases (eg Plex, Pterodactyl game ports)

