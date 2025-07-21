# Lidarr

[Link to Github](https://github.com/Lidarr/Lidarr)

[Link to access App](https://media.lattemedia.tv/lidarr)

Lidarr is a music collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new tracks from your favorite artists and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.

Lidarr hosted on Latte

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/lidarr.yml" %}

| Port | Purpose |
| ---- | ------- |
| 666  | Webui   |

| Host Volume      | Container Volume      | Purpose                                                                                                                                       |
| ---------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| media\_downloads | <p>/downloads<br></p> | Where qBittorrent downloads too. Required to access completed downloads to shift to the Media library. Stored of Fettuccine, accessed via NFS |
| media\_media     | <p><br>/music</p>     | Media library that Plex views. Required to manage metadata and add to library. Stored of Fettuccine, accessed via NFS                         |
