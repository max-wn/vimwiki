## SC-IM

[sc-im](https://github.com/andmarti1424/sc-im) is an ncurses based, vim-like spreadsheet calculator based on sc. Spreadsheet Calculator Improvised, aka sc-im, is an ncurses based, vim-like spreadsheet calculator.

### links

1. [direct link](https://github.com/andmarti1424/sc-im)
2. [help file](https://raw.githubusercontent.com/andmarti1424/sc-im/freeze/src/doc)
3. [tutor](https://github.com/jonnieey/Sc-im-Tutorial/blob/master/Lesson1_Navigation.sc)

### quick start

|        Key       |                 Purpose                 |
|------------------|-----------------------------------------|
|         =        | Insert a numeric value                  |
|         \        | Insert a text value                     |
|         e        | Edit a numeric value                    |
|         E        | Edit a string value                     |
|         x        | Delete current cell content             |
|        :q        | Quit the app                            |
|        :h        | See help                                |
|  :w filename.sc  | Save current spreadsheet in sc format   |
|         j        | Move down                               |
|         k        | Move up                                 |
|         h        | Move left                               |
|         l        | Move right                              |
|      gtab12      | go to cell AB12                         |
|         u        | undo last change                        |
|        C-r       | redo last change undone                 |
|        yy        | Copy current cell                       |
|         v        | select a range using cursor/hjkl keys   |
|         p        | paste a previously yanked cell or range |
|        ir        | insert row                              |
|        ic        | insert column                           |
|        dr        | delete row                              |
|        dc        | delete column                           |
|        gg        | go to the first cell in the sheet       |
|        G         | go to the last valid cell in the sheet  |


#### Instructions for sc-in tutorial

Open files with sc-im eg.
```sh
sc-im Lesson1 - Navigation.sc
```

### sc-im-md integrator

Edit embedded markdown tables with SC-IM in a Vim terminal window.

**Link:**

1. https://github.com/mipmip/vim-scimark

**Usage:**

1. Point your cursor on a markdown table and press `<leader>sc`
2. From here you are inside `sc-im`.
3. The most minimal table scimark reckognizes is `||`.
4. See more in `:help Scimark`

TODO
- [O] study sc-im tutorial: https://github.com/jonnieey/Sc-im-Tutorial
  - [X] 0. Lesson0 - General commands and shortcuts in sc-im
  - [X] 1. Lesson1 - Navigation
  - [X] 2. Lesson2 - Formatting cell contents
  - [X] 3. Lesson3 - Copy, Paste, Cut basics
  - [X] 4. Lesson4 - Copy, Paste, Cut
  - [X] 5. Lesson5 - Marks
  - [X] 6. Lesson6 - Sc-im Modes
  - [X] 7. Lesson7 - Insert and Edit Mode
  - [X] 8. Lesson8 - Visual Mode
  - [X] 9. Lesson9 - Command Mode
  - [X] 10. Lesson10 - Configuration File
  - [X] 11. Lesson11 - Numeric Functions
  - [ ] 12. Lesson12 - String Functions
  - [ ] 13. Lesson13 - Date Functions
  - [ ] 14. Lesson 14 - Conditional Function "if"
- [X] try this plugin: https://github.com/mipmip/vim-scimark

---

[[/index|Get Back To Index]]
