go to https://www.youtube.com/watch?v=8ZI8AYl6zaM&t=527s

pterodactyl Installer
https://github.com/vilhelmprytz/pterodactyl-installer

java docker image for paper mc on arm
https://github.com/Software-Noob/pterodactyl-images 

### [[Setup Firewall Rules]]

### Install Script for Pterodactyl 
```bash
sudo -s
bash <(curl -s https://raw.githubusercontent.com/pterodactyl-installer/pterodactyl-installer/master/install.sh)
```

### Install Script for Wings
```bash
sudo -s
bash <(curl -s https://raw.githubusercontent.com/vilhelmprytz/pterodactyl-installer/master/install-wings.sh)
```

### Start Wings 
```bash
systemctl start wings
```

### Display port ip address
```bash
hostname -I | awk '{print $1}
```

