## various temporary stuff

START KM 01.12.2009
START YM 19.10.2015



### usb and disks

`lsblk -f` show with type, UUID and spaces
`lsblk` short list

In `/dev` you do indeed see the hard drives as `/sda` and `/sdb` etc. If you go to `/dev/disk/by-id/` you will see a different list by unique device names.

example
```bash
mount /dev/disk/by-id/usb-id-name /mnt/usbstick
```

for badblicks see instructions in : https://wiki.archlinux.org/title/Badblocks
example

checking a disk for bad blocks before formatting it
Use `-cc` to do a read-write bad block test
```bash
mkfs.ext4 -c /dev/device
```

Read-write test (warning: destructive)
```bash
badblocks -wsv /dev/device
```
Options:
    `-w` do a destructive write test
    `-s` show progress
    `-v` be "verbose" and output bad sectors detected to stdout

---

[[/index|Get Back To Index]]
