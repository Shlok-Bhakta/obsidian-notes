Full backend for apps [Website](https://pocketbase.io) / [Third Party Github](https://github.com/muchobien/pocketbase-docker)

## [[Docker Compose]] 
```yml
version: "3.7"
services:
  pocketbase:
    image: ghcr.io/muchobien/pocketbase:latest
    container_name: pocketbase
    restart: unless-stopped
    ports:
      - "8090:8090"
    volumes: # make directory (change left side) EX: (change:keep)
      - ~/pocketbase/data:/pb_data # Create a directory called data
      - ~/pocketbase/public:/pb_public # Create a directory called public 
    healthcheck: 
      test: wget --no-verbose --tries=1 --spider http://localhost:8090/api/health || exit 1
      interval: 5s
      timeout: 5s
      retries: 5
```
