## pacman cheatsheet

### Common commands

| Command                 | Description                       |
| ----------------------- | --------------------------------- |
| `pacman -Syu <pkg>`     | Install (and update package list) |
| `pacman -S <pkg>`       | Install only                      |
| `pacman -Rs <pkg>`      | Uninstall                         |
| `pacman -Ss <keywords>` | Search in repo                    |
| `pacman -Qs <keywords>` | Search on PC                      |
| `pacman -Syu`           | Upgrade everything                |

### Query

| Command              | Description                            |
| -------------------- | -------------------------------------- |
| `pacman -Qe`         | List explictly-installed packages      |
| ---                  | ---                                    |
| `pacman -Ql <pkg>`   | What files does this package have?     |
| `pacman -Qii <pkg>`  | List information on package            |
| ---                  | ---                                    |
| `pacman -Qo <file>`  | Who owns this file?                    |
| ---                  | ---                                    |
| `pacman -Qs <query>` | Search installed packages for keywords |

### Orphans

| Command                       | Description                 |
| ----------------------------- | --------------------------- |
| `pacman -Qdt`                 | List unneeded packages      |
| `pacman -Rns $(pacman -Qdtq)` | Uninstall unneeded packages |

Avoid orphans by using `pacman -Rsc` to remove packages, which will remove unneeded dependencies.

### Other

| Command            | Description                |
| ------------------ | -------------------------- |
| `pactree <pkg>`    | What does _pkg_ depend on? |
| `pactree -r <pkg>` | What depends on _pkg_?     |

### Some explanations

Uncomment Color and VerbosePkgLists lines in file:
```bash
vim /etc/pacman.conf
```

This will refresh your databases even if they are already up to date. I have found this to rarely be necessary, even when updating my mirrorlist or adding custom repos. Could be used when your database was corrupted, and that happens exactly very rarely in Arch.
```bash
sudo pacman -Syyu
```

### References

* [Pacman tips and tricks](https://wiki.archlinux.org/index.php/Pacman/Tips_and_tricks) _(wiki.archlinux.org)_
