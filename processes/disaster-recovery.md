---
description: This page is designed to be printed
---

# Disaster Recovery

As much as we don't want it to happen, somethings things die. Sometimes power runs out.

### What is a 'Disaster'

This documentation can be followed for the below scenarios

* Power outage
* Server hardware failure

## Procedure

### Physical Hardware Checklist

* [ ] Press the display button on the [UPS](../service-overviews/infrastructure/cyberpower-powerpanel-and-ups.md) and confirm
  * [ ] It is powered on
  * [ ] It has power from mains
*   [ ] Check all infrastructure is powered on (look for power lights)

    _Refer to Physical Hardware section on the left_
* [ ] Remove faceplate from NTD and confirm powered on
* [ ] Confirm [networking equipment](../physical-hardware/unifi.md) is powered on

### Software Checklist

* [ ] Network Test
  * [ ] Ping 8.8.8.8 to confirm internet is working
  * [ ] Ping google.com to confirm external DNS is working
  * [ ] Ping setup.ui.com to confirm internal DNS is working
* [ ] Confirm[ Proxmox VE](../service-overviews/infrastructure/proxmox-ve.md) is accessible
  * [ ] Internal link loads login page (use Linux credentials)
  * [ ] All storage pools are online
  * [ ] VM's show and are booting (there is a delay between boots so some may be on, others off)
* [ ] Confirm [Proxmox Backup Server](../service-overviews/maintenance-and-monitoring/proxmox-backup-server.md) is accessible
  * [ ] Internal link loads login page (use Linux credentials)
  * [ ] All storage pools are online
* [ ] Confirm the [NAS ](https://nas.xfgn.dev)is accessible (creds in vault)
  * [ ] Open Storage Manager and confirm 'system is healthy'
* [ ] Log into [UptimeKuma](../service-overviews/maintenance-and-monitoring/uptimekuma.md) and confirm that all services are green. It may take 15 minutes for them all to report as online
* [ ] Confirm servers are reporting data back to [NetData](../service-overviews/maintenance-and-monitoring/beszel.md) and check for any alerts\
  &#xNAN;_&#x41;lerts related to disk backlog, IO delay or disk usage can be ignored for now. Backlog and IO delay can be caused by multiple VM's starting up ay once_

_An excessive, but very thorough way, to check all services are online is to go through each page in this doco and trying to access any "link to app" links_

### Services failing to start

Unfortunately I'm unable to write specific doco here as there is to much to capture. Please refer to the troubleshooting section on the left panel and/or the hints below

* Compare the down services against the Cloudflare tunnels - are they all on the 1 server?
