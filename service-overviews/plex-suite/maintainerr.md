# Maintainerr

[Link to App](http://maintainerr.lattemedia.tv/)

[Link to GitHub or Website](https://github.com/jorenn92/Maintainerr)

Automates deletion of Plex media based on filters

This app is hosted on Latte as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/e161ff0fac40df82f2b10aed3e2b7ff6e0d2333b/docker-compose/maintainerr.yml" %}

| Port | Purpose |
| ---- | ------- |
| 6246 | WebUI   |

| Host Volume                                                                          | Container Volume | Purpose          |
| ------------------------------------------------------------------------------------ | ---------------- | ---------------- |
| [maintainerr\_data](https://portainer.xfgn.dev/#!/8/docker/volumes/maintainerr_data) | /opt/data        | Application Data |

| Integration | Purpose                                               |
| ----------- | ----------------------------------------------------- |
| Plex        | Pull data from plex, eg watch history                 |
| Sonarr      | Pull data from Sonarr, eg if returning season         |
| Radarr      | Pull data from Radarr, eg date requested              |
| Overseerr   | Pull data from Overseerr, eg how many times requested |
