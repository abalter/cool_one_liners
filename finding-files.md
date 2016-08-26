Finding files bigger than a certain size, and sorting them

    find / -type f -size +50M -exec du -h {} \; | sort -n
