# DockFlare (CF Zero Trust)

Refer to the following documentation for creation and management of Cloudflare services

* [.](./ "mention")
* [external-access-to-systems.md](../../policies/external-access-to-systems.md "mention")
* [authentication-access-and-accounts.md](../../policies/authentication-access-and-accounts.md "mention")

## Zero Trust / Tunnels

[Link to App](https://www.cloudflare.com/en-au/products/tunnel/)

The Cloudflare tunnel is a port-forwarding-less reverse proxy. The traffic is tunneled through Cloudflare servers reducing the risk of DDOS  and other malicious attacks. Another advantage is that Cloudflare handles authentication, so its harder to brute force one of our internal services.



### Flowchart <a href="#bkmrk-flowchart" id="bkmrk-flowchart"></a>

<img src="../../.gitbook/assets/file.excalidraw (8).svg" alt="" class="gitbook-drawing">

## DockFlare

_Tunnels are slowly being migrated to DockFlare_

[Link to GitHub or Website](https://github.com/ChrispyBacon-dev/DockFlare)

DockFlare simplifies Cloudflare Tunnel and Zero Trust Access policy management by using Docker labels for automated configuration, while also providing a powerful web UI for manual service definitions and policy overrides. It enables secure, hassle-free public access to both Dockerized and non-Dockerized applications with minimal direct interaction with Cloudflare. Acting as a dynamic, self-hosted ingress controller, DockFlare offers persistent, UI-driven control over access policies centralizing and streamlining your access management.

This app is part of the [all-compose-stacks.md](../portainer-and-gitops/all-compose-stacks.md "mention") and is hosted on each machine / VM.

Each docker container can be accessed via the tunnel by following [#dockflare](../../processes/deploy-new-container-stack.md#dockflare "mention")

The DockFlare UI can be accessed at the relevant host, eg [https://espresso-tunnel.xfgn.dev](https://espresso-tunnel.xfgn.dev/) and [https://cocoa-tunnel.xfgn.dev](https://cocoa-tunnel.xfgn.dev/)

