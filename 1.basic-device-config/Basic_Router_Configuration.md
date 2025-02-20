

# Basic Router Configuration


---


## Initial Router Configuration

Cisco routers have similar initial configuration as Cisco switches

```aiignore
Router(config)# hostname R1
R1(config)# enable secret class
R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# service password-encryption


R1(config)# banner motd #Authorized Access Only!#


R1(config)# copy running-config startup-config
```




---

## Dual Stack Topology

- Allows both IPv4 and IPv6 to run simultaneously. 
- Allows seamless transition/migration to IPv6


---



## Configure Router Interfaces

Interface availability requirements:

- At least 1 IP address configured
- Activate (no shutdown)
- Connected to another device on physical layer
- (Optional) Short description



```aiignore
R1(config)# interface gigabitEthernet 0/0/0
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# description Link to LAN 1
R1(config-if)# no shutdown
R1(config-if)# exit

R1(config)# interface gigabitEthernet 0/0/1
R1(config-if)# ip address 192.168.11.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64
R1(config-if)# description Link to LAN 2
R1(config-if)# no shutdown
R1(config-if)# exit

[ WAN interface ]
R1(config)# interface serial 0/0/0
R1(config-if)# ip address 209.165.200.225 255.255.255.252
R1(config-if)# ipv6 address 2001:db8:acad:3::225/64
R1(config-if)# description Link to R2
R1(config-if)# no shutdown
R1(config-if)# exit


```


## IPv4 Loopback Interface

- router's internal logical interface
- no physical port, only a software interface
- automatically placed in an "up" state
- useful for testing:
  - testing internal routing processes
  - emulate networks behind router
  - simulate a link to the internet
- useful as a lab environment for additional interfaces:
  - create multiple loopback interfaces to simulate more networks


Enable and assign a loopback address
```aiignore
R1(config)# interface loopback (number)
R1(config)# ip address (ip-address) (subnet-mask)
```

For multiple loopback interfaces enabled on a router:
- each loopback interface must have unique IPv4 address








