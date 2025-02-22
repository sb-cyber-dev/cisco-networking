
# Verify Directly Connected Networks


---

## Verify interface status

```aiignore
show ip interface brief
show ipv6 interface brief
```

- status of all interfaces on the router
- verify interfaces are active and operational


---

## Verify IPv6 Link Local and Multicast Addresses

```aiignore
show ipv6 interface brief
show ipv6 interface gigabitethernet0/0/0
```

- two ipv6 addresses per interface:
  - ipv6 global unicast address (manual)
  - link-local unicast address (auto)


---

## Verify Interface Configuration

```aiignore
show running-config interface gigabitethernet 0/0/0
show interfaces

show ip interface
show ipv6 interface
```

- displays current commands applied to the specified interface


---


## Verify Routes

```
show ip route
show ipv6 route
```
- shows:
  - 3 directly connected network entries
  - 3 local host route interface entries

---

## Filter 'show' command output


---

### Section

```aiignore
show running-config | section line vty
```

- shows entire section, starting with filtering expression


---

### Include

```aiignore
show ip interface brief | include up
```

- includes all output lines that match the filtering expression


---

### Exclude

```aiignore
show ip interface brief | exclude unassigned
```

- excludes all output lines that match the filtering expression


---

### Begin

```aiignore
show ip route | begin Gateway
```

- start with line that matches the filtering expression

---


## Command History

```aiignore
terminal history size 200
show history
```



















