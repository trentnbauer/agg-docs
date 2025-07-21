# Kasm

[Link to App](https://kasm.xfgn.dev)

[Link to GitHub or Website](https://kasmweb.com/)

Streaming containerized apps and desktops to end-users. The Workspaces platform provides enterprise-class orchestration, data loss prevention, and web streaming technology to enable the delivery of containerized workloads to your browser.

This app is hosted on Latte as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/3a839ccc55a1f28ee42b5673f5ffa4b13ab15465/docker-compose/kasm.yml" %}

| Port | Purpose    |
| ---- | ---------- |
| 3000 | Setup Port |
| 444  | WebUI      |

| Host Volume                           | Container Volume                     | Purpose                                      |
| ------------------------------------- | ------------------------------------ | -------------------------------------------- |
| /dev/input                            | /dev/input                           |                                              |
| kasm\_custom\_icons                   | /icons                               | Upload custom Icons                          |
| kasm\_opt                             | /opt                                 | Config                                       |
| /opt/kasm/current/log/agent\_json.log | opt/kasm/current/log/agent\_json.log | Exports sign-in logs for Crowdsec to monitor |
| kasm\_profiles                        | /profiles                            | Persistent profiles data                     |
| /run/udev/data                        | /run/udev/data                       |                                              |

| Integration  | Purpose                                           |
| ------------ | ------------------------------------------------- |
| Google OAuth | Account creation and management handled by Google |

\
