## Archiving and compression

GNU compression utility

gzip
bzip2

rar --> Both the format and the rar utility are proprietary.

### links
https://wiki.archlinux.org/title/Tar
https://archlinux.org/packages/core/x86_64/gzip/
https://wiki.archlinux.org/title/Gzip


### basis

in MacOS we have preinstalled `Archive Utility` which can work with `zip` files.

path for it:
```
/System/Library/CoreServices/Applications/Archive\ Utility.app/
```

other utilities for MacOS
https://formulae.brew.sh/formula/zip#default  # I use preinstalled utility

https://formulae.brew.sh/cask/rar#default --> installed
https://manned.org/rar --> manual for above rar utility

examples:

- Archive 1 or more files:
`rar a path/to/archive_name.rar path/to/file1 path/to/file2 path/to/file3`

- Unarchive 1 archive:
`rar x path/to/archive_name.rar`


---

[[/index|Get Back To Index]]
