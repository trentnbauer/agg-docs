---
coverY: 0
---

# Pterodactyl

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Time Required</td><td>1 Hour</td></tr><tr><td>Difficulty</td><td>Easy</td></tr><tr><td>Required Knowledge</td><td>Docker, Reverse Proxies</td></tr></tbody></table>

_Come across an issue with this documentation? You can make an edit request yourself, using the 'Submit Change' button on the left, or report it on our_ [_Discord_](https://discord.agamersgrind.com)

## The Scenario

Our goal is to create a new Pterodactyl Panel and Wings node for hosting game servers.

This documentation is NOT intended for a professional / reseller environment. Please do not follow this guide if you intend on selling or publicizing your server resources, as

* Proxy / Tunnelling wings and panel is NOT supported by Pterodactyl developers
* This guide is provided with best effort support

### Panel

The Pterodactyl Panel is the front end gui for managing your servers. The panel can be connected to multiple Wings nodes (or hosts), which this documentation is written for.

### Wings

Wings hosts the game server compute (CPU) and storage. As this machines job is to process data, a lot of high performing single thread cores are required as well as a lot of RAM.

### Flowchart

<figure><img src="https://4115153834-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F6s9LbmHPE41U6jxE7Mp6%2Fuploads%2FLIrMkgJVCxZY3X6E6Z20%2Ffile.excalidraw.svg?alt=media&#x26;token=492c8a46-ed18-4945-a4b2-b34ff40cbdf4" alt=""><figcaption></figcaption></figure>

## Prerequisites

* Panel machine
  * [Docker and compose installed](https://docs.docker.com/engine/install/ubuntu/)
  * Port 3306 to be available\
    _Further testing has confirmed the panel will ONLY talk to DB's on 3306_
* 1 machine to install the Wings node on (can be the same as the panel machine but not recommended)\
  _You can create multiple node machines_
  * [Docker and Compose installed](https://docs.docker.com/engine/install/ubuntu/)
  * A high performance, well spec'd machine;
    * Lots of RAM
    * High single thread passmark CPUs
    * SSD storage
* [A Domain that's managed by Cloudflare](../cloudflare/domains.md)
* A [Cloudflare Tunnel](../cloudflare/tunnel/)
* A [Cloudflare DDNS container with proxy turned off](../cloudflare/dynamic-dns.md) (this address will be your game server IP. Eg play.yourdomain.com)

### Recommended

* [Portainer & GitOps](../portainer-and-gitops/)
* A separate server for the Panel and each Wings node (if setting up more than 1)
