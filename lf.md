## lf

lf (as in "list files") is a terminal file manager written in Go with a heavy
inspiration from ranger file manager.

### links

1. https://archlinux.org/packages/?name=lf  # arch
2. https://github.com/gokcehan/lf  # github
3. https://formulae.brew.sh/formula/lf#default  # brew

### Bindings (set up in Luke's `lfrc`)

```sh
map <c-f> $lf -remote "send $id select \"$(fzf)\""
map J $lf -remote "send $id cd $(sed -e 's/\s*#.*//' -e '/^$/d' -e 's/^\S*\s*//' ${XDG_CONFIG_HOME:-$HOME/.config}/shell/bm-dirs | fzf)"
map gh
map g top
map D delete
map E extract
map C copyto
map M moveto
map <c-n> push :mkdir<space>""<left>
map <c-r> reload
map <c-s> set hidden!
map <enter> shell
map x $$f
map X !$f
map o &mimeopen "$f"
map O $mimeopen --ask "$f"

map A :rename; cmd-end   # at the very end
map c push A<c-u>        # new rename
map I :rename; cmd-home  # at the very beginning
map i :rename            # before extension
map a :rename; cmd-right # after extension
map B bulkrename
map b $setbg $f

map <c-e> down
map <c-y> up
map V push :!nvim<space>

map W $setsid -f $TERMINAL >/dev/null 2>&1

map U $printf "%s" "$fx" | xclip -selection clipboard
map u $printf "%s" "$fx" | sed 's/.*\///' | xclip -selection clipboard
map . $printf "%s" "$fx" | sed -E 's/^.+\[/https:\/\/www.youtube.com\/watch?v=/' | sed -E 's/\]\..+//' | xclip -selection clipboard
map <gt> $printf "%s" "$fx" | sed -E 's/^.+\[/https:\/\/piped.video\/watch?v=/' | sed -E 's/\]\..+//' | xclip -selection clipboard
map T $sxiv -t "$(pwd)" # opens thumbnail mode
map <c-l> unselect
```

### Default Bindings

`c` --> `Ctrl`

| Comand        | -----   | Key Binding                    |
|---------------|---------|--------------------------------|
| quit          |         | (default 'q')                  |
| up            |         | (default 'k' and '<up>')       |
| half-up       |         | (default '<c-u>')              |
| page-up       |         | (default '<c-b>' and '<pgup>') |
| scroll-up     |         | (default '<c-y>')              |
| down          |         | (default 'j' and '<down>')     |
| half-down     |         | (default '<c-d>')              |
| page-down     |         | (default '<c-f>' and '<pgdn>') |
| scroll-down   |         | (default '<c-e>')              |
| updir         |         | (default 'h' and '<left>')     |
| open          |         | (default 'l' and '<right>')    |
| jump-next     |         | (default ']')                  |
| jump-prev     |         | (default '[')                  |
| top           |         | (default 'gg' and '<home>')    |
| bottom        |         | (default 'G' and '<end>')      |
| high          |         | (default 'H')                  |
| middle        |         | (default 'M')                  |
| low           |         | (default 'L')                  |
| toggle        |         |                                |
| invert        |         | (default 'v')                  |
| invert-below  |         |                                |
| unselect      |         | (default 'u')                  |
| glob-select   |         |                                |
| glob-unselect |         |                                |
| calcdirsize   |         |                                |
| clearmaps     |         |                                |
| copy          |         | (default 'y')                  |
| cut           |         | (default 'd')                  |
| paste         |         | (default 'p')                  |
| clear         |         | (default 'c')                  |
| sync          |         |                                |
| draw          |         |                                |
| redraw        |         | (default '<c-l>')              |
| load          |         |                                |
| reload        |         | (default '<c-r>')              |
| echo          |         |                                |
| echomsg       |         |                                |
| echoerr       |         |                                |
| cd            |         |                                |
| select        |         |                                |
| delete        | (modal) |                                |
| rename        | (modal) | (default 'r')                  |
| source        |         |                                |
| push          |         |                                |
| read          | (modal) | (default ':')                  |
| shell         | (modal) | (default '$')                  |
| shell-pipe    | (modal) | (default '%')                  |
| shell-wait    | (modal) | (default '!')                  |
| shell-async   | (modal) | (default '&')                  |
| find          | (modal) | (default 'f')                  |
| find-back     | (modal) | (default 'F')                  |
| find-next     |         | (default ';')                  |
| find-prev     |         | (default ',')                  |
| search        | (modal) | (default '/')                  |
| search-back   | (modal) | (default '?')                  |
| search-next   |         | (default 'n')                  |
| search-prev   |         | (default 'N')                  |
| filter        | (modal) |                                |
| setfilter     |         |                                |
| mark-save     | (modal) | (default 'm')                  |
| mark-load     | (modal) | (default "'")                  |
| mark-remove   | (modal) | (default '"')                  |
| tag           |         |                                |
| tag-toggle    |         | (default 't')                  |

---

[[/index|Get Back To Index]]
