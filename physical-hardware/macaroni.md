# Macaroni

| Tool           | Tunnel Address                               | Internal Address                               |
| -------------- | -------------------------------------------- | ---------------------------------------------- |
| Proxmox VE     | [https://pve.xfgn.dev](https://pve.xfgn.dev) | [https://10.0.0.2:8006](https://10.0.0.2:8006) |
| Proxmox Backup | [https://pbs.xfgn.dev](https://pbs.xfgn.dev) | [https://10.0.0.2:8007](https://10.0.0.2:8007) |

## Specifications

<table><thead><tr><th width="234">Component</th><th>Model</th></tr></thead><tbody><tr><td>Case</td><td>Silverstone Alta G1M White (Planned PowerMac G4 swap)</td></tr><tr><td>Motherboard</td><td>MSI B660M Pro</td></tr><tr><td>CPU</td><td>i5 13500</td></tr><tr><td>CPU Cooler</td><td>Noctua NH-U9</td></tr><tr><td>RAM</td><td>4x32GB Vengeance LP, 3200mhz</td></tr><tr><td>GPU</td><td>Quadro P4000</td></tr><tr><td>Power Supply</td><td>Corsair 600w SFX</td></tr><tr><td>Storage</td><td><p>2x NVME 2TB SDD (T-Create Classic) - Server Storage</p><p>2x SATA 4TB HDD (WD Green) - Backup Storage</p><p>1x SATA 500GB SSD (Crucial MX500) - Boot Drive<br>1x SATA 240GB SSD (Crucial BX500) - Cache Drive</p></td></tr><tr><td>Other</td><td>HomeAssistant SkyConnect dongle<br>ZWave Dongle</td></tr></tbody></table>

## ZFS Storage Pools

<table><thead><tr><th width="155">Name</th><th width="155">Type</th><th>Drives</th><th>Purpose</th></tr></thead><tbody><tr><td>SSDRAID</td><td>ZFS, MIRROR</td><td>2x 2TB NVME</td><td>VM Disk storage</td></tr><tr><td>HDD-MIRROR</td><td>ZFS, MIRROR</td><td>2x 4TB HDD</td><td>Backup storage</td></tr></tbody></table>

## Images

Images of the server below. Please note: These pictures will span multiple iterations so they hardware may look different between images

Early 2023

![](<../.gitbook/assets/image (26).png>)<img src="../.gitbook/assets/image (41).png" alt="" data-size="original">

Late 2023

![](<../.gitbook/assets/image (8).png>)![](<../.gitbook/assets/image (12).png>)
