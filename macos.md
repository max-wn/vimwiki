## MacOS

https://support.apple.com/ru-ru/HT211683

https://support.apple.com/ru-ru/HT201300

https://support.apple.com/kb/SP653?locale=ru_RU

### linux on mac

https://www.youtube.com/watch?v=x0Qmaa38UM8

### burn ISO on mac

https://github.com/balena-io/etcher
https://www.balena.io/etcher


### format flash

```bash
diskutil list  # return names of disks (now flash is "disk2")
```

```bash
sudo diskutil eraseDisk exfat FLASH /dev/disk2  # exfat --> new file system on flash (as example) FLASH --> new volume name
```

### to write iso on flash

```bash
sudo diskutil umountDisk /dev/disk2  # unmaunt flash before writing

# example how to write Ddebian iso
sudo dd if=/Users/name_of_user/Downloads/debian-live-10.2.0-amd64-xfce.iso of=/dev/rdisk2 bs=1m
```

### to write macОС on flash

you should format flash to _Mac OS Extended_ and name it as `MyVolume` -->
important!

write macos on flash

```bash
sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume --applicationpath /Applications/Install\ macOS\ Mojave.app`
```

### how to find apps for deleting

```bash
find . -name "*vlc*" && sudo find /Library -name "*vlc*"
```

### homebrew

```bash
brew update    # First update the formulae and Homebrew itself
brew outdated  # You can now find out what is outdated with
brew upgrade   # Upgrade everything with
brew doctor    # inspect homebrew
```

---

[[/index|Get Back To Index]]
