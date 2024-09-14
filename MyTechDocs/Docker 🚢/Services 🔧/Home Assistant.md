Managing Your home
[website](https://www.home-assistant.io) / [github](https://github.com/home-assistant/core)

## [[Docker Compose]]:
### Official HASSIO Compose File (didn't work last time)

```yml docker-compose
version: '2'

services:
  homeassistant:
    container_name: homeassistant
    image: "ghcr.io/home-assistant/home-assistant:stable"
    volumes:
      - /home/shlok/haconf:/config # make sure to have a config path on host
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 80:80
      - 443:443
    restart: unless-stopped
    privileged: true

```

### Linuxserver.io Compose File (did work)

```yaml docker-compose
version: "2.1"
services:
  homeassistant:
    image: lscr.io/linuxserver/homeassistant:latest
    container_name: homeassistant
    network_mode: host
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - /homeassistant:/config
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 8123:8123
    restart: unless-stopped
    privileged: true
```


## Install Hacs
- inside the container
```bash
wget -O - https://get.hacs.xyz | bash -
```
- restart the container 
- go to the place to get integrations and search HACS
- Install


## Setup with [[Cloudflared]] 

- Add config to [[Cloudflared]] 

- Try to connect to the web gui over the tunnel

- Open logs in [[Portainer]]

- should see an error along the lines of
`2023-11-09 22:36:38.780 ERROR (MainThread) [homeassistant.components.http.forwarded] Received X-Forwarded-For header from an untrusted proxy 172.18.0.2`

- edit the config file (default location)
```shell
sudo nano /homeassistant/configuration.yaml
```

- add to the bottom of the file
```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 192.168.1.140
    - 172.18.0.2 # change this to the ip from the log
```
- Change the 172.19.0.2 to the ip from the log

- restart the container

