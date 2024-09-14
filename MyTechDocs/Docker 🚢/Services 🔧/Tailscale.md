[talescale](https://tailscale.com)

## [[Docker Compose]]:
```yml
version: "2.4"
services:
  tailscale:
      privileged: true
      hostname: tailscale
      network_mode: "host"
      container_name: tailscale
      image: tailscale/tailscale:stable
      volumes:
          - "/opt/appdata/tailscale/var_lib:/var/lib" 
          - "/dev/net/tun:/dev/net/tun"                 
      cap_add:                                          
        - net_admin
        - sys_module
      command: tailscaled
      restart: unless-stopped
```

Run the following to have the abilityfor your Host device to be the `Exit Node`
```bash
docker exec tailscale tailscale up --advertise-exit-node
```

## Start Tailscale

```bash
sudo tailscale up --reset
```

```bash
sudo tailscale up --advertise-exit-node
```