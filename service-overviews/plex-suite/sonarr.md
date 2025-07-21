# Sonarr

[Link to Github](https://github.com/Sonarr/Sonarr)

Sonarr is a PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.

My instances of Sonarr are hosted on Latte

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/205cfc374516886a137f2f0b66dca9c87fa0f740/docker-compose/sonarrv4.yml" %}

## [**1080p**](https://media.xfgn.dev/sonarr)

The general instance of Sonarr, used to capture 720 and 1080p content

| Port | Purpose |
| ---- | ------- |
| 8989 | Webui   |

| Host Volume       | Container Volume      | Purpose                                                                                                                                       |
| ----------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| media\_downloads  | <p>/downloads<br></p> | Where qBittorrent downloads too. Required to access completed downloads to shift to the Media library. Stored of Fettuccine, accessed via NFS |
| media\_media      | <p><br>/movies</p>    | Media library that Plex views. Required to manage metadata and add to library. Stored of Fettuccine, accessed via NFS                         |
| media\_backups    | /backups              | Dedicated shared backup volume                                                                                                                |
| media\_sonarr1080 | /config               | Config files                                                                                                                                  |

| Integration | Purpose                                  |
| ----------- | ---------------------------------------- |
| qBittorrent | To add and monitor downloading contented |

## [**4k**](https://media.xfgn.dev/s4k)

The 4k instance of Sonarr. This content is (generally) not available outside of home

| Port | Purpose |
| ---- | ------- |
| 8990 | Webui   |

| Host Volume      | Container Volume      | Purpose                                                                                                                                       |
| ---------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| media\_downloads | <p>/downloads<br></p> | Where qBittorrent downloads too. Required to access completed downloads to shift to the Media library. Stored of Fettuccine, accessed via NFS |
| media\_media     | <p><br>/movies</p>    | Media library that Plex views. Required to manage metadata and add to library. Stored of Fettuccine, accessed via NFS                         |
| media\_backups   | /backups              | Dedicated shared backup volume                                                                                                                |
| media\_sonarr4k  | /config               | Config files                                                                                                                                  |

| Integration | Purpose                                  |
| ----------- | ---------------------------------------- |
| qBittorrent | To add and monitor downloading contented |
