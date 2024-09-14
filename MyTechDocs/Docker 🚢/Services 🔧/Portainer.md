a way to easily manage docker containers 

Allocate to Port 9000

Installation for cli
```bash
sudo docker run -d -p 9000:9000 -p 9443:9443 --name=portainer --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

for single server use make sure to set up a [[macvlan]] 