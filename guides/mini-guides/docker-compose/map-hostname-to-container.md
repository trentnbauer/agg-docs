# Map hostname to container



```yaml
version: "2.3"
services:
  app:
    image: myimage:version
    restart: unless-stopped
    volumes:
      - /etc/hostname:/etc/hostname:ro
....
```
