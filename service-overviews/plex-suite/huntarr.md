# Huntarr

[Link to App](https://huntarr.lattemedia.tv)

[Link to GitHub or Website](https://github.com/plexguide/Huntarr.io)

This application continually searches your media libraries for missing content and items that need quality upgrades. It automatically triggers searches for both missing items and those below your quality cutoff. It's designed to run continuously while being gentle on your indexers, helping you gradually complete your media collection with the best available quality.

This app is hosted on Latte as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/huntarr.yml" %}

| Port | Purpose |
| ---- | ------- |
| 9705 | Web UI  |

| Host Volume     | Container Volume | Purpose             |
| --------------- | ---------------- | ------------------- |
| huntarr\_config | /config          | Configuration files |

| Integration            | Purpose        |
| ---------------------- | -------------- |
| Lidarr, Radarr, Sonarr | Manage library |

\
