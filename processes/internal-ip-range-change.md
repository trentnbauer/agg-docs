# Internal IP Range Change

## IP Range Change

This process needs to be followed when our 'Home' subnet is changed. This ensures that everything is functional post change.

The majority of our services communicate via DNS, so there should be minimal outages from this.

## Process

* [ ] Log into [PVE](../service-overviews/infrastructure/proxmox-ve.md) and take note of each VM
* [ ] UniFi / Firewall changes
  * [ ] Update DHCP
    * network boot IP to [netbootxyz.md](../service-overviews/maintenance-and-monitoring/netbootxyz.md "mention") server
    * network boot image to `netboot.xyz.kpxe`
    * Set domain to `agg.local`
  * [ ] Reboot firewall to force DHCP update
  * [ ] Set DHCP reservations for each VM noted earlier
  * [ ] Update Firewall Rules to new IPs
* [ ] Macaroni may need its DNS manually updated in Datacenter > Macaroni > System > DNS&#x20;
* [ ] Reboot Fettuccine
* [ ] Reboot Latte
* [ ] Follow [#software-checklist](disaster-recovery.md#software-checklist "mention")
