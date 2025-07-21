---
coverY: 0
---

# Pterodactyl

[Link to App](https://panel.agamersgrind.com)

Pterodactyl® is a free, open-source game server management panel built with PHP, React, and Go. Designed with security in mind, Pterodactyl runs all game servers in isolated Docker containers while exposing a beautiful and intuitive UI to end users.

You can follow my guide on the public documentation site to replicate my set up :)&#x20;

## Flowchart

### Software Level

This flowchart shows how the apps integrate

<img src="../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

### Hardware Level

This flowchart shows what lives where

<img src="../.gitbook/assets/file.excalidraw (5).svg" alt="" class="gitbook-drawing">

## Panel

The Panel is hosted on Cocoa, as a docker container

The Panel stack is made up of 3 containers,

* Redis
* MariaDB
* Panel Application

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/0c971ff4d4fc9e2b4aef55d440b2304f5b4b1b04/docker-compose/pterodactyl-panel.yml" %}

### Redis

| Host Volume        | Container Volume | Purpose                              |
| ------------------ | ---------------- | ------------------------------------ |
| Randomly Generated | /data            | Stores the cached files... I assume? |

### MariaDB

| Host Volume               | Container Volume | Purpose           |
| ------------------------- | ---------------- | ----------------- |
| /srv/pterodactyl/database | /var/lib/mysql   | Database location |

### Panel

| Port | Purpose                |
| ---- | ---------------------- |
| 809  | WebUI HTTP             |
| 4439 | WebUI HTTPS (not used) |

| Host Volume       | Container Volume   | Purpose                          |
| ----------------- | ------------------ | -------------------------------- |
| pteropanel\_var   | /app/var           | Contains configuration .env file |
| pteropanel\_nginx | /etc/ngix/http.d   |                                  |
| pteropanel\_certs | /etc/letsencrypt   |                                  |
| pteropanel\_logs  | /apps/storage/logs |                                  |

| Integration | Purpose                                          |
| ----------- | ------------------------------------------------ |
| Mocha       | Connect to the Wings container to manage servers |

## Wings

[Link to GitHub or Website](https://github.com/pterodactyl/wings)

Wings is Pterodactyl's server control plane, built for the rapidly changing gaming industry and designed to be highly performant and secure. Wings provides an HTTP API allowing you to interface directly with running server instances, fetch server logs, generate backups, and control all aspects of the server lifecycle.

This app is hosted on Mocha and Cola as a docker container

This stack is made up of 2 containers,

* Wings
* MariaDB

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/0c971ff4d4fc9e2b4aef55d440b2304f5b4b1b04/docker-compose/pterodactyl-wings.yml" %}

### Wings

| Port | Purpose                                   |
| ---- | ----------------------------------------- |
| 443  | Panel Connection Port (Cloudflare Tunnel) |
| 2022 | SFTP                                      |
| 8080 | Daemon port (unused)                      |

| Host Volume                 | Container Volume           | Purpose                             |
| --------------------------- | -------------------------- | ----------------------------------- |
| /var/run/docker.sock        | /var/run/docker.sock       | Manage Docker containers ( servers) |
| /var/lib/docker/containers/ | var/lib/docker/containers/ |                                     |
| etc                         | /etc/pterodactyl/          | Config file lives here              |
| /var/lib/pterodactyl/       | /var/lib/pterodactyl/      |                                     |
| /var/log/pterodactyl/       | /var/log/pterodactyl/      |                                     |
| /tmp/pterodactyl/           | /tmp/pterodactyl/          |                                     |
| /srv/daemon-data/           | /srv/daemon-data/          |                                     |

| Integration | Purpose                      |
| ----------- | ---------------------------- |
| Panel       | Panel manages wings instance |

### **MariaDB**

| Port | Purpose                 |
| ---- | ----------------------- |
| 3306 | Port to access Database |

| Host Volume | Container Volume | Purpose           |
| ----------- | ---------------- | ----------------- |
| db          | /var/lib/mysql   | Database location |

| Integration | Purpose                |
| ----------- | ---------------------- |
| Panel       | Panel manages database |
