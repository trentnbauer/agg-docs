# Tdarr

[Link to App](https://tdarr.lattemedia.tv)

[Link to GitHub or Website](https://github.com/HaveAGitGat/Tdarr)

Tdarr V2 is a cross-platform conditional based transcoding application for automating media library transcode/remux management in order to process your media files as required. For example, you can set rules for the required codecs, containers, languages etc that your media should have which helps keeps things organized and can increase compatability with your devices. A common use for Tdarr is to simply convert video files from h264 to h265 (hevc), saving 40%-50% in size.

I am using Tdarr to grab any files NOT h265 that are over 30mbit and convert them to h265, resulting in smaller file sizes.

This app contains multiple containers,

* Server
* Node/s

This app is hosted on Latte as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/e7217429b4938fae60ea28885135cc6ab74c3e15/docker-compose/tdarr-serv.yml" %}

### Instance 1

| Port | Purpose                                |
| ---- | -------------------------------------- |
| 8265 | Webui                                  |
| 8266 | Port for Server and Node communication |

| Host Volume           | Container Volume | Purpose                                                    |
| --------------------- | ---------------- | ---------------------------------------------------------- |
| /cache                | /cache           | [dedicated cache SSD](../../physical-hardware/macaroni.md) |
| tdarr-server\_media   | /media           | NFS share to NAS, stores content                           |
| tdarr-server\_configs | /app/configs     | Configuration files                                        |
| tdarr-server\_server  | /app/server      |                                                            |
| tdarr-server\_logs    | /app/logs        |                                                            |
| /etc/hostname         | /etc/hostname    | Read only                                                  |

| Integration | Purpose |
| ----------- | ------- |
|             |         |

\
