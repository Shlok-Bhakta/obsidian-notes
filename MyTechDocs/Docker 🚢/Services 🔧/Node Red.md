
# [[Docker Compose]] 
Gotten from [NodeRed Docs](https://nodered.org/docs/getting-started/docker)



```yml
version: "3.7"

services:
  node-red:
    image: nodered/node-red:latest
    environment:
      - TZ=America/Chicago
    ports:
      - "1880:1880"
    volumes:
      - /home/shlok/noderedconf:/data # Create a noderedconf folder on host
```