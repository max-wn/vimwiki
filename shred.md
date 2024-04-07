:hello_world:

shredding a 'file'

```bash
shred [OPTION] filename
```

shredding a 'disk'

```bash
shred -vfz [/file/system/path]
```

According to the man page, some of the [OPTIONS] you can use with shred are:

    -n, --iterations=N
    Instead of the default (3) times, overwrite the data N times.
    -z, --zero
    Add a final overwrite with zeros to hide shredding.
    -f, --force
    Force the permissions to allow writing if necessary.
    -v, --verbose
    Show progress in detail.
    -u, --remove
    Truncate and remove file after overwriting.


we can overwrite, hide shredding, and remove the file in a single command

```bash
shred -vzu -n5 poem.txt
```

Where,

    -v stands for verbose and gives detailed output.
    -z replaces the final pass with zeros to hide shredding.
    -u removes the file after shredding. We don't need to remove file
    afterwards using rm with this flag.
    -n changes the number of passes. We have set it to 5.

You can use shred to wipe your drive

```bash
sudo shred -vfz /dev/sde
```

Replace `/dev/sde` with your mount point

Where,

    -v gives detailed output.
    -f forces the write permissions if missing.
    -z writes zeros in the final pass.

You can also use shred on RAID partitions.

```bash
shred -vfz -n 10 /dev/md1
```

There are certain cases when shred is not effective. According to the man
pages, below are some of the cases:

* Log-structured or journaled file systems, such as those supplied with AIX
  and Solaris (and JFS, ReiserFS, XFS, Ext3, and so on)
* File systems that write redundant data, such as RAID-based file systems.
* File systems that make snapshots. Examples include: Network Appliance's NFS
  server.
* File systems that support caching in temporary locations, such as NFS
  version 3 clients.
* Compressed file systems.

---

[[/index|Get Back To Index]]
