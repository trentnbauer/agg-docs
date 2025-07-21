# Tautulli

[Link to Access App](https://media.xfgn.dev/tautulli)

[Link to Download App](https://github.com/Tautulli/Tautulli)

A python based web application for monitoring, analytics and notifications for [Plex Media Server](https://plex.tv/).

This project is based on code from [Headphones](https://github.com/rembo10/headphones) and [PlexWatchWeb](https://github.com/ecleese/plexWatchWeb).

Tautulli runs on Cocoa as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/tautulli.yml" %}

| **Port** | **Purpose** |
| -------- | ----------- |
| 8181     | WebUI       |

| **Host Volume** | **Container Volume** | **Purpose**                |
| --------------- | -------------------- | -------------------------- |
| tautulli\_app   | /config              | configuration and database |

| **Integration** | **Purpose**                                    |
| --------------- | ---------------------------------------------- |
| Plex            | Syncs media and user data (eg user watch time) |

\
