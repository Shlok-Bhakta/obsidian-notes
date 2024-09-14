Entire Linux Distro on accessible from the web
[Docs](https://docs.linuxserver.io/images/docker-webtop)


## [[Docker Compose]] 
```yml
---
version: "2.1"
services:
  webtop:
    image: lscr.io/linuxserver/webtop:debian-kde # replace tag linuxserver.io
    container_name: webtop
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /home/shlok/webtop/config:/config # make sure this dir exists
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 3000:3000
      - 3001:3001
    restart: unless-stopped
```