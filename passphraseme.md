## passphraseme

A quick and simple cryptographically secure script to generate high entropy
passphrases using the Electronic Frontier Foundation's wordlists, including
their fandom-inspired wordlists.

https://pypi.org/project/passphraseme/

https://github.com/micahflee/passphraseme


```bash
pip3 install passphraseme
```

usage:

```bash
passphraseme [-h] [--sep [sep]]
                    [-l | -s1 | -s2 | -got | -hp | -st | -sw | -d [dictionary]]
                    [word_count]
```

positional arguments:
  `word_count`             Word count

optional arguments:
 `-h, --help`              show this help message and exit
 `--sep [sep]`             Separator
 `-l, --large`             Use EFF's general large wordlist
 `-s1, --short1`           Use EFF's general short wordlist
 `-s2, --short2`           Use EFF's short wordlist with unique prefixes
 `-got, --game-of-thrones` Use EFF's Game of Thrones wordlist (Passwords of Westeros)
 `-hp, --harry-potter`     Use EFF's Harry Potter wordlist (Accio Passphrase!)
 `-st, --star-trek`        Use EFF's Star Trek wordlist (Live Long and Passphrase)
 `-sw, --star-wars`        Use EFF's Star Wars wordlist (The Passphrase Is Strong With This One)
 `-d [dictionary], --dictionary [dictionary]` Custom wordlist filename


---

[[/index|Get Back To Index]]
