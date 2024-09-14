```bash
sudo firewall-cmd --zone=public --permanent --add-port=19132/tcp
sudo firewall-cmd --zone=public --permanent --add-port=19132/udp
sudo firewall-cmd --zone=public --permanent --add-port=25565/tcp
sudo firewall-cmd --zone=public --permanent --add-port=25565/udp
sudo firewall-cmd --zone=public --permanent --add-port=80/tcp
sudo firewall-cmd --zone=public --permanent --add-port=80/udp
sudo firewall-cmd --zone=public --permanent --add-port=443/tcp
sudo firewall-cmd --zone=public --permanent --add-port=443/udp
sudo firewall-cmd --zone=public --permanent --add-port=8080/tcp
sudo firewall-cmd --zone=public --permanent --add-port=8080/udp
sudo firewall-cmd --zone=public --permanent --add-port=2022/tcp
sudo firewall-cmd --zone=public --permanent --add-port=2022/udp
sudo firewall-cmd --zone=public --permanent --add-port=22/tcp
sudo firewall-cmd --zone=public --permanent --add-port=22/udp
sudo firewall-cmd --zone=public --permanent --add-port=5657/tcp
sudo firewall-cmd --zone=public --permanent --add-port=5657/udp
sudo firewall-cmd --zone=public --permanent --add-port=55423/tcp
sudo firewall-cmd --zone=public --permanent --add-port=55423/udp
sudo firewall-cmd --zone=public --permanent --add-port=8123/tcp
sudo firewall-cmd --zone=public --permanent --add-port=8123/udp
sudo firewall-cmd --zone=public --permanent --add-port=54372/tcp
sudo firewall-cmd --zone=public --permanent --add-port=54372/udp
sudo firewall-cmd --zone=public --permanent --add-port=56756/tcp
sudo firewall-cmd --zone=public --permanent --add-port=56756/udp
sudo firewall-cmd --zone=public --permanent --add-port=19133/tcp
sudo firewall-cmd --zone=public --permanent --add-port=19133/udp
sudo firewall-cmd --zone=public --permanent --add-port=19131/tcp
sudo firewall-cmd --zone=public --permanent --add-port=19131/udp
sudo firewall-cmd --zone=public --permanent --add-port=45645/tcp
sudo firewall-cmd --zone=public --permanent --add-port=45645/udp
sudo firewall-cmd --reload
echo Firewall stuff Finished
```
