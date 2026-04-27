## clamav

### links

1. https://wiki.archlinux.org/title/ClamAV
2. https://formulae.brew.sh/formula/clamav#default
3. https://github.com/Cisco-Talos/clamav
4. https://docs.clamav.net://docs.clamav.net/
5. https://www.clamav.net/
6. Самый лучший антивирус для GNU/Linux, Android, iOS, Windows: https://www.youtube.com/watch?v=GU0aDoOhYX0
7. ClamAV: https://t.me/open_source_friend/568
8. ClamAV документация: https://docs.clamav.net/
9. ClamAV скрипт для автоматического сканирования и отправки уведомлений: https://ixnfo.com/en/clamav-script-for-automatic-scanning-and-email-notifications.html

### Базы ClamAV

держит в:

```sh
# linux
/var/lib/clamav/

# macos
/usr/local/var/lib/clamav/
```
Они лежат там просто как файлы, можно копировать просто поверх старых.

Если ты запускаешь ClamAV вручную для сканирования, после обновления баз
ничего делать не нужно — новый экземпляр сканера откроет и прочитает новые
файлы. Если используешь `clamd`, то либо сервису нужно дать команду
перезагрузить базы, например: `systemctl reload clamav-daemon`, либо послать
`clamd` сигнал `SIGUSR2`.

It is not possible to update bases in RUSS due to sunctions. Just download
bases manualy via VPN from:

1. https://database.clamav.net/main.cvd
2. https://database.clamav.net/bytecode.cvd
3. https://database.clamav.net/daily.cvd


on Mac with brew installed clamav bases stored in:
```sh
/usr/local/Cellar/clamav/0.105.1/share/clamav
```

### tips

```sh
clamscan -vi --bell ~/Downloads
```

***

## chkrootkit

1. http://www.chkrootkit.org/
2. https://aur.archlinux.org/packages?O=0&K=chkrootkit
3. https://formulae.brew.sh/formula/chkrootkit#default
4. https://github.com/Magentron/chkrootkit

***

## rkhunter

1. http://rkhunter.sourceforge.net/

### rkhunter мануал:

1. https://www.tecmint.com/install-rootkit-hunter-scan-for-rootkits-backdoors-in-linux/
2. https://wiki.archlinux.org/title/Rkhunter
3. https://formulae.brew.sh/formula/rkhunter#default

***

Mobile Verification Toolkit: https://t.me/open_source_friend/1061

---

[[/index|Get Back To Index]]
