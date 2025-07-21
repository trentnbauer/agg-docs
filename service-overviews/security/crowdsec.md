# CrowdSec

[Link to App](https://app.crowdsec.net/)

CrowdSec Security Engine, the open-source intrusion prevention system written in Go, protects against attacks on any server by parsing real-time service logs (servers, SSH, WordPress etc. logs) by detecting malicious behaviors.

All our servers are checked for SSH brute force, Log4j exploits and any CVE's that CS can detect. In addition to that, they're configured to monitor logs for the relevant apps on each server, such as attacks against Pterodactyl, Kasm and AdGuard (eg credential brute force).

This app is hosted externally, with a client installed on each VM. This is pushed out via [Ansible](../maintenance-and-monitoring/ansible.md)

<table><thead><tr><th width="223.33333333333331">Integration</th><th width="152">Host</th><th>Purpose</th></tr></thead><tbody><tr><td>NFTables</td><td>Any server with a port  forward</td><td>Add malicious IPs to firewall blocklists</td></tr><tr><td>SSH</td><td>All servers</td><td>Monitors for bruteforce login attempts</td></tr><tr><td>Cloudflare</td><td>Lungo, Cola, Mocha, Latte</td><td>Provide malicious IP's with Captcha requests before accessing agamersgrind.com, agamersgrind.dev, xfgn.dev and lattemedia.tv</td></tr><tr><td>UptimaKuma</td><td>Cola</td><td>Monitors for brute force login attempts</td></tr><tr><td>AdGuard</td><td>Americano, Espresso</td><td>Monitors for brute force login attempts</td></tr><tr><td>Wireguard</td><td>Cappuccino</td><td>Monitors for bruteforce login attempts</td></tr><tr><td>Pterodactyl Wings</td><td>Cocoa, Mocha</td><td>Monitors for bruteforce login attempts</td></tr><tr><td>Wordpress - AGG</td><td>Cocoa</td><td>Monitors for bruteforce login attempts</td></tr><tr><td>Kasm</td><td>Latte</td><td>Monitors for bruteforce login attempts</td></tr><tr><td>Proxmox</td><td>Macaroni</td><td>Monitors for bruteforce login attempts</td></tr><tr><td>DSM</td><td>Fettuccine</td><td>Monitors for bruteforce login attempts</td></tr></tbody></table>

\
