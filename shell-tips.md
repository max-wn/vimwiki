## shell tips

### beep

#### links
https://linuxconfig.org/turn-off-beep-bell-on-linux-terminal
https://wiki.archlinux.org/title/PC_speaker

#### Console

You can add this command in `/etc/profile` or a dedicated file like
`/etc/profile.d/disable-beep.sh` as follows
```
setterm -blength 0
```

Another way is to uncomment or add this line in `/etc/inputrc` or `~/.inputrc`
```
set bell-style none
```

---

[[/index|Get Back To Index]]
