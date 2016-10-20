Skip first k lines of a file:  
`tail -n +<k+1> filename`  

Skip first 3 lines of a file:  
`tail -n +4 filename`  
`awk 'NR>2' filename`  
http://stackoverflow.com/a/3508070/188963

Skip last k lines of a file:  
`head -n -k filename`  

Skip last 3 lins of a file:  
`head -n -3 filename`  

http://stackoverflow.com/a/604871/188963
