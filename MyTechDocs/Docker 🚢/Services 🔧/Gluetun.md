
[github](https://github.com/qdm12/gluetun)

>[!warning]
>in the /gluton folder make sure to copy over client.crt and client.key
# [[Docker Compose]]
```yaml
version: "3.3"
services:
  gluetun:
    image: qmcgaw/gluetun
    container_name: gluetun
    cap_add:
      - NET_ADMIN
    devices:
      - /dev/net/tun:/dev/net/tun
    ports:
      - 8888:8888/tcp # HTTP proxy
      - 8388:8388/tcp # Shadowsocks
      - 8388:8388/udp # Shadowsocks
      - 6881:6881 #torrent protocol I think?
      - 6881:6881/udp #torrent protocol I think?
      - 8989:8989 # Sonarr
      - 9096:9096 # Prowlarr
      - 8085:8085 # Qbittorrent
    volumes:
      - /home/shlok/glueton:/gluetun
    environment:
      # See https://github.com/qdm12/gluetun-wiki/tree/main/setup#setup
      - VPN_SERVICE_PROVIDER=cyberghost
      - VPN_TYPE=openvpn
      - OPENVPN_USER=mjByQah6v4
      - OPENVPN_PASSWORD=XuHdBa9D8t
      - TZ=America/Chicago
```



