## veracrypt

### usage of veracrypt via cryptsetup

```sh
sudo cryptsetup --type tcrypt open path/to/container Backup  # open veracrypt container and named it 'Backup'
sudo mount /dev/mapper/Backup /mnt/usbstick/                 # mount it
sudo umount /mnt/usbstick                                    # unmount
sudo cryptsetup close Backup                                 # close veracrypt container
```

---

[[/index|Get Back To Index]]
