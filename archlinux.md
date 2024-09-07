# Arch Linux installation guide

## links
https://wiki.archlinux.org/title/Installation_guide#Post-installation
https://wiki.archlinux.org/title/General_recommendations


## download arch iso

Download latest Arch iso file and verify signature. All instructions awaliable
in [wiki](https://wiki.archlinux.org/index.php/Installation_guide "wiki
guide")

**for example on macOS:**
* download iso from [wiki](https://www.archlinux.org/download/ "wiki
   downloads")
* `cd` to Download directory
* get the checksum:

```bash
md5 /path/to/archlinux-version-x86_64.iso
# or via gnupg
gpg --keyserver-options auto-key-retrieve --verify /path/to/archlinux-version-x86_64.iso.sig
```

* the command return md5 checksum and you should compare it with md5 checksum
   mentioned on [site](https://www.archlinux.org/download/ "wiki downloads")
* Write Arch to USB.

## usb and iso preparation

Find name of USB (for example it is `sdaX`)

```bash
lsblk  # for GNU Linux
# or
diskutil list  # for macos
```

Unmount USB

```bash
sudo umount /dev/sda
# or
diskutil unmountDisk /dev/sdaX
```

Format USB

```bash
sudo mkfs -t ext4 -L FLASH /dev/sdaX
```

Now copy the ISO image file to the device.

```bash
# for macos
sudo dd if=path/to/archlinux-version-x86_64.iso of=/dev/rdiskX bs=1m
```

## arch installation

To verify the boot mode, list the efivars directory:

```bash
ls /sys/firmware/efi/efivars
```

If the command shows the directory without error, then the system is booted
in UEFI mode. If the directory does not exist, the system may be booted in
BIOS

### Check internet connection

check ip and ping (if no ip and ping use wifi instructions):

```bash
ip link  #Ensure your network interface is listed and enabled
```

Set rfkill off

```bash
rfkill unblock wifi
```

Set device up

```bash
ip link set wlan0 up
```

#### Connect to wifi via `iwctl`

[see link](https://wiki.archlinux.org/title/Iwctl "iwctl")

To get an interactive prompt do:

```bash
iwctl
```

To list all available commands:

```bash
[iwd]# help
```

Connect to a network

First, if you do not know your wireless device name, list all Wi-Fi devices:

```bash
[iwd]# device list
```
Find your device name (for example it is `wlan0`)

Then, to scan for networks:

```bash
[iwd]# station wlan0 scan
```
Above command will not output anything

You can then list all available networks:

```bash
[iwd]# station wlan0 get-networks
```

Finally, to connect to a network:

```bash
[iwd]# station wlan0 connect SSID
```

If a passphrase is required, you will be prompted to enter it. Alternatively,
you can supply it as a command line argument:

```bash
iwctl --passphrase your-passphrase station device connect SSID
```

Check connection

```bash
ping -c 3 archlinux.org
```

### update system clock

```bash
timedatectl set-ntp true
timedatectl status  # to check the service status
```

### Check our disks (for example it is 'nvme0n1')

```bash
lsblk
# or
fdisk -l
```

### Disk partition

```bash
fdisk /dev/nvme0n1
```

interface: `m` - help, `p` - disks, `d` - delete disk, `n` - new partition
hint `n` for new partition, always chose primary, start sector defoult, end
sector put the size as mentioned below:

1. primary (boot): `+512M`
2. primary (swap): `+16G`
3. primary (root): `+50G`
4. primary (home): hit `Enter` for all the rest space

hit `w` for write these partitions

NOTE: swap partition should be 1/2 of your RAM but not more than 8G, maximum 16G. Big swap is a waste of disk space...

### Set file system as follows:

`-c` --> Check the device for bad blocks before creating the file system. If this option is specified twice, then a slower read-write test is used instead of a fast read-only test.

for boot

```bash
mkfs.ext4 -c /dev/nvme0n1p1
```

for root

```bash
mkfs.ext4 -c /dev/nvme0n1p3
```

for home

```bash
mkfs.ext4 -c /dev/nvme0n1p4
```

for swap

```bash
mkswap -c /dev/nvme0n1p2
```

swap activation

```bash
swapon /dev/nvme0n1p2
```

### Mount root

```bash
mount /dev/nvme01p3 /mnt
```

### Create home directory

```bash
mkdir /mnt/home
```

### Create boot directory

```bash
mkdir /mnt/boot
```

### Mount boot

```bash
mount /dev/nvme01p1 /mnt/boot
```

### Mount home

```bash
mount /dev/nvme01p4 /mnt/home
```

### Install arch

```bash
pacstrap /mnt base base-devel linux linux-firmware linux-headers vim
inetutils netctl dhcpcd man-pages man-db
```

### Generate fstab

generate fstab, force fstab to use UUID and write fstab to file

```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

### Transfer from USB linux to Computer linux

```bash
arch-chroot /mnt
```

### Set time zone

```bash
ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime
```

### Generate time

```bash
hwclock --systohc
```

### Generate local

uncomment langusges in:

```bash
vim /etc/locale.gen
en_US.UTF-8 UTF-8
```

enable local

```bash
locale-gen
```

Set (wright in file) language in:

```bash
vim /etc/locale.conf
LANG=en_US.UTF-8
```
### Add hosts

Wright your hostname in file:

```bash
vim /etc/hostname
```

Add matching entries to hosts

```bash
vim /etc/hosts
```

put the followimg in file:

```bash
127.0.0.1   localhost
::1         localhost
127.0.1.1   <hostname>.localdomine <hostname>
```

### Set root password

```bash
passwd
> yourpassword
```
### set color in pacman

```bash
vim /etc/pacman.conf
# uncoment these lines:
#Color
#VerbosePkgLists
```

### Set grub

```bash
pacman -S grub                              # install grub
grub-install --target=i386-pc /dev/nvme0n1  # Enable grub
grub-mkconfig -o /boot/grub/grub.cfg        # Create config file for grub
```

### Set Network Manager

```bash
pacman -S networkmanager         # install NM
systemctl enable NetworkManager  # enable Network Manager
# only after below mentioned reboot
nmcli connection show            # show connections
nmcli device wifi list           # show wifi networks
nmcli device wifi connect <SSID or BSSID> password <yourpassword>  # Connect to a wifi network
```

More info see in [wiki](https://wiki.archlinux.org/index.php/NetworkManager "NM archwiki")

### Exit from root and unmount USB

```bash
exit
umount -R /mnt
```

### Reboot

```bash
reboot
```

### Check internet cinnection.

```bash
ping -c 3 archlinux.org
# If not, execute:
nmcli device wifi connect <SSID or BSSID> password <yourpassword>  # Connect to a wifi network
# or make NM tuning for wifi (see below)
```

### Correct mirror list via Reflector

```bash
pacman -S reflector                    # install reflector
cat /etc/pacman.d/mirrorlist           # check mirrors
vim /etc/xdg/reflector/reflector.conf  # adjust config
systemctl start reflector.service      # start reflector
cat /etc/pacman.d/mirrorlist           # check mirrors
```

### Update & upgrade system

```bash
sudo pacman -Syu
```

### Users and groups.

Add new user (-m means home dir will be created)

```bash
useradd -m <nameofuser>
```

Add password for new user

```bash
passwd <nameofuser>
> password
```

Add user to groups

```bash
usermod -aG wheel <nameofuser>
#audio,video,optical,storage --> ???
```

Check user's groups

```bash
groups <nameofuser>
```

Open sudoers file `/etc/sudoers` and uncomment wheel group line `# %wheel ALL=(ALL) ALL`

```bash
vim /etc/sudoers
```

Logout from root user and lgon as <nameofuser>
`exit`

### Install xorg and video drivers

```bash
sudo pacman -S xorg xorg-xinit xterm
```

Copy `.xinitrc` to `home` directory, see instructions in [arch wiki](https://wiki.archlinux.org/title/Xinit)

```bash
cp /etc/X11/xinit/xinitrc /home/nils/.xinitrc
```

Check your video card (here I have nvidia and I will use proprietary driver)

```bash
lspci -k | grep -E "(VGA|3D)"
```

Uninstal conflict drivers. IMPORTANT!

```bash
sudo pacman -Rs xf86-video-amdgpu
sudo pacman -Rs xf86-video-nouveau
sudo pacman -Rs xf86-video-intel
```

Ceck if you have mesa (if not, install it)

```bash
sudo pacman -Qs mesa mesa-utils
```

Install nvidia packages

```bash
sudo pacman -S nvidia nvidia-utils
```

Check xorg

```bash
sudo startx
```

Exit from xorg

```bash
exit
```

### Install WM (qtile and additional packages for it)

```bash
sudo pacman -S qtile python-pip python-setuptools

# probably you will also need the following pakages: python-psutil
python-iwlib python-keyring python-dateutil python-pyxdg python-mpd2
```

Put the following line in `.xinitrc`

```
# comment lines from "twm..." to "exec xterm..." and put below:

exec qtile start
```

Start qtile from tty by command:

```bash
startx
```

show mod keys (work only if WM starts):

```bash
xmodmap -pm
```

### Install fonts

```bash
sudo pacman -S ttf-jetbrains-mono
```

probably plus `ttf-linux-libertine` or: `noto-fonts`

### Install additional important packages

```bash
sudo pacman -S alacritty git openssh gnupg pass rsync veracrypt stow firefox
mc xclip
```

packages description:

* alacritty  --> terminal emulator
* git        --> distributed version control system
* openssh    --> tool for remote login with the SSH protocol
* gnupg      --> complete and free implementation of the OpenPGP standard
* pass       --> password manager
* rsync      --> file copying tool for remote and local files
* veracrypt  --> disk encryption
* stow       --> Manage installation of multiple softwares in the same directory tree
* firefox    --> internet browser
* tldr       --> Command line client for tldr, a collection of simplified and community-driven man pages
* mc         --> file manager
* xclip      --> Command line interface to the X11 clipboard

### Set defolt programms

put in file `vim ~/.bash_profile`

```bash
export EDITOR="vim"
export BROWSER="firefox"
```

### Install audio packages

```bash
sudo pacman -S pulseaudio pulseaudio-alsa alsa-utils
```

package description:

* pulseaudio       --> A featureful, general-purpose sound server
* pulseaudio-alsa  --> ALSA Configuration for PulseAudio
* alsa-utils       --> Advanced Linux Sound Architecture - Utilities

Set up sound, instructions see in
[wiki](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture "alsamixer archwiki")

### Install video packages

```bash
sudo pacman -S mpv youtube-dl
```

packages description:

* mpv         --> video player
* youtube-dl  --> A command-line program to download videos from YouTube.com
  and a few more sites

---

### Install workflow packages

```bash
sudo pacman -S figlet mutt udisks2 pycharm-community-edition moc
htop calcurse sxiv zathura zathura-pdf-mupdf zathura-djvu
pacman-contrib github-cli newsboat perl-image-exiftool calibre ffmpeg krita
gimp pandoc texlive-most texlive-lang biber lynx urlscan
```

packages description:

* figlet                    --> display large letters out of text
* mutt                      --> email client
* udisks2                   --> to query and manipulate storage devices
* pycharm-community-edition --> python ide
* moc                       --> audio player
* htop                      --> interactive process viewer
* calcurse                  --> todo manager
* sxiv                      --> lightweight and scriptable image viewer
* zathura                   --> document viewer PDF, PS, DjVu
* zathura-pdf-mupdf         --> document viewer PDF, PS, DjVu
* zathura-djvu              --> document viewer PDF, PS, DjVu
* pacman-contrib            --> contributed scripts and tools for pacman systems
* github-cli                --> cli client gor github
* newsboat                  --> rss feed
* perl-image-exiftool       --> Reader and rewriter of EXIF informations that supports raw files
* calibre                   --> e-book management application
* ffmpeg                    --> Complete solution to record, convert and stream audio and video
* krita                     --> edit and paint images
* gimp                      --> GNU Image Manipulation Program
* pandoc                    --> Conversion between markup formats
* texlive-most              --> group contains most TeX Live packages
* texlive-lang              --> group contains packages providing character sets and features for languages with non-latin characters
* biber                     --> A Unicode-capable BibTeX replacement for biblatex users
* lynx                      --> A text browser for the World Wide Web
* urlscan                   --> Mutt and terminal url selector

### Turn off PC:

```bash
sudo shutdown -h now
```

---

## Misc

### Create RU keyboard layout

For using `Shift + Ctrl` for US-RU change:

```bash
localectl --no-convert set-x11-keymap us,ru "" "" grp:ctrl_shift_toggle
```

Restart xinit

### STEAM installation.

All instructions see in [wiki](https://wiki.archlinux.org/index.php/Steam "steam archwiki")

to enable multilib repository, uncomment the `[multilib]` section in
`/etc/pacman.conf` as follows:

```
[multilib]
Include = /etc/pacman.d/mirrorlist
```

install proprietary 32-bit version OpenGL graphics driver

```bash
sudo pacman -S lib32-nvidia-utils
```

Generated `en_US.UTF-8` locale, preventing invalid pointer error

The GUI heavily uses the Arial font. See Microsoft fonts. An alternative is to
use `ttf-liberation`

```bash
sudo pacman -S ttf-liberation
```

install `wqy-zenhei` to add support for Asian languages

```bash
sudo pacman -S wqy-zenhei
```

install steam

```bash
sudo pacman -S steam
```

### Emergency action:

`Ctrl + Alt + F2` or `F3` or `F4` etc --> Open new tty session

### УСТАНОВКА РУССКОГО ЯЗЫКА

#### var 1

Например, можно установить английскую и русскую раскладки, которые будут
переключаться по `ctrl+shift`:

```bash
localectl --no-convert set-x11-keymap us,ru "" "" grp:ctrl_shift_toggle
```
restart xinit

#### var 2
(RALT --> ENG, Shift + RALT --> RUS)

Check keyboard settigs on the your computer:

```bash
setxkbmap -layout us,ru -print
```

create file config:

```bash
touch ~/.config/xkb/config
```

Write the result in the file:

```bash
setxkbmap -layout us,ru -print > ~/.config/xkb/config
```

chenge string `xkb_symbols...` as folows:

```
xkb_symbols "my" {
include "pc+us+ru:2+inet(evdev)"
key <RALT> { [ ISO_First_Group, ISO_Last_Group ] };
};
```

Load config:

```bash
xkbcomp $HOME/.config/xkb/config $DISPLAY
```

source finde [here](https://m.habr.com/ru/post/486872/ "instructions")

---

### NM tuning for wifi

disable dhcpcd on ethernet

```bash
sudo systemctl disable dhcpcd@enp8s0.service
```

disable netctl on wifi

```bash
sudo systemctl disable netctl-auto@wlan0.service
```

enable NM

```bash
sudo systemctl enable NetworkManager.service
```

reboot

```bash
reboot
```
### System Time

https://wiki.archlinux.org/title/System_time#Time_zone

Troubleshooting

Clock shows a value that is neither UTC nor local time
This might be caused by a number of reasons. For example, if your hardware clock is running on local time, but timedatectl is set to assume it is in UTC, the result would be that your timezone's offset to UTC effectively gets applied twice, resulting in wrong values for your local time and UTC.

To force your clock to the correct time, and to also write the correct UTC to your hardware clock, follow these steps:

1. Setup [ntpd](https://wiki.archlinux.org/title/Ntpd) (enabling it as a service is not necessary).
2. Set your [time zone](https://wiki.archlinux.org/title/System_time#Time_zone) correctly.
3. Run `ntpd -qg` to manually synchronize your clock with the network, ignoring large deviations between local UTC and network UTC.
4. Run `hwclock --systohc` to write the current software UTC time to the hardware clock.

---

THE END
