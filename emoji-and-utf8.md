## some advices for font configuration

### commands
```bash
fc-match monospace  # check the best font for monospace
fc-match emoji      # check the best font for emoji

cat Downloads/emoji-test.txt | less  # emoji test file

fc-list : family style | grep "PT Mono"  # see exact names of font families

sudo pacman -S ttf-inconsolata-lgc-nerd  # inconsolata with added the Cyrillic alphabet
sudo pacman -S ttf-joypixels             # font for emoji and icons

curl https://www.cl.cam.ac.uk/~mgk25/ucs/examples/UTF-8-demo.txt  # UTF-8 test file
```

### links
https://github.com/ryanoasis/nerd-fonts
https://www.paratype.com/collections/pt/44157
