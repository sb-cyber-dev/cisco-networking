# Chapter 1: Basic Device Configuration

---

## Concepts
- Switch Boot Sequence

---

## Switch Basic BOOT Sequence

When a Cisco device is powered on, it goes through these 5 steps:

### Step 1

Switch loads POST (Power-On Self-Test), stored in ROM. 
- Tests CPU, DRAM, and flash file system


### Step 2

Switch loads boot loader software, stored in ROM.


### Step 3

Boot loader performs low-level CPU initialization


### Step 4

Boot loader initializes flash file system


### Step 5

Boot loader locates and loads default IOS os software image into memory, handing off control


---


## Boot system command

Command is used to set BOOT env var to specify which IOS image the device should load upon startup


```
S1(config)# boot system <filepath>
```


---


## Switch LED Indicators

- SYST (power,functioning properly)
- RPS/Redundant Power System (on, connected, available, functioning)
- STAT/Port (linked, port up, functioning, blocked)
- DUPLX/port duplex mode (full/half)
- SPEED (10Mbps, 100Mbps, 1000Mbps)
- PoE/Power over Ethernet (supported, mode selected)

---


## Recover from System Crash

- Access boot loader through console serial connection
- run 'flash_init' to initialize flash file system
- Make updates as necessary
- run 'boot' to load IOS

---


## Switch Management Access

Requirements to prepare switch for remote management access:
- Have a SVI (Switch Virtual Interface) configured with
  - IPv4 address and subnet mask
  - OR IPv6 address and prefix length
- Configured with a default gateway


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












