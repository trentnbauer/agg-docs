# ❔ New Domain

## Required Knowledge

[authentication-access-and-accounts.md](../policies/authentication-access-and-accounts.md "mention")

[cloudflare.md](../service-overviews/infrastructure/cloudflare.md "mention")

[dns-management.md](dns-management.md "mention")

[creation-and-managment-of-servers-or-services.md](../policies/creation-and-managment-of-servers-or-services.md "mention")

[monitoring-and-alerting.md](../policies/monitoring-and-alerting.md "mention")

[external-access-to-systems.md](../policies/external-access-to-systems.md "mention")

[bitwarden.md](../service-overviews/security/bitwarden.md "mention")

## Purchase Domain

Our preference is to [purchase domains via Cloudflare](https://dash.cloudflare.com/7d52087ea953fbe2fa5d873636173e63/domains/register) though they do not have all TLDs. If the domain cannot be registered via Cloudflare you will need to purchase it via another provider, such as Namecheap.

If you purchase a domain through a different provider you will need to [set up the site in Cloudflare follow that providers steps for changing your Nameservers to Cloudflare.](https://developers.cloudflare.com/dns/zone-setups/full-setup/setup/) I would recommend looking at the registrars documentation for changing the Nameservers to Cloudflare, as Cloudflare's documentation may be outdated.

## Configure Domain

### Configuring an Email address



### SPF & DMARC

{% embed url="https://gist.github.com/irazasyed/a5ca450f1b1b8a01e092b74866e9b2f1#step-5-setup-spf-records--dmarc-policy-in-cloudflare-dns" %}

## Cloudflare WAF

### Crowdsec Bouncer

Refer to [#cloudflare-bouncer](crowdsec-modules.md#cloudflare-bouncer "mention")

### WAF Rules



## Configure Gmail SMTP

This guide will set you through configured a generic noreply@ email

### Create Cloudflare Route



### Configure Gmail

1. Log into Gmail with the Gmail SMTP account
2. Click on the settings cog > all settings
3. Click on Accounts and Import
4. Locate the 'Send mail as' section and click on 'add another email address'
   1.  Fill out the first form and hit next\


       <table><thead><tr><th width="127">Field</th><th>Data</th></tr></thead><tbody><tr><td>Name</td><td>Name of the Email account</td></tr><tr><td>Email</td><td>Email address</td></tr></tbody></table>
   2.  Fill out the second form and hit next\


       <table><thead><tr><th width="153">Field</th><th>Data</th></tr></thead><tbody><tr><td>SMTP Server</td><td>smtp.gmail.com</td></tr><tr><td>Port</td><td>587</td></tr><tr><td>Username</td><td>Gmail SMTP account email address</td></tr><tr><td>Password</td><td>Gmail SMTP account SMTP app password</td></tr><tr><td>TLS</td><td>Tick secure connection using TLS</td></tr></tbody></table>
5.



## Add domain to Google Search Console

The [Google Search Console](https://search.google.com/search-console) provides some analytics on clicks

1. &#x20;???

