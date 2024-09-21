## MPD

(music player daemon) is an audio player that has a server-client architecture. It plays audio files, organizes playlists and maintains a music database, all while using very few resources. In order to interface with it, a separate [client](ncmpcpp.md) is needed.

### links
https://wiki.archlinux.org/title/Mpd -- archwiki
https://mpd.readthedocs.io/en/stable/user.html -- documentation
https://www.musicpd.org/

### start
TODO
this below does not work
```sh
systemctl start mpd
systemctl status mpd
systemctl --user enable mpd.service
ncmpcpp
```
it works if just run `mpd` and `ncmpcpp`

---

[[/index|Get Back To Index]]
