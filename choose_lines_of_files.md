

 here is the very pithy `sed` way of finding every 4th line, as a one-liner that turns 4-line fastq into 2-line fasta:
 
     sed -n '1~4s/^@/>/p;2~4p
     
http://stackoverflow.com/a/9895102/188963

This is easy to accomplish with awk.

Remove every other line:

    awk 'NR % 2 == 0' file > newfile


Remove every 10th line:

    awk 'NR % 10 != 0' file > newfile

The NR variable in awk is the line number. Anything outside of { } in awk is a conditional, and the default action is to print.


http://stackoverflow.com/a/9895062/188963

You could possibly do it with sed, e.g.

    sed -n -e 'p;N;d;' file # print every other line, starting with line 1

If you have GNU sed it's pretty easy

    sed -n -e '0~10p' file # print every 10th line
    sed -n -e '1~2p' file # print every other line starting with line 1
    sed -n -e '0~2p' file # print every other line starting with line 2
