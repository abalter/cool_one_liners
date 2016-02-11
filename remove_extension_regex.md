http://stackoverflow.com/a/29981305/188963

Now, if you want some stylish old-school regexp:

    echo "foo.bar.tar.gz" | sed "s/^\(.*\)\..*$/\1/"

-> Shall return:  foo.bar.tar

<pre>
I will break it down: 
s/     Substitute
^      From the beginning
\(     Mark
.*     Everything (greedy way)
\)     Stop Marking (the string marked goes to buffer 1)
\.     until a "." (which will be the last dot, because of the greedy selection)
.*     select everything (this is the extension that will be discarded)
$      until the end
/      With (substitute)
\1     The buffer 1 marked above (which is the filename before the last dot(.)
/      End
</pre>

Cristiano Savino


http://stackoverflow.com/a/30863119/188963

Here are some alternative suggestions (mostly in `awk`), including some advanced use cases, like extracting version numbers for software packages.  

    f='/path/to/complex/file.1.0.1.tar.gz'
    
    # Filename : 'file.1.0.x.tar.gz'
    	echo "$f" | awk -F'/' '{print $NF}'
    
    # Extension (last): 'gz'
    	echo "$f" | awk -F'[.]' '{print $NF}'
    	
    # Extension (all) : '1.0.1.tar.gz'
    	echo "$f" | awk '{sub(/[^.]*[.]/, "", $0)} 1'
    	
    # Extension (last-2): 'tar.gz'
    	echo "$f" | awk -F'[.]' '{print $(NF-1)"."$NF}'
    
    # Basename : 'file'
    	echo "$f" | awk '{gsub(/.*[/]|[.].*/, "", $0)} 1'
    
    # Basename-extended : 'file.1.0.1.tar'
    	echo "$f" | awk '{gsub(/.*[/]|[.]{1}[^.]+$/, "", $0)} 1'
    
    # Path : '/path/to/complex/'
    	echo "$f" | awk '{match($0, /.*[/]/, a); print a[0]}'
    	# or 
    	echo "$f" | grep -Eo '.*[/]'
    	
    # Folder (containing the file) : 'complex'
    	echo "$f" | awk -F'/' '{$1=""; print $(NF-1)}'
    	
    # Version : '1.0.1'
    	# Defined as 'number.number' or 'number.number.number'
    	echo "$f" | grep -Eo '[0-9]+[.]+[0-9]+[.]?[0-9]?'
    
    	# Version - major : '1'
    	echo "$f" | grep -Eo '[0-9]+[.]+[0-9]+[.]?[0-9]?' | cut -d. -f1
    
    	# Version - minor : '0'
    	echo "$f" | grep -Eo '[0-9]+[.]+[0-9]+[.]?[0-9]?' | cut -d. -f2
    
    	# Version - patch : '1'
    	echo "$f" | grep -Eo '[0-9]+[.]+[0-9]+[.]?[0-9]?' | cut -d. -f3
    
    # All Components : "path to complex file 1 0 1 tar gz"
    	echo "$f" | awk -F'[/.]' '{$1=""; print $0}'
    	
    # Is absolute : True (exit-code : 0)
    	# Return true if it is an absolute path (starting with '/' or '~/'
    	echo "$f" | grep -q '^[/]\|^~/'
     
    

All use cases are using the original full path as input, without depending on intermediate results.
