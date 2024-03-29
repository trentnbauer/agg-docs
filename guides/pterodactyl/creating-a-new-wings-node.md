# Creating a new Wings node

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Time Required</td><td>30 Minutes</td></tr><tr><td>Difficulty</td><td>Moderate</td></tr></tbody></table>

_I am installing Wings on my test VM, 'Basil', for writing this documentation. Any references to Basil will need to be changed to your server. Once this documentation has been finalized, Wings will be deleted from Basil._

## Installing Wings and set up Reverse Proxy

### Configure the 'Pterodactyl Wings' Portainer stack

Refer to the [Portainer](broken-reference/) and [GitOps](broken-reference/) documentation for configuring a new Portainer stack using the AGG Pterodactyl Wings Docker Compose file

* Name the stack something simple, like 'wings'
* Ensure you fill all the variables from the ENV file

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/pterodactyl-wings.yml" %}

{% code title=".ENV file" %}
```editorconfig
PORT_SFTP=2022    #unfortunately SFTP doesn't seem to work with CF tunnels
TZ=
SQL_PASS=
SQL_PASS_ROOT=
PORT_DB=3306
PORT=             #This is the port Cloudflare will talk too, do not use 443
```
{% endcode %}

### Allow Ports through the Firewall

1. SSH into your server
2.  Allow SSH and enable the firewall with the below commands

    ```
    ufw allow ssh
    ufw enable
    ```

    \
    _This is to increase security on this hardware as a port forward is required_
3.  Run the command `ufw allow PORT`, replacing PORT with what you set for PORT and PORT\_SFTP above, eg;

    <pre class="language-sh"><code class="lang-sh"><strong>ufw allow 2022
    </strong></code></pre>

### Confirm the Container is working

1. Start the Wings container if it not running
2.  Check your docker logs, you should see something similar to below

    <figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>
3.  Open your internet browser and navigate to hostname:port, you should see the below error;

    <pre><code><strong>{"error":"The required authorization heads were not present in the request."}
    </strong></code></pre>

### Configure the Reverse Proxy

Refer to the [Cloudflare Proxy](../cloudflare/tunnel/create-a-proxy-public-hostname.md) and [Authentication ](broken-reference/)guides

* Your subdomain and domain needs to match the PTERO\_PANEL\_URL variable set above
* Type is HTTP, pointing at yourserver:port

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

## Configure Panel & Wings

### Set up a Node on the Panel

1. Log into Pterodactyl with an administrator account
2. Click on the Settings cog in the top right
3. Click on Nodes
4. Click on Create New in the top right and
   * Name your Node (I normally give them the same name as the server)
   * Provide the FQDN of your Node (this is the externally available reverse proxy address configured here [#configure-the-reverse-proxy](creating-a-new-wings-node.md#configure-the-reverse-proxy "mention"))
   * Tick 'Use SSL Connection'
   * Tick 'Behind Proxy'
   * Provide RAM & over allocation of the machine or VM
   * Provide the disk space & over allocation of the machine or VM
   * Set your Daemon port to 443 (As Cloudflare uses 443 for its proxy)
   *   Click on 'Create Node'

       <figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

### Upload Configuration file to Wings

1. In Pterodactyl, click on 'Nodes' on the left
2.  You should see your new Node, with a red heart\\

    <figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
3.  Click on your new node, then the Configuration tab and confirm that the highlighted lines are the same as mine\\

    <figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption><p><em>I would also recommend changing the upload limit to 1024</em></p></figcaption></figure>
4. Copy the contents of the file and save it as 'config.yml'
5. Log into Portainer and click on the Wings host
6. Click on 'Stacks' and select the 'wings' stack
7. Click on 'Stop stack'
8. Click on 'Volumes'
9. Locate the Wings 'config' volume - it will be named after your stack (eg wings\_config) and click on Browse
10. Click on the Upload button, then select your config.yml file
11. Click on Stacks and open your Wings stack
12. Restart the stack and wait 30 seconds
13. Refresh the Pterodactyl Nodes page and it should now be connected\\

    <figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

### Assigning Ports to the Node

1. Click on your new node and click the 'Allocations' tab
2. On the right hand panel, input
   1. IP address: 0.0.0.0
   2. IP Alias: Your domain or subdomain that points to your servers public IP
   3.  Ports: The port range you will forward to this VM (I've chosen ports 500-600)\\

       <figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
   4. Run the `ufw allow` command to allow these ports through the firewall. You can use a : to allow a range, such as 500:600

### Port Forward

You will now need to port forward the chosen ports to your server.

Firstly, have a look at your modem / router. You will need to take note of

* Brand
* Model number or part number

Port forwarding is particularly tricky for beginners, mostly because every device is slightly different.

You'll need to do some Googling and / or Youtube'ing on how to port forward with your model router / modem.

## Why do I do it this way?

My assumption here is that the Pterodactyl dev's want us to set up and use SSL certs on the Wings host and make it publicly available without a proxy. I can't be bothered generating certs and managing their expirations in my Homelab. My configuration offloads the certificate management to Cloudflare (or any other reverse proxy - I used to use NGINX Proxy Manager for this) which means that I don't need to worry about cycling certificates.

Offloading this task to the Cloudflare tunnel does create a couple of potential issues,

* If the tunnel is down / crashes, the Panel can't talk Wings
* If your hosting the Panel and Wings in your \_home\_lab, the connection is reliant on the internet being up
* Cloudflare outages may break the Panel / Wings communication
* Pterodactyl Discord does not provide support for proxied panel/wings connections

Please note that I don't have SFTP working with this set up, though I imagine changing the SFTP port and forwarding that port to the host would function fine.
