# ❔ Create new Virtual Machine

## Required Knowledge

* [creation-and-managment-of-servers-or-services.md](../policies/creation-and-managment-of-servers-or-services.md "mention")
* [authentication-access-and-accounts.md](../policies/authentication-access-and-accounts.md "mention")

## Process

### Create a new VM in Proxmox

1. &#x20;???

### Install SSH Keys

Refer to [ssh-keys.md](ssh-keys.md "mention")

### Create a new environment in Portainer

#### OnPrem

1. Log into Portainer
2. On the left, select Environments
3. On the right, click on 'add'
4. Select Docker Standalone, then hit Start
5. Select Edge Agent
   * Provide the name of the VM
   * For the API server, provide "https://espresso.agg.local:9443"

#### Externally hosted

Follow the above doco, but the API server is https://play.agamersgrind.com:9443

Refer to [#port-forward-in-unifi](port-forwarding-or-tunneling-a-service.md#port-forward-in-unifi "mention") and add the devices public IP to the source of the "Espresso - Edge Agent Connection" FW rule

### Deploy basic stacks

Refer to the[ 'all' compose files](https://github.com/trentnbauer/agg.local/tree/6179c492144ddd0c65ade24f1d0b9d2adeca8416/docker-compose/all) and run the stacks applicable to this server

### Push base config via [Ansible](https://ansible.xfgn.dev/project/1/inventory)

1. Edit all relevant groups and add the machine as root@hostname\
   ![](<../.gitbook/assets/image (20).png>)

***

## Setup Complete

Now that the VM is configured it is ready to have applications and services installed.

Please read these guides and policies before configuring any further

* [monitoring-and-alerting.md](../policies/monitoring-and-alerting.md "mention")
* [external-access-to-systems.md](../policies/external-access-to-systems.md "mention")
* [management-of-documentation.md](../policies/management-of-documentation.md "mention")
