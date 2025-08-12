# ❔ Deploy new Container Stack

## Required Knowledge

* How to create Docker Compose files
* [authentication-access-and-accounts.md](../policies/authentication-access-and-accounts.md "mention")
* [creation-and-managment-of-servers-or-services.md](../policies/creation-and-managment-of-servers-or-services.md "mention")
* [external-access-to-systems.md](../policies/external-access-to-systems.md "mention")
* [monitoring-and-alerting.md](../policies/monitoring-and-alerting.md "mention")
* [management-of-documentation.md](../policies/management-of-documentation.md "mention")

## Create Compose file in Github

All compose files are stored in the `Docker-Compose` folder inside GitHub with format .yml

Refer to [#github-gitops](../service-overviews/portainer-and-gitops/#github-gitops "mention")

### Handling Variables

When variables are used, such as variables for Ports, please use the `${VARIABLENAME:-DefaultValue}` structure. This ensures that if the variable is not set, it will be set to the default rather than null. Some containers will not start with null variables. Some example use cases;

{% code overflow="wrap" %}
```yaml
ports:
  - ${WEBPORT:-8200}:8200  #If a $PORT variable is not provided, it will default to 8200
environment:
  - CONFIGFILE=${CONFIGFILE:-/path/to/config.yml} #if the $CONFIGFILE variable is not provided, it will default to /path/to/config.yml
```
{% endcode %}

### Logging

Each container should have the below to ensure that logging is reduced. The settings can be tweaked where required.

{% code overflow="wrap" %}
```yaml
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3" 
```
{% endcode %}

## DockFlare

DockFlare is a container that automates creation and removal of Cloudflare Zero Trust Tunnels using labels, refer to [dockflare-cf-zero-trust.md](../service-overviews/remote-access/dockflare-cf-zero-trust.md "mention")

In the below example, we'll configure this for the "overseerr" container. Refer to [overseerr.md](../service-overviews/plex-suite/overseerr.md "mention") to see a complete compose file

### HTTP

<pre class="language-yaml" data-title="Labels for the container"><code class="lang-yaml">      - dockflare.enable=${CFTUNNEL:-true}
      - dockflare.0.hostname=${CFSUBDOMAIN}${CFDOMAIN}
<strong>      - dockflare.0.service=http://${HOSTNAME:-localhost}:${WEBPORT:-5055}
</strong>      - dockflare.0.access.policy=${CFPOLICY:-default_tld} #default_tld, authenticate, bypass
      - dockflare.0.zonename=${CFDOMAIN}
      - dockflare.0.path=${CFURLPATH:-}
</code></pre>

### HTTPS

{% code title="Labels for the container" %}
```yaml
      - dockflare.0.hostname=${CFSUBDOMAIN}${CFDOMAIN}
      - dockflare.0.service=http://${HOSTNAME:-localhost}:${WEBPORT:-5055}
      - dockflare.0.access.policy=${CFPOLICY:-default_tld} #default_tld, authenticate, bypa
      - dockflare.0.zonename=${CFDOMAIN}
      - dockflare.0.path=${CFURLPATH:-}
      - dockflare.0.no_tls_verify=true
```
{% endcode %}

_Don't forget to ammend the default value for the port variable_

As you may see, you can have multiple tunnels assigned to 1 container using the numeric value, eg `dockflare.0.x`, `dockflare.1.x` etc

And the variables (or .env file) to make DockFlare automate the creation of the tunnel,

#### Subdomain with URL path

{% code title=".env" %}
```
CFSUBDOMAIN= #Include a . at the end - MANDATORY
CFDOMAIN=
CFURLPATH=/
HOSTNAME=
```
{% endcode %}

#### Subdomain

{% code title=".env" %}
```
CFSUBDOMAIN= #Include a . at the end - MANDATORY
CFDOMAIN=
HOSTNAME=
```
{% endcode %}

#### Root domain

{% code title=".env" %}
```
CFDOMAIN=
HOSTNAME=
```
{% endcode %}

#### Root domain with URL path

{% code title=".env" %}
```
CFDOMAIN=
CFURLPATH=/
HOSTNAME=
```
{% endcode %}

The HOSTNAME variable is the IP or local DNS address for the host, eg myserver.local or 192.168.1.10

### Health Checks

Where possible, all containers should have health checks. We utilize the [AutoHeal ](../service-overviews/maintenance-and-monitoring/autoheal.md)container which will restart unhealthy containers. The intention of this is to automate DR.

Here are some examples of health checks;

#### Web UI

Port (80 below) needs to be set as the containers port (right hand side of the port mapping)

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml">        healthcheck:
<strong>      test: curl --connect-timeout 15 --silent --show-error --fail -k http://LOCALHOST:80
</strong>      interval: 30s
      retries: 3
      start_period: 30s
      timeout: 20s
    labels:
      - autoheal=true
</code></pre>

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml">        healthcheck:
<strong>      test: wget --no-verbose --tries=1 --spider http://LOCALHOST:80 -O /dev/null || exit 1
</strong>      interval: 30s
      retries: 3
      start_period: 30s
      timeout: 20s
    labels:
      - autoheal=true
</code></pre>

#### MongoDB

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml"><strong>        healthcheck:
</strong>      test: ["CMD", "mongo", "--eval", "db.adminCommand('ping')"]
      interval: 30s
      timeout: 10s
      retries: 5
    labels:
      - autoheal=true
</code></pre>

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml"><strong>        healthcheck:
</strong>      test: ["CMD-SHELL", "pidof mongod || exit 1"]
      interval: 30s
      timeout: 10s
      retries: 5
    labels:
      - autoheal=true
</code></pre>

#### MariaDB

{% code overflow="wrap" %}
```yaml
    healthcheck:
      test: ["CMD", "mariadb-admin", "ping", "-proot", "--password=$MYSQL_PASS_ROOT"]
      interval: 30s
      timeout: 10s
      retries: 5
    labels:
      - autoheal=true
```
{% endcode %}

## Deploy Stack

### What server?

Pick a server that is relevant to the use-case.&#x20;

* If the app relates to Plex, the container should be installed on the same host as the Plex server
* If the app requires a GPU, the container should be on a server with a GPU
* If the app relates to Pterodactyl, it should be installed on the same server as either the panel or wings.
* Etc

### Deploy Stack



## ENV file required?

If an ENV file is required,

1. SSH into [Portainer host](../service-overviews/portainer-and-gitops/#portainer-1)
2.  Run the below command to CD into the Portainer files

    ```bash
    cd /var/snap/docker/common/var-lib-docker/volumes/portainer/_data/env
    ```
3.  Run the below command (correct the file name) to create a new ENV file,

    ```bash
    nano myapp.env
    ```
4. Paste the contents of the ENV file and save it
5.  Update the Docker Compose file to reference the env file per below

    ```yaml
        env_file:
          - $ENV
    ```
6.  Update the stack and set the ENV variable as below (correct the file name)

    <pre><code><strong>/data/env/myapp.env
    </strong></code></pre>
7. Save and stop the stack
8. Delete and related docker volumes
9. Pull and deploy the stack
