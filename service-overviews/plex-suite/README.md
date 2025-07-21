---
coverY: 0
---

# Plex Suite

Plex is a tool for streaming local content to other devices. The Plex app is available on practically everything that other streaming services are (eg Netflix)

The other apps listed in this doco are here to integrate, manage and automate various systems to provide our viewers with the best content possible

## Suite Summary

<table><thead><tr><th width="155">App Name</th><th>Purpose</th></tr></thead><tbody><tr><td>Plex</td><td>Streams locally stored video and audio to Plex clients</td></tr><tr><td>Overseerr</td><td>Adds content to Radarr and Sonarr</td></tr><tr><td>Prowlarr</td><td>Searches torrent sites and NZB indexers for content</td></tr><tr><td>Bazarr</td><td>Searches for and downloads Subtitles</td></tr><tr><td>Sonarr</td><td>Automates the process of downloading and storing TV series</td></tr><tr><td>Radarr</td><td>Automates the process of downloading and storing movies</td></tr><tr><td>Lidarr</td><td>Automates the process of downloading and storing music</td></tr><tr><td>Maintainerr</td><td>Automates deletion of content based on specified criteria</td></tr><tr><td>Tdarr</td><td>Converts media from 1 format to another</td></tr><tr><td>qBittorrent</td><td>Downloads Torrents</td></tr><tr><td>SabNZBD</td><td>Downloads from Usenet servers</td></tr><tr><td>Tautulli</td><td>Pulls data from Plex server, such as watched content and active users</td></tr><tr><td>MovieMatch</td><td>Tinder for movies, looks at content on Plex server</td></tr><tr><td>FlareSolverr</td><td>Attempts to bypasses Captcha and bot challenges</td></tr><tr><td>Wizarr</td><td>User invite and management tool for Plex</td></tr><tr><td><a href="../infrastructure/cloudflare.md#zero-trust">CF Tunnel</a></td><td>Makes internally hosted applications externally accessible. Routes / proxies via Cloudflare, keeping the host secure</td></tr><tr><td>Huntarr</td><td>Automates searching for and upgrading existing content</td></tr><tr><td>Decluttar</td><td>A script that hooks into the *Arr apps to remove stalled and stuck downloads</td></tr><tr><td>Monitarr</td><td>Hooks into Sonarr and Radarr to view downloads and ETAs in 1 web app</td></tr></tbody></table>

## Flowcharts <a href="#bkmrk-flowchart" id="bkmrk-flowchart"></a>

### Software Defined flowchart

This flowchart shows how the various applications link together at a software level

<img src="../../.gitbook/assets/file.excalidraw (3).svg" alt="" class="gitbook-drawing">

### Hardware defined flowchart

This flowchart shows the hardware side of things - what servers the applications live and tunnels to them

<img src="../../.gitbook/assets/file.excalidraw (4).svg" alt="" class="gitbook-drawing">
