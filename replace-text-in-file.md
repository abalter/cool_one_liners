http://stackoverflow.com/a/11145362/188963

    sed -i 'Ns/.*/replacement-line/' file.txt

where `N` should be replaced by your target line number. This replaces the line in the original file. To save the changed text in a different file, drop the `-i` option:

    sed 'Ns/.*/replacement-line/' file.txt > new_file.txt
    
http://stackoverflow.com/a/11145377/188963

    awk 'NR==4 {$0="different"} { print }' input_file.txt
    
http://unix.stackexchange.com/a/70879/151352
    
You can specify line number in sed or NR (number of record) in awk.

    awk 'NR==34 { sub("AAA", "BBB") }'
or use FNR (file number record) if you want to specify more than one file on the command line.

    awk 'FNR==34 { sub("AAA", "BBB") }'

or

    sed '34s/AAA/BBB/'

to do in-place replacement with sed

    sed -i '34s/AAA/BBB/' file_name
    

http://unix.stackexchange.com/a/112024/151352

 - You can combine `sed` commands:

        sed -i 's/foo/bar/g; s/baz/zab/g; s/Alice/Joan/g' file

 Be aware that order matters (`sed 's/foo/bar/g; s/bar/baz/g'` will substitute `foo` with `baz`).



