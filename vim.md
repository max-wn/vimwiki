## VIM

### clipdoard

#### links
https://vim.fandom.com/wiki/Accessing_the_system_clipboard
https://stackoverflow.com/questions/3961859/how-to-copy-to-clipboard-in-vim
https://stackoverflow.com/questions/11489428/how-to-make-vim-paste-from-and-copy-to-systems-clipboard
https://wiki.archlinux.org/title/Vim

Getting Vim to work with the X11 clipboard can be a struggle if you want to
run Vim in a terminal. In this case, you will have to check for X11 clipboard
support. The GUI version of Vim always has clipboard support.

```
vim --version | grep clipboard
```

If you see `+clipboard` or `+xterm_clipboard`, you are good to go. If it's
`-clipboard` and `-xterm_clipboard`, you will need to look for a version of Vim
that was compiled with clipboard support.
For Archlinux it is [gvim](https://archlinux.org/packages/?name=gvim), Vi
Improved, a highly configurable, improved version of the vi text editor (with
advanced features, such as a GUI)

### vim cheat sheets

[vim-basis](vim-basis.md)
[vim-cheat-sheet](vim-cheat-sheet.md)
[vim-commands](vim-commands.md)

### vim plugins

[vimplug](vimplug.md) -- a minimalist Vim plugin manager

#### vim-commentary
https://github.com/tpope/vim-commentary
Comment stuff out. Use `gcc` to comment out a line (takes a count), `gc` to comment out the target of a motion (for example, `gcap` to comment out a paragraph), `gc` in visual mode to comment out the selection, and `gc` in operator pending mode to target a comment. You can also use it as a command, either with a range like `:7,17Commentary`, or as part of a `:global` invocation like with `:g/TODO/Commentary`. That's it.

Oh, and it uncomments, too. The above maps actually toggle, and `gcgc` uncomments a set of adjacent commented lines.

---

[[/index|Get Back To Index]]
