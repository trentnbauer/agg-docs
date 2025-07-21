# Dashdot

[Link to App](https://stats.lattemedia.tv/)

[Link to GitHub or Website](https://github.com/MauriceNino/dashdot)

dash. (or dashdot) is a modern server dashboard, running on the latest tech, designed with glassmorphism in mind. It is intended to be used for smaller VPS and private servers.

This app is hosted on Latteas a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/4f6df13067a0c5090aa36eb3502749c9283f865a/docker-compose/dashdot-nvidia.yml" %}

| Port | Purpose |
| ---- | ------- |
| 3001 | WebUI   |

| Host Volume | Container Volume | Purpose         |
| ----------- | ---------------- | --------------- |
| /           | /mnt/host:ro     | Read disk usage |

| Integration | Purpose |
| ----------- | ------- |
|             |         |

\
