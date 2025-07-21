---
coverY: 0
---

# Portainer and GitOps

## Portainer

[Link to App](https://portainer.xfgn.dev)

[Link to GitHub or Website](https://www.portainer.io/)

Portainer's _hybrid & multi-cloud container management software_ supports Kubernetes, Docker, Swarm in any Data Center, Cloud, Network Edge or IIoT Device.

The main instance of Portainer is hosted on Espresso but each other Docker host also has the Portainer Edge Agent installed, which enable central management.

### Flowchart

<img src="../../.gitbook/assets/file.excalidraw (7).svg" alt="" class="gitbook-drawing">

As Portainer needs to be installed BEFORE we can use GitOps compose files, we do not use have a Compose file for it.

```bash
docker run -d \
  -p 8000:8000 \
  -p 9443:9443 \
  --name portainer \
  --restart=always \
  --label dockflare.enable=true \
  --label dockflare.hostname=### \
  --label dockflare.service=https://###:9443 \
  --label dockflare.access.policy=default_tld \
  --label dockflare.zonename=### \
  --label dockflare.no_tls_verify=true \
  --label com.centurylinklabs.watchtower.enable=true \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer:/data \
  portainer/portainer-ce:lts

```

_The above run command also enables the Watchtower to update Portainer. Watchtower (only enabled for containers with the watchtower enabled label) is deployed to all hosts as part of the 'all' edge stack. This ensures that Portainer is always up to date, as Portainer cannot update or manage itself._

### Instances

#### Portainer

| Port | Purpose   |
| ---- | --------- |
| 9443 | SSL WebUI |
| 8000 | API Port  |

| Host Volume          | Container Volume     | Purpose                         |
| -------------------- | -------------------- | ------------------------------- |
| /var/run/docker.sock | /var/run/docker.sock | Management of docker containers |
| portainer            | /data                | configuration                   |

| Integration  | Purpose               |
| ------------ | --------------------- |
| Google OAuth | Enable authentication |

#### Edge Agent

| Port | Purpose  |
| ---- | -------- |
| 8000 | API Port |

| Host Volume          | Container Volume     | Purpose                         |
| -------------------- | -------------------- | ------------------------------- |
| /var/run/docker.sock | /var/run/docker.sock | Management of docker containers |

| Integration | Purpose            |
| ----------- | ------------------ |
| Portainer   | Central management |

### Managing Portainer

#### Tags and Groups

Applying a tag to a Portainer instance allows us to organize instances into groups which makes identifying each individual servers function easier as well as some automation.

Currently, we have 4 tags;

* Production
* Production Bare Metal
* Production Synology
* Test

Assigning one or any of these tags to a Portainer instance will add it to the group by the same name

#### Stacks

Stacks are Portainers take on Docker Compose. The Compose file can be managed directly in Portainer or via a third party service, such as GitHub. Refer to the [GitOps documentation](broken-reference) for more information

#### Edge Stacks

Edge Stacks are stacks that are assigned to groups, which are then pushed to any Portainer instance in that group.

Unfortunately, Edge Stacks cannot be managed centrally via GitHub but instead centrally managed in Portainer.

## GitHub / GitOps

<table data-header-hidden><thead><tr><th></th><th></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="https://github.com/trentnbauer/agg.local">Private GitHub Repo</a></td><td><a href="https://github.com/trentnbauer/agg">Public GitHub Repo</a></td><td></td></tr></tbody></table>

GitOps gives you tools and a framework to take DevOps practices, like collaboration, CI/CD, and version control, and apply them to infrastructure automation and application deployment. Developers can work in the code repositories they already know, while operations can put the other necessary pieces into place.

This app is hosted externally.

Specific files are sync'd from the private repo to public repo for documentation reference. **Any files with secrets or identifiable information should not be sync'd across.**

<table><thead><tr><th width="232">Integration</th><th width="134">Repo</th><th>Purpose</th></tr></thead><tbody><tr><td>Portainer</td><td>N/A</td><td>Portainer reads data in GitHub, pulling compose files and containers</td></tr><tr><td>Renovate Bot</td><td>Private</td><td>A bot that watches for container updates in the compose files and creates a merge request to update them</td></tr><tr><td><a href="https://mergify.com/">Mergify bot</a></td><td>Public</td><td>Merges pull requests in the 'approved' state</td></tr><tr><td>Auto Approve action</td><td>Public</td><td>Auto approves pull requests created by me</td></tr><tr><td>Sync Files action</td><td>Private</td><td>Sync's files from the private repo to the public repo</td></tr></tbody></table>

\
