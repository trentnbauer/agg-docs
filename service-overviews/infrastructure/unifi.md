# UniFi

| Internal Address                     | Tunnel Address                                   | UniFi Portal                                   |
| ------------------------------------ | ------------------------------------------------ | ---------------------------------------------- |
| [https://10.0.0.1](https://10.0.0.1) | [https://unifi.xfgn.dev](https://unifi.xfgn.dev) | [https://unifi.ui.com/](https://unifi.ui.com/) |

#### Part of this doco is stored here [unifi.md](../../physical-hardware/unifi.md "mention")

UniFi is a line of wireless access points, switches, routers, controller devices, VoIP phones, and access control products, cameras and EV chargers created by Ubiquiti. It can be used for the corporate network and also for the home network. An Unifi network controller manages all the equipment in the UNIFI network.

UniFi devices are managed by the UniFi software, which runs on a Cloudkey device or UniFi OS

The IP address for our Firewall is 10.0.0.1&#x20;

## IP Ranges

<table><thead><tr><th width="225">Range</th><th>Use Caes</th></tr></thead><tbody><tr><td>10.0.0.1/8</td><td>Home, server and management network</td></tr><tr><td>182.168.0.1/24</td><td>IoT Network</td></tr><tr><td>172.16.0.1/24</td><td>Wireguard VPN</td></tr></tbody></table>

## Modifications

[The NextDNS agent has been installed on Rigatoni](https://github.com/nextdns/nextdns/wiki/UnifiOS)
