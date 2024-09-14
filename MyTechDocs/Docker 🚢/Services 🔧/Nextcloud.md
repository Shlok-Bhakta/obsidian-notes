Nextcloud is an alternative to google drive self hosted
[github](https://github.com/nextcloud/all-in-one)

## [[Docker Compose]] 
```yml
services:
  nextcloud:
    image: lscr.io/linuxserver/nextcloud:latest
    container_name: nextcloud
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /home/dockerservices/nextclouddata/config:/config
      - /home/dockerservices/nextclouddata/data:/data
    ports:
      - 16489:80
    restart: unless-stopped
networks: {}
```
