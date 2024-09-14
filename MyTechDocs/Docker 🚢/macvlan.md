A way to put services from [[Docker]] onto different ip addresses on one physical port so container can have their own ip address
[macvlan docs](https://docs.docker.com/network/macvlan/#:~:text=To%20create%20a%20macvlan%20network%20which%20bridges%20with,will%20physically%20go%20through%20on%20the%20Docker%20host) 


## How to set up a [[macvlan]] in [[Portainer]] 

- First run
```bash
ip a
```
- Find a the network interface that doesn't seem completely stupid
- Go to [[Portainer]] (CE / Server Version: 2.17.1)
- Go to network 
- Click on add network 
	![[Pasted image 20230412153226.png]]
- Give it a name such as mymacvlanconfig and set the driver to [[macvlan]]
![[Pasted image 20230412153408.png]]
- Set config options
	- Subnet EX: 192.168.1.0/24
	- Gateway EX: 192.168.1.1
	- IP Range EX: 192.168.1.150/28
- Click "Create network"
- Click add Network Again
	![[Pasted image 20230412153226.png]]
- Give it a name such as mymacvlan and set the driver to [[macvlan]] 
- Click Creation This time
- Under the configuration dropdown select mymacvlanconfig 
- Enable manual container attachment
	![[Pasted image 20230412153852.png]]
- Click "Create network" 
----------------------------------------------------------------------------