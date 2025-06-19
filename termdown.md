## termdown

Countdown timer and stopwatch in your terminal

### links
1. https://archlinux.org/packages/?name=termdown
2. https://github.com/trehn/termdown

### usage

see `tldr termdown` and `termdown --help`

### examples

```sh
termdown -ab -f digital
termdown 1h30m20s -abe -c 10 -f digital -T "This Is My Timer"
# -a, --alt-format --> Use colon-separated time format
# -b, --blink      --> Flash terminal at end of countdown
# -e, --end        --> Display target datetime of unpaused countdown
# -c, --critical N --> Draw final N seconds in red and announce them individually with --voice or --exec-cmd (defaults to 3)
# -f, --font FONT  --> Choose from http://www.figlet.org/examples.html
# -T, --title TEXT --> Text to display on top of countdown/stopwatch
```

---

[[/index|Get Back To Index]]
