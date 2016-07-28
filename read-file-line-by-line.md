Not a 1-liner, but

The following (save as `rr.sh`) reads a file passed as an argument line by line:

    #!/bin/bash
    while IFS='' read -r line || [[ -n "$line" ]]; do
        echo "Text read from file: $line"
    done < "$1"

Explanation:

- `IFS=''` (or `IFS=`) prevents leading/trailing whitespace from being trimmed.
- `-r` prevents backslash escapes from being interpreted.
- `|| [[ -n $line ]]` prevents the last line from being ignored if it doesn't end with a `\n` (since `read` returns a non-zero exit code when it encounters EOF).

Run the script as follows:

    chmod +x rr.sh
    ./rr.sh filename.txt

....
