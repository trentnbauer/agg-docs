# Davinci Resolve Server

[Link to App](https://drs.trentbauer.com)

[Link to GitHub or Website](https://wirebear.co.uk/software/studio-server)

This tool syncs my Davinci Resolve project files to a single server, allowing me to edit on my laptop or PC

This app is hosted on Latte as a docker container

```yaml
version: '3'

services:
  app:
    image: allebb/studio-server:1.0.4-rc6
    restart: unless-stopped
    network_mode: bridge
    environment:
      - TZ=${TZ:-Australia/Melbourne}
    ports:
      - 5432:5432                 #DB             https://wirebear.co.uk/software/studio-server
      - 50059:50059               #Davinci Chat   https://wirebear.co.uk/software/studio-server
      - 8543:${PORTWEB:-8543}
    volumes:
      - hooks:/var/studio-server/hooks/
      - database:/var/studio-server/database/
      - jobs:/etc/cron.d/

volumes:
  hooks:
  database:
  jobs:
```

### Latte

| Port  | Purpose                      |
| ----- | ---------------------------- |
| 5432  | Resolve Server Database Port |
| 50059 | Chat client                  |
| 8543  | WebUI                        |

| Host Volume | Container Volume | Purpose |
| ----------- | ---------------- | ------- |
| Hooks       |                  |         |
| Database    |                  |         |
| Jobs        |                  |         |

| Integration | Purpose                         |
| ----------- | ------------------------------- |
| Cortado     | Network storage for raw footage |

\
