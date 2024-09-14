# [[Linux]] 
## Install (raspberry pi os bullseye)
```bash
sudo apt-get install samba samba-common-bin
```

## Current Config
```bash
cd /etc/samba/smb.conf
```
- default path of the config 

```/etc/samba/smb.conf
[content]
comment = place to store content
path = "home/shlok/USBHDD"
writeable = Yes
guest ok = Yes
create mask = 0777
directory mask = 0777
```
- insert at the bottom of the file
- make sure the path exists
- make sure to [[Change Permission]] of the drive and location 

## Restart
```bash
sudo systemctl restart smbd
```
- requires restart after editing the config