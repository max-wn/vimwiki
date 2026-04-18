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

### TLDR

`exiftool` Read and write meta information in files.
More information: https://exiftool.org/exiftool_pod.html.

```sh
# Print the EXIF metadata for a given file:
exiftool path/to/file
# Remove all EXIF metadata from the given files:
exiftool -All= path/to/file1 path/to/file2
# Remove GPS EXIF metadata from given image files:
exiftool "-gps*=" path/to/image1 path/to/image2
# Remove all EXIF metadata from the given image files, then re-add metadata for color and orientation:
exiftool -All= -tagsfromfile @ -colorspacetags -orientation path/to/image1 path/to/image2
# Move the date at which all photos in a directory were taken 1 hour forward:
exiftool "-AllDates+=0:0:0 1:0:0" path/to/directory
# Move the date at which all JPEG photos in the current directory were taken 1 day and 2 hours backward:
exiftool "-AllDates-=0:0:1 2:0:0" -extension jpg
# Only change the DateTimeOriginal field subtracting 1.5 hours, without keeping backups:
exiftool -DateTimeOriginal-=1.5 -overwrite_original
# Recursively rename all JPEG photos in a directory based on the DateTimeOriginal field:
exiftool '-filename<DateTimeOriginal' -dateFormat %Y-%m-%d_%H-%M-%S%%lc.%%e path/to/directory -recurse -extension jpg
```

---

THE END

[001]: https://github.com/qpdf/qpdf "Content-preserving PDF transformation system"
[002]: https://exiftool.org/TagNames/PDF.html "exiftool and qpdf"
[003]: https://wiki.archlinux.org/title/PDF,_PS_and_DjVu "Remove metadata"
