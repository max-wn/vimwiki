## shell tips

### beep

#### links

1. https://linuxconfig.org/turn-off-beep-bell-on-linux-terminal
2. https://wiki.archlinux.org/title/PC_speaker

#### Console

You can add this command in `/etc/profile` or a dedicated file like
`/etc/profile.d/disable-beep.sh` as follows:

```sh
setterm -blength 0
```

Another way is to uncomment or add this line in `/etc/inputrc` or `~/.inputrc`:

```sh
set bell-style none
```

---

[[/index|Get Back To Index]]
