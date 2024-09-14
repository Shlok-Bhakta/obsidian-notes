[docs](https://netplan.readthedocs.io/en/stable/netplan-tutorial/#running-netplan-for-the-first-time)

Example config File
```yaml
network:
  version: 2
  ethernets:
    enp6s18:
      dhcp4: false
      dhcp6: false
      accept-ra: false
      link-local: []
      addresses:
        - 10.11.1.239/22
      routes:
        - to: default
          via: 10.11.0.1
      nameservers:
        search:
          - netplanlab.local
        addresses:
          - 10.11.0.1
          - 1.1.1.1
```

