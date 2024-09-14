Should just be a full version of windows in a docker container with web gui like [[Webtop]] 
[Github](https://github.com/dockur/windows)

## [[Docker Compose]] 
```yaml
version: "3"
services:
  windows:
    image: dockurr/windows
    container_name: windows
    devices:
      - /dev/kvm
    cap_add:
      - NET_ADMIN
    ports:
      - 8006:8006
      - 11278:3389/tcp
      - 3389:3389/udp
    environment:
	  VERSION: "tiny11"
	  RAM_SIZE: "4G"
	  CPU_CORES: "2"
	  DISK_SIZE: "64G"
	volumes
	  - /var/win:/storage #This will eat at least 64 gb storage so please chuck it somewhere else
    stop_grace_period: 2m
    restart: on-failure
```


