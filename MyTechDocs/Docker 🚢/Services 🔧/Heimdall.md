
Use [[Homarr]] 

## [[Docker Compose]] 
```yml
version: "2.1"
services:
  heimdall:
    image: lscr.io/linuxserver/heimdall:latest
    container_name: heimdall
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - /home/shlok/hiemconf:/config # make sure to have a config path
    ports:
      - 80:80
      - 443:443
    restart: unless-stopped
```

