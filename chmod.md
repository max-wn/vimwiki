## chmod examples

Standart permission

```sh
chmod 755 <dir>
```

Как можно сделать рекусивный chmod в каталоге с большой вложенностью чтобы для
папок ставились права 700, а для для файлов 600?

```sh
find /path -type d -exec chmod 700 {} \;
find /path -type f -exec chmod 600 {} \;
```

example
```sh
find ./ -type f -exec chmod 664 {} \;
# 664 means rw-rw-r--
# './' means current dir
```

The configuration directory `~/.ssh`, its contents should be accessible only by
the user (check this on both the client and the server), and the user's home
directory should only be writable by the user:

```sh
chmod go-w ~
chmod 700 ~/.ssh
chmod 600 ~/.ssh/*
chown -R $USER ~/.ssh
```

On the server, make the `authorized_keys` file read-only for the user and deny
all other permissions:

```sh
$ chmod 400 ~/.ssh/authorized_keys
```

GnuPG Home directory

The GnuPG home directory is where the GnuPG suite stores its keyrings and
private keys, and reads configurations from. By default, the path used is
`~/.gnupg`. By default, the home directory has its permissions set to `700` and
the files it contains have their permissions set to `600`. Only the owner of the
directory has permission to read, write, and access the files. This is for
security purposes and should not be changed. In case this directory or any
file inside it does not follow this security measure, you will get warnings
about unsafe file and home directory permissions.

---

[[/index|Get Back To Index]]
