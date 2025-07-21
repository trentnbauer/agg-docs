# Plex

Plex can be access via [https://plex.tv](https://plex.tv/)&#x20;

A one-stop destination to stream movies, TV shows, and music, Plex is the most comprehensive entertainment platform available today. Available on almost any device, Plex is the first-and-only streaming platform to offer free ad-supported movies, shows, and live TV together with the ability to easily search—and add to your Watchlist—any title ever made, no matter which streaming service it lives on. Using the platform as their entertainment concierge, 17 million (and growing!) monthly active users count on Plex for new discoveries and recommendations from all their favorite streaming apps, personal media libraries, and beyond.

Plex is installed on Latte as a docker container. The GTX 1650 in the server has been passed through to this VM to allow for hardware encoding.

The video and audio content that Plex streams is stored on Fettuccine

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/205cfc374516886a137f2f0b66dca9c87fa0f740/docker-compose/plex.yml" %}

| **Port**             | **Purpose**                   |
| -------------------- | ----------------------------- |
| 32400 (Port Forward) | Display webUI, stream content |

| **Host Volume** | **Container Volume** | **Purpose**                                       |
| --------------- | -------------------- | ------------------------------------------------- |
| plex\_media     | /nfs/Media           | nfs mount of the Media share on Fettuccine        |
| /dev/shm        | /dev/shm             | RAM. Used for storing live-transcoded data        |
| plex\_app       | /config              | Stores the Plex database, config, thumbnails etc. |

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg.local/blob/main/docker-compose/plex.yml" %}
