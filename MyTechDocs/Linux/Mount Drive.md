# [[Linux]]
```bash
sudo mount -t auto /dev/sda1 /home/shlok/USBHDD/
```
- /dev/sda1 is the drive location 
- /home/shlok/USBHDD is the destination

Might need to reformat drive if it was used on windows before

## Mounting on reboot

##### Docs from
https://confluence.jaytaala.com/display/TKB/Mount+drive+in+linux+and+set+auto-mount+at+boot

Make a folder in the media directory (make one for each drive)
```bash
mkdir /home/shlok/usb1
```

To find the drive uuid run 
```bash
ls -al /dev/disk/by-uuid/ | awk '{for (i=9; i<=NF; i++) printf "%s ", $i; print ""}'
```

Open /etc/fstab
```bash
sudo nano /etc/fstab
```

FORMAT:
`# <file system> <mount point>   <type>  <options>       <dump>  <pass>`
UUID is the uuid from the earlier command 
change /home/shlok/usb1 to be the right spot
```bash
UUID=datapartition /home/shlok/usb1 ext4 defaults 0 0
```


## Checking Mount Location
```bash
mount | grep sda
```
- replace sda with the drive

## Mount Info
```bash
dmesg | grep sda
```
- replace sda with the drive 

