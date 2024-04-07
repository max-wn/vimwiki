## clamav

### links
https://wiki.archlinux.org/title/ClamAV
https://formulae.brew.sh/formula/clamav#default
https://github.com/Cisco-Talos/clamav
https://docs.clamav.net://docs.clamav.net/
https://www.clamav.net/

Самый лучший антивирус для GNU/Linux, Android, iOS, Windows

https://www.youtube.com/watch?v=GU0aDoOhYX0

ClamAV: https://t.me/open_source_friend/568

ClamAV документация: https://docs.clamav.net/

ClamAV скрипт для автоматического сканирования и отправки уведомлений:
https://ixnfo.com/en/clamav-script-for-automatic-scanning-and-email-notifications.html

### Базы ClamAV
держит в
```
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

https://database.clamav.net/main.cvd

https://database.clamav.net/bytecode.cvd

https://database.clamav.net/daily.cvd


on Mac with brew installed clamav bases stored in:
```
/usr/local/Cellar/clamav/0.105.1/share/clamav
```

### tips
```
clamscan -vi --bell ~/Downloads
```

***

## chkrootkit
http://www.chkrootkit.org/
https://aur.archlinux.org/packages?O=0&K=chkrootkit
https://formulae.brew.sh/formula/chkrootkit#default
https://github.com/Magentron/chkrootkit


***

## rkhunter
http://rkhunter.sourceforge.net/

rkhunter мануал:
https://www.tecmint.com/install-rootkit-hunter-scan-for-rootkits-backdoors-in-linux/
https://wiki.archlinux.org/title/Rkhunter
https://formulae.brew.sh/formula/rkhunter#default

***

Mobile Verification Toolkit: https://t.me/open_source_friend/1061


---

[[/index|Get Back To Index]]
