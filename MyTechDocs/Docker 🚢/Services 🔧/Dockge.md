[Github](https://github.com/louislam/dockge)

```yaml
version: "3.8"
services:
  dockge:
    image: louislam/dockge:latest
    restart: unless-stopped
    ports:
      # Host Port : Container Port
      - 25000:5001
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /home/dockge/data:/app/data
      - /home/dockge/stacks:/home/dockge/stacks
    environment:
      # Tell Dockge where is your stacks directory
      - DOCKGE_STACKS_DIR=/home/dockge/stacks
```