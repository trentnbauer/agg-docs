# Duplicati

[Link to App](https://duplicati.xfgn.dev)

[Link to GitHub or Website](https://www.duplicati.com/)

Duplicati is a backup client that securely stores encrypted, incremental, compressed remote backups of local files on cloud storage services and remote file servers.

This app is hosted on Macaroni as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/duplicati.yml" %}

| Port | Purpose |
| ---- | ------- |
| 8200 | Webui   |

| Integration                          | Purpose                 |
| ------------------------------------ | ----------------------- |
| [Google Drive](google-drive-sync.md) | Backups to Google Drive |
