## Operations with USB
### Links
https://wiki.archlinux.org/title/File_systems  # file systems
https://wiki.archlinux.org/title/Badblocks#  # badblocks is a program to test storage devices for bad blocks
https://wiki.archlinux.org/title/USB_storage_devices  # This document describes how to use the popular USB memory sticks with Linux.

### Create filesystems

find badblocks (execute as sudo)
`badblocks -wsv /dev/sda2`
Options:
`-w` do a destructive write test
`-s` show progress
`-v` be "verbose" and output bad sectors detected to stdout

`mkfs.ext4 -c -L /dev/sda2`
`-c` Check the device for bad blocks before creating the file system. If this option is specified twice `cc`, then a slower read-write test is used instead of a fast read-only test.
`-L` Specifies the volume label to be associated with the exFAT filesystem.

`mkfs.exfat -L FLASH-EXFAT /dev/sda2`
`-L` Specifies the volume label "FLASH-EXFAT" to be associated with the exFAT filesystem.

`mkfs.btrfs -L FLASH-BTRFS /dev/sda2`
`-L` Specifies the volume label "FLASH-BTRFS" to be associated with the exFAT filesystem.

### Mount USB

Create directory for USB
```bash
mkdir /mnt/usbstick
```

Give a group to usbstick directory
```bash
sudo chown root:wheel /mnt/usbstick
```

Give a right to usbstick directory
```bash
sudo chmod g+w /mnt/usbstick
```

Plug USB devise

Find all disks
```bash
lsblk     # show short list
# or
lsblk -f  # show long list
```

OR find all mounted disks
```bash
blkid -o list
```

OR finde a name of USB device (for example it is sda)
```bash
sudo fdisk -l
```

OR see what is mounted
```bash
blkid -o list -c /dev/null
```

Mount USB
```bash
sudo mount /dev/sda /mnt/usbstick
# or
sudo mount -o gid=users,fmask=113,dmask=002 /dev/sda /mnt/usbstick  # if you want non-root users to be able to write to the USB stick
```

Unmount USB
```bash
sudo umount /mnt/usbstick
```

If you have problems with mounting USB, in `/dev` you do indeed see the hard drives as `/sda` and `/sdb` etc. If you go to `/dev/disk/by-id/` you will see a different list by unique device names. When you mount it, use that name just as you would use `/sda`. The advantage of using unique device names instead of names like `/sda`, is the device is mounted the the same way each time regardless of boot order or thumb drives left in while rebooting which can change the usb drive order, etc.

Example of mount command:
```bash
mount /dev/disk/by-id/usb-COWON_J3_0221001E55027D511123241626337D51-0:0 /mnt/usbstick
```

### Encrypt USB
#### links
https://wiki.archlinux.org/title/Cryptsetup
https://videos.lukesmith.xyz/w/qxMiq53aTieALZwumuxG6G
https://wiki.archlinux.org/title/Btrfs

#### Commands
execute as sudo
```bash
cryptsetup luksFormat /dev/sda2        # create a new LUKS container on sda2
cryptsetup open /dev/sda2 drive        # create / open directory with name "drive"
mkfs.btrfs /dev/mapper/drive           # create file system. use "mapper" instead of "sda"! execut only once at startup
mount /dev/mapper/drive /mnt/usbstick  # mout USB
umount /dev/usbstick                   # unmount USB
cryptsetup close drive                 # close secret drive
```

---

[[/index|Get Back To Index]]
