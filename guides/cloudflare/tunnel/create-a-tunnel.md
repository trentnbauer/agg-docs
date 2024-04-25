# Create a Tunnel

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Time Required</td><td>15 Minutes</td></tr><tr><td>Difficulty</td><td>Low</td></tr></tbody></table>

## Create your Tunnel

1. Log into Cloudflare
2. On the left, click on 'Zero Trust'
3. On the left, click on Access > Tunnels
4. Click on 'Create a tunnel'
5. Name the tunnel (eg "Home Network") and click on 'save tunnel'
6. Scroll down on the next page and locate the connector command,\
   ` cloudflared.exe service install`` `` `**`R4nd0mStr1ng0fCh4ract3rs`**
7. Take note of the unique key after 'install' (bolded above); save this in your password vault
8. Click on Next
9.  We're now forced to create a public hostname (reverse proxy). Per the scenario we will create a tunnel for Overseer;

    | Field     | Data               |
    | --------- | ------------------ |
    | subdomain | overseerr          |
    | domain    | yourdomain.com     |
    | path      |                    |
    | type      | HTTP               |
    | url       | ServerHostame:Port |
10. click on 'Additional application settings'
11. Click on 'Save tunnel'
12. You will be brought back to the Tunnels homepage, your tunnel will show as 'inactive'

## Deploy the Tunnel Container

1. Create a new compose file in your GitHub repo using the below compose template

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/cloudflared.yml" %}

2. Create a new GitOps stack using the tunnel compose file
3. Under Environmental variables
   1. add a variable "CLOUDFLARE\_UUID", using the key noted in step 6 above
4. Deploy your stack
5. Refresh the Cloudflare tunnel page, it will now state 'active'

Repeat steps 2-4 for each additional tunnel you wish to create (for load balancing and redundancy)

## Test the Tunnel

Browse to the public hostname we created earlier (step 9; subdomain + domain) and confirm that the Overseerr screen loads
