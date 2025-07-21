# Wizarr

[Link to Access App](https://invite.xfgn.dev/)

[Link to Download App](https://github.com/Wizarrrr/wizarr)

Wizarr is a automatic user invitation system for Plex, Jellyfin and Emby. Create a unique link and share it to a user and they will automatically be invited to your Media Server! They will even be guided to download the clients and instructions on how to use your requests software!

Wizarr is hosted on Cocoa, as a docker container

{% @github-files/github-code-block %}

| **Port** | **Purpose** |
| -------- | ----------- |
| 5690     | WebUI       |

| **Host Volume** | **Container Volume** | **Purpose**          |
| --------------- | -------------------- | -------------------- |
| wizarr\_app     | /data/database       | Application database |

| **Integration** | **Purpose**                             |
| --------------- | --------------------------------------- |
| Plex            | Grants Plex users access to Plex server |

\
