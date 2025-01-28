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

