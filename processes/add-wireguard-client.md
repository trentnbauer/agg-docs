# Add Wireguard Client

## Required Knowledge

[external-access-to-systems.md](../policies/external-access-to-systems.md "mention")

[Broken link](broken-reference "mention")

[unifi.md](../service-overviews/infrastructure/unifi.md "mention")

## Process

### Add client to WG server

1. Log into [UniFi admin portal](https://unifi.ui.com/)
2. Select Rigatoni
3. Select Settings > VPN
4. Select VPN Server and pick RigatoniWG
5. Click on Add Client
   1. Name the client (do not use spaces as this breaks UniFi WG)
   2. Click on Download to download the conf file
   3. Click on Add
6. Click on Save

### Add Config to Wireguard Client

1. [Download and install the appropriate client](https://www.wireguard.com/install/)
2. Open Wireguard and Import the conf file
3. Edit the conf file and replace '0.0.0.0/0' with the [Home IP range](../service-overviews/infrastructure/unifi.md#ip-ranges)
4. Save and connect to the tunnel

## Confirm tunnel is working

1. Browse to [google.com](https://google.com)
2. Browse to [setup.ui.com](https://setup.ui.com) (should load an SSL error)
