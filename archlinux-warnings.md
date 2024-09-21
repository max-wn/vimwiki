## this is pacman warnings

1.
==> WARNING: Possibly missing firmware for module: 'aic94xx'
==> WARNING: Possibly missing firmware for module: 'wd719x'
==> WARNING: Possibly missing firmware for module: 'xhci_pci'
==> WARNING: Possibly missing firmware for module: 'ast'
==> WARNING: Possibly missing firmware for module: 'qed'
==> WARNING: Possibly missing firmware for module: 'bfa'
==> WARNING: Possibly missing firmware for module: 'qla2xxx'
==> WARNING: Possibly missing firmware for module: 'qla1280'

https://aicsx.github.io/ax/blog/2022/01/07/Possibly-missing-firmware-for-module.html

https://wiki.archlinux.org/title/Mkinitcpio

[001]: https://aur.archlinux.org/packages/mkinitcpio-firmware "mkinitcpio-firmware from AUR"

If you want to suppress the warnings, you can install the missing firmware. The meta-package [mkinitcpio-firmware][001] in `AUR` contains most optional firmwares. Alternatively, manually install the needed packages (see above link). Or just ignore these warnings.

2.
==> WARNING: consolefont: no font found in configuration

https://wiki.archlinux.org/title/Linux_console#Fonts
https://wiki.archlinux.org/title/Linux_console/Keyboard_configuration
https://aicsx.github.io/ax/blog/2022/01/08/consolefont-no-font-found-in-configuration.html
https://wiki.archlinux.org/title/Installation_guide

TODO maybe use terminus with Cyrilic?
https://archlinux.org/packages/extra/any/terminus-font/

```bash
# default system consile fonts are here
ls -lah /usr/share/kbd/consolefonts/
# use Terminus font for console, finde via
ls -lah /usr/share/kbd/consolefonts/ | grep Terminus
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



---

[[/index|Get Back To Index]]
