

# Secure Remote Access

---


## Telnet Operation

- Uses TCP port 23
- unsecure plaintext authentication and data transmission


---

## SSH Operation

- Uses TCP port 22
- Provides encrypted management connection to a remote device


### Verify Switch supports SSH

```aiignore
show version
show ip ssh
```

[ If IOS filename includes "k9", it supports encrypted features ]


---


## Configure SSH

---

### Prerequisite

- Unique hostname
```aiignore
hostname S1
```

- IP address configuration
- VLAN configuration
- Default Gateway (if accessing from different subnet)
```aiignore
ip default-gateway 192.168.1.1
interface vlan 1
ip address 192.168.1.100 255.255.255.0
no shutdown
```



### SSH Configuration Steps

Force SSH Version 2 (More secure, but not always used by default)
```aiignore
configure terminal
ip ssh version 2
exit
write memory
```



Configure IP domain
```aiignore
S1(config)# ip domain-name cisco.com
```

Generate RSA key pairs (Automatically enables SSH)
```aiignore
S1(config)# crypto key generate rsa
(modulus length = ) 1024 or higher
```


Configure User Authentication

- Local Authentication
```aiignore
S1(config)# username admin secret password
```


Configure VTY lines
```aiignore
line vty 0 15
transport input ssh
login local   (use local username auth)
(OR set password `password MyPassword`)
(OR use password `login`)
```



---

### Test SSH Login

```aiignore
ssh 192.168.1.1
```






---







### Delete RSA key pair

(SSH server is auto disabled when RSA key pair is deleted)
```aiignore
S1(config)# crypto key zeroize rsa
```






