# AutoHeal

[Link to GitHub or Website](https://github.com/willfarrell/docker-autoheal)

Monitor and restart unhealthy docker containers. This functionality was proposed to be included with the addition of `HEALTHCHECK`, however didn't make the cut. This container is a stand-in till there is native support for `--exit-on-unhealthy`

This app is hosted on each server, using the [All compose stack](../portainer-and-gitops/all-compose-stacks.md)

The container will monitor and restart any containers with the `autoheal`=`true` label
