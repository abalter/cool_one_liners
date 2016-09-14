http://stackoverflow.com/questions/16956810/how-to-find-all-files-containing-specific-text-on-linux

Do the following:

<!-- language: lang-sh -->

    grep -rnw '/path/to/somewhere/' -e "pattern"

* `-r` or `-R` is recursive, 
* `-n` is line number, and 
* `-w` stands match the whole word. 
* `-l` (lower-case L) can be added to just give the file name of matching files.
* Along with these, `--exclude` or `--include` parameter could be used for efficient searching. Something like below:

<!-- language: lang-sh -->

    grep --include=\*.{c,h} -rnw '/path/to/somewhere/' -e "pattern"

This will only search through the files which have .c or .h extensions. Similarly a sample use of `--exclude`:

<!-- language: lang-sh -->

    grep --exclude=*.o -rnw '/path/to/somewhere/' -e "pattern"

Above will exclude searching all the files ending with .o extension. Just like exclude file it's possible to exclude/include directories through `--exclude-dir` and `--include-dir` parameter; for example, the following shows how to integrate `--exclude-dir`:

<!-- language: lang-sh -->

    grep --exclude-dir={dir1,dir2,*.dst} -rnw '/path/to/somewhere/' -e "pattern"

This works very well for me, to achieve almost the same purpose like yours.

For more options : 
<!-- language: lang-sh -->

    man grep
