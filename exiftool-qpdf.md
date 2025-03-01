## exiftool and qpdf cheatsheet

### links

1. https://exiftool.org/
2. https://archlinux.org/packages/?name=perl-image-exiftool
3. https://archlinux.org/packages/extra/x86_64/qpdf/ -- qpdf

### pdf

[instruction from exiftool][002] :

All metadata edits are reversible. While this would normally be considered an
advantage, it is a potential security problem because old information is never
actually deleted from the file. (However, after running ExifTool the old
information may be removed permanently using the `qpdf` utility with this
command `qpdf --linearize in.pdf out.pdf`)

[QPDF][001] — Content-preserving PDF transformation system.

[instruction from Arch Wiki][003] how to remove metadata Using ExifTool:

```sh
exiftool -All= -overwrite_original input.pdf
mv input.pdf /tmp/temp.pdf
qpdf --linearize /tmp/temp.pdf input.pdf
```

The linearize step is needed to prevent recovery of deleted metadata.

---

THE END

[001]: https://github.com/qpdf/qpdf "Content-preserving PDF transformation system"
[002]: https://exiftool.org/TagNames/PDF.html "exiftool and qpdf"
[003]: https://wiki.archlinux.org/title/PDF,_PS_and_DjVu "Remove metadata"
