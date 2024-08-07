## Operations with USB
### Links
#### www
https://wiki.archlinux.org/title/File_systems  # file systems
https://wiki.archlinux.org/title/Badblocks#  # badblocks is a program to test storage devices for bad blocks
https://wiki.archlinux.org/title/USB_storage_devices  # This document describes how to use the popular USB memory sticks with Linux.
https://losst.pro/kak-posmotret-usb-ustrojstva-linux
https://archlinux.org/packages/core/x86_64/usbutils/
https://man.archlinux.org/man/lsusb.8.en

#### mount cell phone
[simple mtpfs](simple-mtpfs.md) -- how to mount android

#### disks check list
[disks](disks.md) -- check your disks :)

### Create filesystems
find badblocks (execute as sudo)
`badblocks -wsv /dev/sda2`
Options:
`-w` do a destructive write test
`-s` show progress
`-v` be "verbose" and output bad sectors detected to stdout

`mkfs.ext4 -c -L FLASH-EXT4 /dev/sda2`
`-c` Check the device for bad blocks before creating the file system. If this option is specified twice `cc`, then a slower read-write test is used instead of a fast read-only test.
`-L` Specifies the volume label to be associated with the filesystem.

`mkfs.exfat -L FLASH-EXFAT /dev/sda2`
`-L` Specifies the volume label "FLASH-EXFAT" to be associated with the filesystem.

`mkfs.btrfs -L FLASH-BTRFS /dev/sda2`
`-L` Specifies the volume label "FLASH-BTRFS" to be associated with the filesystem.

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
# or
lsusb     # show usb devises
# or
ls -lah /dev/disk/by-id/usb*  # show usb by id
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

To chnge owership:
```bash
chown -R $USER ~/path/to/file
```

### Encrypt USB
#### links
https://wiki.archlinux.org/title/Cryptsetup
https://videos.lukesmith.xyz/w/qxMiq53aTieALZwumuxG6G
https://wiki.archlinux.org/title/Btrfs
https://wiki.archlinux.org/title/Dm-crypt/Device_encryption#Cryptsetup_usage

#### Commands

```bash
sudo cryptsetup luksFormat /dev/sda2        # create a new LUKS container on sda2
sudo cryptsetup open /dev/sda2 drive        # create / open directory with name "drive"
sudo mkfs.btrfs /dev/mapper/drive           # create file system. use "mapper" instead of "sda"! execut only once at startup
sudo mount /dev/mapper/drive /mnt/usbstick  # mout USB
sudo umount /mnt/usbstick                   # unmount USB
sudo cryptsetup close drive                 # close secret drive
```

!!! if you will hav errors with btrfs try to wipe dada on volume:
See link, chapter "Previously used partitions"
https://man.archlinux.org/man/cryptsetup.8

```bash
sudo wipefs --all --no-act /dev/sda*  # dry run
sudo wipefs --all /dev/sda*           # wipe recursively
```

### usage of veracrypt via cryptsetup
https://wiki.archlinux.org/title/VeraCrypt

```bash
sudo cryptsetup --type tcrypt open path/to/container Backup  # open veracrypt container and named it 'Backup'
sudo mount /dev/mapper/Backup /mnt/usbstick/  # mount it
sudo umount /mnt/usbstick  # unmount
sudo cryptsetup close Backup  # close veracrypt container
```

### misc
If you need to know which type of FAT file system a partition uses, use the file command:

```bash
sudo file -s /dev/partition
```

### TRIM
according to archwiki:
https://wiki.archlinux.org/title/TRIM

Periodic TRIM
The `util-linux` package provides `fstrim.service` and `fstrim.timer` `systemd` unit files. `Enabling` the timer will activate the service weekly. The service executes `fstrim(8)` on all mounted filesystems on devices that support the discard operation.

The timer relies on the timestamp of `/var/lib/systemd/timers/stamp-fstrim.timer` (which it will create upon first invocation) to know whether a week has elapsed since it last ran. Therefore there is no need to worry about too frequent invocations, in an anacron-like fashion.

To query the units activity and status, see `journalctl`.
https://wiki.archlinux.org/title/Journalctl

To change the periodicity of the timer or the command run, `edit` the provided unit files.
https://wiki.archlinux.org/title/Edit

```bash
lsblk --discard  # verify TRIM support
sudo systemctl enable fstrim.timer   # enable periodic TRIM
# or
sudo systemctl disable fstrim.timer  # disable periodic TRIM
# or manually fstrim (discard unused blocks on a mounted filesystem) once
sudo fstrim -v /path/to/mountpoint
# or
sudo fstrim -av
	-a  # trim all mounted filesystems on devices that support the discard operation.
	-v  # verbose
	-n  # dy-run
sudo journalctl --grep=PATTERN  # print log entries from the systemd journal where flags could be:
	-b  # show all messages from this boot
	-f  # show only the most recent journal entries, and continuously print new entries as they are appended to the journal
```

---

[[/index|Get Back To Index]]
