## this is pacman warnings

1. ==> WARNING: Possibly missing firmware for module: 'xhci_pci'
https://aicsx.github.io/ax/blog/2022/01/07/Possibly-missing-firmware-for-module.html


2. ==> WARNING: consolefont: no font found in configuration

https://wiki.archlinux.org/title/Linux_console/Keyboard_configuration
https://aicsx.github.io/ax/blog/2022/01/08/consolefont-no-font-found-in-configuration.html

```bash
# check settings
sudo showconsolefont
cat /etc/vconsole.conf
sudo localectl status
# set VC keymap to 'us'
sudo localectl set-keymap --no-convert us
# open
sudo nvim /etc/vconsole.conf
# and wright there
FONT=Lat2-Terminus16
# final step: rerun kernel imaging (option '-p' calls a default preset to be used for building the kernel image. If you have other needs read the documentation about mkinitcpio.
sudo mkinitcpio -P
```
SOLVED

3. ==> WARNING: Possibly missing firmware for module: 'ast'
4. ==> WARNING: Possibly missing firmware for module: 'qed'
5. ==> WARNING: Possibly missing firmware for module: 'bfa'
6. ==> WARNING: Possibly missing firmware for module: 'qla2xxx'
7. ==> WARNING: Possibly missing firmware for module: 'wd719x'
8. ==> WARNING: Possibly missing firmware for module: 'qla1280'
9. ==> WARNING: Possibly missing firmware for module: 'aic94xx'


---

[[/index|Get Back To Index]]
