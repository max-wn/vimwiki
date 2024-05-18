## khal

### links
khal
https://archlinux.org/packages/?sort=&q=khal&maintainer=&flagged=  # pacage info
https://github.com/pimutils/khal  # github
https://khal.readthedocs.io/en/latest/  # documentation
https://formulae.brew.sh/formula/khal#default  # brew
https://khal.readthedocs.io/en/latest/configure.html  # instructions vdirsyncer
https://vdirsyncer.pimutils.org/en/stable/tutorial.html  # syncroniser tuturilal
https://github.com/pimutils/vdirsyncer  # github

### tips

allows for adding new events interactively.

```bash
khal new -i
```

shows all events scheduled for a given date (or datetime) range, with custom formatting:

```bash
khal list 2024-05-01 2024-06-01
# or
khal calendar today 30d
```

examples of long commands

khal new [-a CALENDAR] [OPTIONS] [START [END | DELTA] [TIMEZONE] SUMMARY
[:: DESCRIPTION]]

```bash
khal new -g meeting -r yearly 2024-05-15 21:30 21:31 Test summary :: Test description
```

---

[[/index|Get Back To Index]]
