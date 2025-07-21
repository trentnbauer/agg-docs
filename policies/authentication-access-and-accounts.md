# Authentication, Access and Accounts

## Management of accounts

### Creating Accounts

* Usernames and passwords should be randomly generated
* Username must not be 'Administrator', 'root', 'Admin' etc unless the application forces it
* Where possible, OpenID should be [configured using the AGG / XFGN OAuth Client](../service-overviews/security/google-openid-auth.md)
  * Enable AutoLogon where possible
* For services behind CloudFlare authentication, local auth can be disabled
* Where possible, [use SSH keys](../processes/ssh-keys.md)
* If a server has public facing SSH (such as a VPS), use SSH keys and disable password sign in

### Storage of account details

* Usernames, passwords, TOPT and backup codes to be saved in our [Password Vault](../service-overviews/security/bitwarden.md)
* Internal services (eg docker containers) are to be saved in the 'Internal Services' folder, whilst external services (eg Cloudflare login, Namecheap login) are saved in the 'External Services' folder.

### Deletion of Accounts

* Credentials to be tested and confirmed working, then saved in Bitwarden before deletion

### Why?

This is to ensure that accounts are hard to breach and are backed up and stored appropriately. Bitwarden has a function to notify admins of any credential breaches.

***

## User Permissions

* Accounts required for integrations between systems (eg Home Assistant monitoring UniFi) must first be created as read-only
* Administrator access to be granted as last ditch
  * Do NOT create new accounts as administrators
  * Log in with new account and test before granting additional access
  * Research app online to figure out what access is required if more is required
  * Administrator access can be granted ONLY IF required

### Why?

This is to ensure that if accounts are breached, they can't do much damage

***

## Cloudflare Authentication

I have 4 primary authentication policies configured in Cloudflare. We mostly use the 'Allow' and 'Bypass' rule

<table data-full-width="true"><thead><tr><th width="163"></th><th>Allow</th><th>Allow with Reason</th><th>Allow with Approval</th><th>Bypass</th></tr></thead><tbody><tr><td>Explanation</td><td>User authentication. Allows access. Can be limited to country</td><td>User authentication. Allows access by requires a reason. Can be limited to country</td><td>User authentication. Allows access by requires approval from a second user. Can be limited to country</td><td>Bypasses authentication prompt. Must be applied to IP addresses, subnets or countries</td></tr><tr><td>Example</td><td>I need to send a WOL packet to a server</td><td>A server is off and I'm unable to send the WOL packet. This allows a second person to do that work though it is not normally within scope of their duties.</td><td>A server is off and I'm unable to send the WOL packet. This allows a second, non-technical person, to request access, be approved by myself or someone else and process this.</td><td>Allow everyone in Australia to have access to service A, but accessing outside of Australia follows one of the above rules instead</td></tr><tr><td>Documentation</td><td>None</td><td>Written for a technical person</td><td>Written for a non-technical person</td><td>None</td></tr></tbody></table>

### Authentication in front of Logon pages

If a public facing service has a login page that shouldn't be publicly accessible, you can put the authentication in front of the URL for the login page. Eg, myapp.mydomain.com/login&#x20;

### Why?

This enables a consistent approach and easy to understand workflow.
