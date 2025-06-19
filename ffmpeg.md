## ffmpeg

complete, cross-platform solution to record, convert and stream audio and video

### links

1. https://wiki.archlinux.org/title/FFmpeg

### usage

```sh
# convert an entire directory with ffmpeg for example from 'opus' to 'mp3'
cd /path/to/dir
for i in *.opus; do ffmpeg -i "$i" "${i%.*}.mp3"; done
```

---

[[/index|Get Back To Index]]
