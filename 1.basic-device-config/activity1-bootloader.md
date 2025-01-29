
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

#### Prevent switch from loading the startup configuration

```aiignore
switch: confreg 0x2142
```

#### (Alt) Prevent startup configuration from loading by changing name
```
switch: dir flash:
Directory of flash:/

2    -rwx  2664051   <date>               c2950-i6q4l2-mz.121-11.EA1.bin
3    -rwx  1460      <date>               config.text
4    -rwx  5         <date>               private-config.text
7    drwx  704       <date>               html
19   -rwx  109       <date>               info
20   -rwx  109       <date>               info.ver

3780096 bytes available (3961344 bytes used)
switch: rename flash:config.text flash:config.text.old
switch: dir flash:
Directory of flash:/

2    -rwx  2664051   <date>               c2950-i6q4l2-mz.121-11.EA1.bin
3    -rwx  1460      <date>               config.text.old
4    -rwx  5         <date>               private-config.text
7    drwx  704       <date>               html
19   -rwx  109       <date>               info
20   -rwx  109       <date>               info.ver

3780096 bytes available (3961344 bytes used)

switch: boot
```
```aiignore
Switch#rename flash:config.text.old flash:config.text
Switch#reload
```


