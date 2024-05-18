## VimWiki

### links
https://github.com/vimwiki/vimwiki/tree/dev
https://vimwiki.github.io/
https://vimwiki.github.io/vimwikiwiki/Tips%20and%20Snips.html
https://samgriesemer.com/Vimwiki

### basis
`vim -c VimwikiIndex`  open vimwiki from terminal
leader is ","

### The basic vimwiki command set

### wiki management
**action**
`[number] <leader> ww` open wiki index file
`[number] <leader> wt` open wiki index file in new tab
`<leader> ws`          list and select available wiki
`<leader> wd`          delete wiki page
`<leader> wr`          rename wiki page
**number** is relative wiki order as defined in `.vimrc`, default `1`.

### diary management
**action**
`[number] <leader> wi` open diary index file for wiki
`<leader> w <leader> i` update current diary index
`[number] <leader> w <leader> w` open today’s diary file for wiki
`[number] <leader> w <leader> t` open today’s diary file for wiki in new tab
`<C-Up>` open previous day’s diary
`<C-Down>` open next day’s diary
**number** is relative wiki order as defined in `.vimrc`, default `1`.

### navigation
**action**
`<CR>`        follow/create wiki link
`<C-S-CR>`    follow/create wiki link in new tab
`<backspace>` go back to previous wiki page
`<Tab>`       go to next link on current page
`<S-Tab>`     go to previous link on current page

### editing shortcuts
**action**
`<C-Space>` toggle list item on/off
`#` add header level
`-` remove header level
`+` create/decorate links
`glm` increase indent of list item
`gll` decrease indent of list item
`gl**` or `gl8` switch or insert “**” symbol
`gl#` or `gl3` switch or insert “#” symbol
`gl-` switch or insert “-“ symbol
`gl1` switch or insert “1.” symbol

### table shortcuts
**action**
`<A-Left>` move column left
`<A-right>` move column right
`<CR>` (insert mode) go down/create cell
`<Tab>` (insert mode) go next/create cell
`gqq` or `gww` reformat table

### text objects
**object**
`ah` section between 2 headings including empty trailing lines
`ih` section between 2 headings excluding empty trailing lines
a\ table cell
i\ inner table cell
`ac` table column
`ic` inner table column

### Commands

`:Vimwiki2HTML` -- Convert current wiki link to HTML.
`:VimwikiAll2HTML` -- Convert all your wiki links to HTML.
`:help vimwiki-commands` -- List all commands.
`:help vimwiki` -- General vimwiki help docs.


### typefaces

There are a few typefaces that give you a bit of control over how your text
is decorated:

  *bold text*
  _italic text_
  _*bold italic text*_
  *_bold italic text_*
  ~~strikeout text~~
  `code (no syntax) text`
  super^script^
  sub,,script,,

For Markdown syntax these variations are used:

  **bold text** or __bold text__
  *italic text* or _italic text_
  ***bold_italic text*** or ___italic_bold text___

Furthermore, there are a number of words which are highlighted extra flashy:
TODO, DONE, STARTED, FIXME, FIXED, XXX.

### Markdown Links

These links are only available for Markdown syntax.  See
http://daringfireball.net/projects/markdown/syntax#link.

Inline link:
  [Looks like this](URL)

Image link:
  ![Looks like this](URL)

Reference-style links:
  a) [Link Name][Id]
  b) [Id][], using the "implicit link name" shortcut

Reference style links must always include two consecutive pairs of
[-brackets, and field entries can not use "[" or "]".

### External files

The "file:" and "local:" schemes allow you to directly link to arbitrary
resources using absolute or relative paths:
  [[file:~/latex-templates/README.md]]
  [[file:~/latex-templates/|Link to a directory]]
  [[local:~/latex-templates/README.md]]

These links are opened with the system command, i.e. !xdg-open (Linux), !open
(Mac), or !start (Windows).

### VimwikiSearch /pattern/
`:VWS /pattern/`
    Search for `/pattern/` in all files of current wiki.
    To display all matches use `|:lopen|` command.
    To display next match use `|:lnext|` command.
    To display previous match use `|:lprevious|` command.



---

[[/index|Get Back To Index]]
