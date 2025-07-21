# qBittorrent

[Link to Access App](https://torrent.xfgn.dev/)

[Link to Download App](https://www.qbittorrent.org/)

qBittorrent is a cross-platform free and open-source BitTorrent client written in native C++. It relies on Boost, Qt 6 toolkit and the libtorrent-rasterbar library (for the torrent back-end), with an optional search engine written in Python.

qBittorrent is hosted on Fettuccine, as a docker containe

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/205cfc374516886a137f2f0b66dca9c87fa0f740/docker-compose/qbittorrent.yml" %}

| **Port** | **Purpose** |
| -------- | ----------- |
| 8080     | WebUI       |

| **Host Volume**     | **Container Volume** | **Purpose**          |
| ------------------- | -------------------- | -------------------- |
| /volume1/downloads  | /volume1/downloads   | Downloading directly |
| qbittorrent\_config | /config              | config files         |
| qbittorent\_data    | /data                | logs, backups        |

\
