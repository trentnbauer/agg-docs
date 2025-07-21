# Limit Bandwidth to Container

Some containers need their bandwidth limited to reduce the risk of them flooding our limit upload speed. Examples of this are

* File storage / sharing
* Websites
* File conversion / editing software

## Network Adaptor

Firstly, you will need to get primary network adaptors name, which (if different from mine - ens18) will need to be set as a variable.

1. SSH into your server
2. Run a command that lists network interfaces, such as `ip link show`
3. Review the output and locate your primary adaptor. You may have a stack of adaptors for your docker containers.

If your network adaptor is named differently than mine, you have 2 options

1. Set `NETADAPT` variable to the network interface name
2. Update `ens18` in the section below to your network interface name

## Compose File

To limit an application's bandwidth you will need to add the Traffic Control container and a network to your compose file. This container manages anything going through the docker network and applies the label limit

```yaml
....

  traffic-control:
    image: lukaszlach/docker-tc:stable
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    networks:
      - network
    restart: on-failure
    cap_add:
      - NET_ADMIN
    command: [--interface, ${NETADAPT:-ens18}]
    
networks:
  network:

....
```

## Applying label to application

In addition to the above, you will need to set the application to use the newly created network and add labels for its configuration,

```yaml
....

services:
  app:
    image: my image
    networks:
      - network
    labels:
      com.docker-tc.enabled: "1"     # Enables Traffic Control mangement
      com.docker-tc.limit: "15mbps"  # Setting the bandwidth limit to 25mbit
      
....
```

