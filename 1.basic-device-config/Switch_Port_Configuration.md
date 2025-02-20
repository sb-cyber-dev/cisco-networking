
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

- Enabled on an interface = configures connection appropriately (crossover/straight-through)
  - Either type of cable can be used to connect to other devices
  - (REQ) interface speed and duplex must be set to AUTO


```aiignore
S1(config-if)# mdix auto

show interfaces FastEthernet0/1 status

show controllers ethernet-controller fa0/1 phy | include MDIX
```



---

## Check Network Access Layer Status

```aiignore
S1# show interfaces fastEthernet 0/18
FastEthernet0/18 is up, line protocol is up (connected)
Hardware is Fast Ethernet, address is 0025.83e6.9092 (bia 0025.83e6.9092)MTU 1500 bytes, BW 100000 Kbit/sec, DLY 100 usec,
```

- (FastEthernet0/18 is up) = hardware layer, interface is receiving carrier detect signal.
- (line protocol is up) = data link layer and indicates whether data link layer protocol keepalives are being received.

### Troubleshoot

- Interface UP, line protocol DOWN = error or hardware problem
- Interface DOWN, line protocol DOWN = cable connection issue or other end is down, speed mismatch
- interface administratively DOWN = Has been manually disabled


### "show interfaces" command Error Fields

- Input Errors = Total # of errors, incl runts, giants, no buffer, frame, overrun, and ignred counts.
- Runts = Discarded frames because are smaller than minimum frame size for medium.
  - Usually caused by malfunctioning NIC or collisions
- Giants = Discarded frames because exceed max frame size for medium. 
- CRC = calculated checksum is not same as checksum received
  - Usually caused by media or cable error. Too much noise. 
- Output errors = Sum of all errors preventing final transmission of datagrams out of current interface
- Collisions = # of messages retransmitted because of Ethernet collision
  - Collisions are normal for half duplex
  - Should NEVER see collisions in full duplex
- Late Collisions = Collision after 512 bits of frame transmitted
  - excessive cable length
  - duplex mismatch




















