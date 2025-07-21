# Overseerr

[Link to Access App](https://request.xfgn.dev)

[Link to Download App](https://github.com/sct/overseerr)

Overseerr is a free and open source software application for managing requests for your media library. It integrates with your existing services, such as Sonarr, Radarr, and Plex!

Overseerr is hosted on Cocoa, as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/205cfc374516886a137f2f0b66dca9c87fa0f740/docker-compose/overseerr.yml" %}

| **Port** | **Purpose** |
| -------- | ----------- |
| 5055     | WebUI       |

| **Host Volume** | **Container Volume** | **Purpose**         |
| --------------- | -------------------- | ------------------- |
| overseerr\_app  | /config              | Config and datavase |

| **Integration** | **Purpose**                                                               |
| --------------- | ------------------------------------------------------------------------- |
| Plex            | Syncs media content and users from Plex                                   |
| Radarr & Sonarr | Syncs and adds content to the 1080p and 4k instances of Radarr and Sonarr |
| Tautulli        | Pulls watch history from Tautulli                                         |

{% embed url="https://raw.githubusercontent.com/trentnbauer/agg.local/main/docker-compose/overseerr.yml?token=GHSAT0AAAAAACCCAC7PUTZXI3HJEGGGBV7UZEBDDUA" %}

\
