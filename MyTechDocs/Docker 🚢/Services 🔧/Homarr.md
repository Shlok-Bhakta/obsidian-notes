[Github](https://github.com/ajnart/homarr)

A simple, yet powerful dashboard for your server.
Allocate to Port 25001
## [[Docker Compose]] 
```
version: '3'
services:
  homarr:
    container_name: homarr
    image: ghcr.io/ajnart/homarr:latest
    restart: unless-stopped
    volumes:
      - ~/homarr/configs:/app/data/configs
      - ~/homarr/icons:/app/public/icons
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - '25001:7575'
```
