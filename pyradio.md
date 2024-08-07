## pyradio

### links
Aur
https://aur.archlinux.org/packages/pyradio

GitHub
https://github.com/coderholic/pyradio

Documentation
https://github.com/coderholic/pyradio/blob/master/docs/index.md

### Controls

                      Main window                                      Playlists window                   Themes window
    -------------------------------------------------------------------------------------------------------------------------------------
    Up/Down/j/k/
    PgUp/PgDown       Change station selection                         Change station playlist            Change station theme
    g                 Jump to first station                            Jump to first playlist             Jump to first theme
    <n>G              Jump to n-th / last station                      Jump to n-th / last playlist       Jump to n-th / last theme
    H M L             Jump to the top / middle bottom of the list      [Valid]                            -
    P                 Jump to playing station                          Jump to playing playlist           -
    Enter/Right/l     Play selected station                            Open selected playlist             Apply selected theme
    `^N` / `^P`           Play next/previous station                       -                                  -
    r                 Select and play a random station                 Re-read playlists from disk        -
    Space/Left/h      Stop/start playing selected station              -                                  -
    Space             -                                                -                                  Apply theme and make it default
    -/+ or ,/.        Change volume                                    [Valid]                            [Valid]
    m                 Mute / unmute player                             [Valid]                            [Valid]
    v                 Save volume (not applicable for vlc)             [Valid]                            [Valid]
    *                 Add station to favorites                         -                                  -
    o s R             Open / Save / Reload playlist                    -                                  -
    a A               Add / append a new station                       -                                  -
    e                 Edit current station                             -                                  -
    E                 Change station's encoding                        -                                  -
    DEL,x             Delete selected station                          -                                  -
    O                 Open RadioBrowser                                -                                  -
    < >               Browse the Stations history list                 -                                  -
    t T               Load theme / Toggle transparency                 [Valid]                            [Valid]
    c                 Open Configuration window.                       -                                  -
    | (vertical       Enable / disable recording
       line or
       pipe symbol)
    / n N             Search, go to next / previous result             [Valid]                            [Valid]
    J                 Create a jump tag
    `<n>^U` `<n>^D`       Move station up / down.                          -                                  -
    ' \ y             Get into Registers, Extra Commands               y (yank) is not applicable         -
                      and Yank modes, respectively
    z                 Toggle "Force http connections"                  -                                  -
    Z                 Display the "Extra Player Parameter" window      -                                  -
    ?                 Show keys help                                   [Valid]                            [Valid]
    `#`                 Redraw window                                    [Valid]                            [Valid]
    Esc/q             Quit                                             -                                  -
    Esc/q/Left/h      -                                                Cancel / close window              Cancel / close window

The same logic applies to all **PyRadio** windows.

**Note:** When inserting numbers (either to jump to a station or to move a station), the number will be displayed at the right bottom corner of the window, suffixed by a "*G*", i.e. pressing *35* will display *[35G]*.

**Note:** When tagging a station position for a move action (by pressing "**J**"), the position will be displayed at the right bottom corner of the window, suffixed by a "*J*", i.e. pressing "*J*" on position *35* will display *[35J]*.


### Global shortcuts

Some of the functions provided by **PyRadio** will always be available to the user. These functions are:

| Shortcut                       |   Function            |Shortcut                       |   Function            |
|--------------------------------|-----------------------|-------------------------------|-----------------------|
| **\+** / **\-** and **,** / **\.** | adjust volume         |**W**                          | toggle title logging |
| **m**                          | mute player           |**w**                          | like a station        |
| **v**                          | save volume           |**^N** / **^P** [1] [2]|play next / previous station|
| **T**                          | toggle transparency   |**<** / **>** [1]             | play next / previous station history entry|

Every window in **PyRadio** will respect these shortcuts, even the ones with a "*Press any key to...*" message.

When focus is on a "*Line editor*", all shortcuts will work when preceded by a "**\\**".


---

[[/index|Get Back To Index]]
