# DNS Management

## Required knowledge

[cloudflare.md](../service-overviews/infrastructure/cloudflare.md "mention")

[external-access-to-systems.md](../policies/external-access-to-systems.md "mention")

## Redirect a web page or subdomain

1. Log into Cloudflare
2. Select the domain you wish to manage
3. on the left, select DNS
4.  Click on Add Record and fill out the record per below and click Save

    <figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption><p>This will redirect discord.agamersgrind.com<br>The IPv4 address doesn't matter, so we just fill Googles DNS</p></figcaption></figure>
5. On the left, click on the arrow next to Rules > Redirect rules
6.  Create a new redirect rule per below and hit Deploy\


    <figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption><p>this will redirect 'discord.agamersgrind.com' (in the IF block) to the discord.gg/invite url (in the THEN block)</p></figcaption></figure>
