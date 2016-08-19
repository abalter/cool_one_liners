Finding multiple start/stop positions of one string in another with overlap:

```
>>> a="cgctacgct"
>>> b="cggtggc" + a + a[4:] + "ttggcagtttca" + a
>>> b
'cggtggccgctacgctacgctttggcagtttcacgctacgct'
>>> r = [(m.start(), m.end() + len(a)-1) for m in re.finditer("(?=" + a + ")",b)]
>>> r
[(7, 15), (12, 20), (33, 41)]
>>> 
```

http://stackoverflow.com/a/4664889/188963
http://stackoverflow.com/a/37313669/188963


In R

http://stackoverflow.com/a/7879329/188963

```
gregexpr("(?=CC)","CCCGTGCC",perl=TRUE)
[[1]]
[1] 1 2 7
attr(,"match.length")
[1] 0 0 0
```
