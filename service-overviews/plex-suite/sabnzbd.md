# SabNZBD

[Link to App](https://media.lattemedia.tv/sabnzbd)

[Link to GitHub or Website](https://sabnzbd.org/)

SABnzbd is an Open Source Binary Newsreader written in Python.

It's totally free, easy to use, and works practically everywhere. SABnzbd makes Usenet as simple and streamlined as possible by automating everything we can. All you have to do is add an `.nzb`. SABnzbd takes over from there, where it will be automatically downloaded, verified, repaired, extracted and filed away with zero human interaction. SABnzbd offers an easy setup wizard and has self-analysis tools to verify your setup.

This app is hosted on Fettuccine as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/205cfc374516886a137f2f0b66dca9c87fa0f740/docker-compose/sabnzbd.yml" %}



| Port | Purpose |
| ---- | ------- |
| 1234 | WebUI   |

<table><thead><tr><th width="265">Host Volume</th><th width="237.33333333333331">Container Volume</th><th>Purpose</th></tr></thead><tbody><tr><td>/volume1/downloads/nzbd/completed</td><td>/volume1/downloads/nzbd/completed</td><td>Completed download storage</td></tr><tr><td>/volume1/downloads/nzbd/incomplete</td><td>/volume1/downloads/nzbd/incomplete</td><td>Incomplete download storage</td></tr><tr><td>sabnzbd_config</td><td>/config</td><td>Configutation files</td></tr></tbody></table>

\
