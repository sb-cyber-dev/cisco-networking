# Commands

---


## Set Basic Passwords

---



### Set Privileged EXEC Mode Password (Enable Secret)

```aiignore
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#enable secret secretpasswordvalue
```

---


### Set Console Access Password

Secures access via console port

```aiignore
Switch(config)#line console 0
Switch(config-line)#password secretpasswordvalue
Switch(config-line)#login            // enables password verification
Switch(config-line)#exit
```

---

### Set VTY (Remote Access) Password

Secures remote access (via Telnet or SSH)

```aiignore
Switch(config)#line vty 0 4
Switch(config-line)#password secretpasswordvalue
Switch(config-line)#login
Switch(config-line)#exit
```


---

## Switch SVI Configuration Example


*Note: Switch by default has management controlled through VLAN 1. All ports assigned to VLAN 1 by default. Best practice to use different VLAN for management.*

```aiignore
S1#configure terminal
S1(config)#interface vlan 99
S1(config-if)#ip address 10.0.0.11 255.255.255.0
S1(config-if)#no shutdown
S1(config-if)#end
S1(config)#ip default-gateway 10.0.0.12
S1#copy running-config startup-config
```
*Note: The SVI will not appear as "up/up" until the VLAN is created and there is a device connected to a switch port associated with the VLAN.*


---


## Show commands

Determine status of both physical and virtual interfaces

```aiignore
S1# show ip interface brief
S1# show ipv6 interface brief
```

