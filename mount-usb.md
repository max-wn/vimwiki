## MOUNT USB

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
lsblk
```

Find all mounted disks
```bash
blkid -o list
```

Finde a name of USB device (for example it is sda)
```bash
sudo fdisk -l
```

See what is mounted
```bash
blkid -o list -c /dev/null
```

Mount USB
```bash
sudo mount /dev/sda /mnt/usbstick
```

Unmount USB
```bash
sudo umount /mnt/usbstick
```
