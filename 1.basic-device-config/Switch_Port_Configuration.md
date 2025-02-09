
# Switch Port Configuration

---

## Topics

- Duplex Communication
- Switch Port Configuration
- 




---

## Duplex Communication

### Full Duplex Communication

- Bidirectional
- Increases bandwidth efficiency (offers 100% efficiency in both directions)
- Allow both ends of a connection to transmit and receive data simultaneously
- No collision domain (Collision detection circuit on MIC is disabled in FD mode)
- Micro-segmented LAN is created when switch PORT has:
  - only **one device** connected
  - operating in full-duplex mode


### Half Duplex Communication

- Unidirectional
- Performance issues, data can flow in only one direction at a time
- Often results in collision
- Typically seen in older hardware (hubs)

---


## (Physical Layer) Switch Port Configuration

---




### Additional Features/Topics

#### Auto-negotiation

- Between switch and connected device
- exchanges FLP (Fast Link Pulse) to determine highest mutually supported speed and duplex mode
- Not supported by Fiber-optic ports
- Failure:
  - Leads to mismatch in speed and suplex settings
  - Causes collisions and retransmission
  - Slow performance and Packet loss

---


### Default Setting


#### Cisco Catalyst 2960/3560

- SPEED = AUTO [Auto-negotiation]
- DUPLEX = AUTO [Auto-negotiation]

#### 10/100/1000 ports (Copper Ethernet Ports)

( As opposed to Fiber-Optic or Fixed-Speed ports or Higher-Speed ports )

- 10/100 Mbps = half or full duplex mode
- 1000 Mbps [1 Gbps] = only full duplex mode


#### Fiber-optic ports (ex. 1000BASE-SX)

- only one preset speed
- always full-duplex

---

### Best Practices for Duplex and Speed setting

- Manually configure speed/duplex for:
  - Known and stable network devices
  - Critical devices (requiring high performance)







---

### DUPLEX and SPEED Command

Manually configure switch ports with specific **duplex** and **speed** settings

```aiignore
S1(config)# interface FastEthernet 0/1
S1(config-if)# duplex full
S1(config-if)# speed 1000        [Mbps]
S1# copy running-config startup-config
```

---


### Troubleshooting duplex/speed


Check duplex and speed settings (on both ends)

```aiignore
show interfaces status
show interfaces GigabitEthernet0/1
```


---

## Auto-MDIX (Automatic Medium-Dependent Interface Crossover) Feature








