
# [[Docker Compose]] 
gotten from reddit :/

```yml
version: "3.8"
services: 
  cloudflared: 
    image: cloudflare/cloudflared 
    container_name: cloudflare-tunnel 
    restart: unless-stopped 
    command: tunnel run 
    environment: 
      - TUNNEL_TOKEN=[Token Here] # generate a token at cloudflare.com
```
