# Bazarr

[Link to App](https://media.lattemedia.tv/bazarr)

[Link to GitHub or Website](https://www.bazarr.media/)

Bazarr is a companion application to Sonarr and Radarr. It manages and downloads subtitles based on your requirements. You define your preferences by TV show or movie and Bazarr takes care of everything for you.

This app is hosted on Latte as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/f4800fa7c650257cb88ac9ef4fd099c4c402a097/docker-compose/bazarr.yml" %}

| Port | Purpose |
| ---- | ------- |
| 6767 | WebUJ   |

| Host Volume    | Container Volume | Purpose              |
| -------------- | ---------------- | -------------------- |
| bazarr\_media  | /media           | Fettuccine NFS share |
| bazarr\_config | /config          | server configs       |

| Integration | Purpose             |
| ----------- | ------------------- |
| Radarr      | Pulls library items |
| Sonarr      | Pullsl ibrary items |

\
