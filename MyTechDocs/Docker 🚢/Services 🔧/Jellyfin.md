Stream content to your devices like Netflix
[linuxserver.io](https://docs.linuxserver.io/images/docker-jellyfin)

## [[Docker Compose]]:
```yml
version: "2.1"
services:
  jellyfin:
    image: lscr.io/linuxserver/jellyfin:latest
    container_name: jellyfin
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - /home/shlok/jellyfin/library:/config
      - /home/shlok/jellyfin/tvshows:/data/tvshows
      - /home/shlok/jellyfin/movies:/data/movies
    ports:
      - 8096:8096
      - 8920:8920 #optional
      - 7359:7359/udp #optional
      - 1900:1900/udp #optional
    restart: unless-stopped
```