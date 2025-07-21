# Morphos

[Link to App](https://conversion.xfgn.dev)

[Link to GitHub or Website](https://github.com/danvergara/morphos)

Today we are forced to rely on third party services to convert files to other formats. This is a serious threat to our privacy, if we use such services to convert files with highly sensitive personal data. It can be used against us, sooner or later. Morphos server aims to solve the problem mentioned above, by providing a self-hosted server to convert files privately. The project provides an user-friendly web UI. For now, Morphos only supports images. Documents will be added soon.

This app is hosted on Cocoa as a docker container

The compose file is made up of 2 containers,

* Morphos (For editing files)
* Docker-TC (For limiting bandwidth to Morphos)

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/2129514009f0c9e93854ce54fef157ce834fcbb3/docker-compose/morphos.yml" %}

### Instance 1

| Port | Purpose |
| ---- | ------- |
| 8877 | WebUI   |

| Host Volume | Container Volume | Purpose               |
| ----------- | ---------------- | --------------------- |
| /tmp        | /tmp             | temp storage of files |

\
