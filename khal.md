## khal

### links
https://archlinux.org/packages/?sort=&q=khal&maintainer=&flagged=
https://github.com/pimutils/khal
https://formulae.brew.sh/formula/khal#default
https://lostpackets.de/khal/index.html

### tips

allows for adding new events interactively.
```
khal new -i
```

shows all events scheduled for a given date (or datetime) range, with custom formatting:
```
khal list 01/10/2022 30/12/2023
```

examples of long commands
```
khal new -r yearly 10/12/2022 09:00 09:01 Купи и отошли открытки всем на Новый Год :: send postcard
khal new -r yearly 18/12/2022 09:00 09:01 ДР Нов Анн 18.12.2006 :: С Днём Рождения!!!
khal new -r yearly 09/02/2023 09:00 09:01 Купи и отошли открытки всем на 23 февраля :: send postcard
khal new -r yearly 29/03/2023 09:00 09:01 Купи и отошли открытки всем на 12 апреля :: send postcard
khal new -r yearly 25/04/2023 09:00 09:01 Купи и отошли открытки всем на 09 мая :: send postcard
khal new -r yearly 03/12/2022 09:00 09:01 ДР Ком Ник 03.12.1976 :: С Днём Рождения!!!

```

---

[[/index|Get Back To Index]]
