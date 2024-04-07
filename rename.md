## rename
Renames multiple files using Perl regular expressions.

### links
https://formulae.brew.sh/formula/rename#default  # brew
https://archlinux.org/packages/community/any/perl-rename/  # arch
https://metacpan.org/release/PEDERST/rename-1.11/view/bin/rename.PL  # manual

### convention
this-is-a-file-neme.extention

### examples
To rename all files matching *.bak to strip the extension, you might say
```
rename 's/\e.bak$//' *.bak
```

To translate uppercase names to lower, you'd use
```
rename 'y/A-Z/a-z/' *
```

### more examples
```
rename 's/\.flip$/.flop/' *     # rename *.flip to *.flop
rename s/flip/flop/ *           # rename *flip* to *flop*
rename 's/^s\.(.*)/$1.X/' *     # switch sccs filenames around
rename 's/$/.orig/' */*.[ch]    # add .orig to source files in */
rename 'y/A-Z/a-z/' *           # lowercase all filenames in .
rename 'y/A-Z/a-z/ if -B' *     # same, but just binaries! or even
rename chop *~                  # restore all ~ backup files
```

### rename by vifm
https://www.youtube.com/watch?v=a4scYdubKbo

### rename by mc
https://www.youtube.com/watch?v=OuirSrSNgYI

---

[[/index|Get Back To Index]]
