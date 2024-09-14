A torrent client that works on the web
:luc_github: [github](https://github.com/qbittorrent/qBittorrent)

>[!warning]
>Not Even going to provide the config without the vpn container it is **very** important that you use a vpn when using this check out [[Gluetun]]
# [[Docker Compose]] 
```yaml
version: "3.3"
services:
  qbittorrent:
    image: lscr.io/linuxserver/qbittorrent:latest
    container_name: qbittorrent
    network_mode: service:gluetun
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
      - WEBUI_PORT=8085
      - DOCKER_MODS=ghcr.io/themepark-dev/theme.park:qbittorrent
    volumes:
      - /home/shlok/qbittorrent/config:/config
      - /home/shlok/qbittorrent/downloads:/downloads
    depends_on:
      - gluetun
    restart: always
```
