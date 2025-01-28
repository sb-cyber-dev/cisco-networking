
# Activity 1: Bootloader

-----

## Interrupt the bootup process

Interrup the bootup process to enter the bootloader

```aiignore
C2950 Boot Loader (C2950-HBOOT-M) Version 12.1(11r)EA1, RELEASE SOFTWARE (fc1)
Compiled Mon 22-Jul-02 17:18 by antonino
WS-C2950-24 starting...
Base ethernet MAC Address: 00:12:34:56:78:99
Xmodem file system is available.

The system has been interrupted prior to initializing the
flash filesystem.  The following commands will initialize
the flash filesystem, and finish loading the operating
system software:

    flash_init
    load_helper
    boot

switch:
```

---

## Initialize Flash Filesystem

```aiignore
switch: flash_init

Initializing Flash...
flashfs[0]: 16 files, 2 directories
flashfs[0]: 0 orphaned files, 0 orphaned directories
flashfs[0]: Total bytes: 7741440
flashfs[0]: Bytes used: 3961344
flashfs[0]: Bytes available: 3780096
flashfs[0]: flashfs fsck took 6 seconds.
...done initializing flash.
Boot Sector Filesystem (bs:) installed, fsid: 3
Parameter Block Filesystem (pb:) installed, fsid: 4
```
---

## Bypass Startup Configuration



