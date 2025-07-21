# External Access to Systems

Currently we are using a Cloudflare Tunnel to reverse proxy services to be available externally, either publicly or behind Cloudflare's authentication. Some services also require port forwarding

<table><thead><tr><th width="195">External type</th><th>Why?</th></tr></thead><tbody><tr><td>Cloudflare Tunnel</td><td><p>Standard web traffic and/or web based apps.</p><p></p><p>Secured behind Cloudflare's network.</p></td></tr><tr><td>Port Forward</td><td><p>High bandwidth traffic (file services), not HTTP/S traffic (eg game servers, video files), latency sensitive services (game servers). </p><p></p><p>Insecure and unsafe.</p></td></tr></tbody></table>

## Does my app need to be open to the public?

It depends on the use-case, and if you want to be! If you or someone else will need to access the service outside of the LAN, the app will need to be externally available.

* Is my app secure enough to be open to the public?
  * How is authentication handled?
  * How are updates handled?
* Does my app need to be open to the public?
  * Why would a random internet user access this app?
  * Would limiting this to a few users be a better solution?
  * What potential issues could arise? (eg file sharing service used to host malicious files)
* Is the app designed to be open to the public (eg Overseerr vs Proxmox)
* What is the potential risk if the app is breached?
  * What damage can be done? (eg deleting all VM's in Proxmox)
  * Can the service be used to jump to or access other services

_If the app needs to be externally available but has some risk associated with it, it could be made available with_ [_Cloudflare Authentication_](broken-reference) _in front of it. This also reduces the risk of DDOS attacks as the malicious actor will be attacking CF, not us._

