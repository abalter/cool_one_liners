```
bicb199:/ balter$ l="qqq123abc-123.$9ghijk^^"
bicb199:/ balter$ b=$( `echo $l | sed -E 's/[a-z0-9]+([a-z]{3})-([0-9]+)\.([a-z]+)[^ ]+/\1 \2 \3/'` )
bicb199:/ balter$ first=${b[0]}
bicb199:/ balter$ second=${b[1]}
bicb199:/ balter$ third=${b[2]}
bicb199:/ balter$ echo $first $second $third
abc 123 ghijk
```

```
bicb199:/ balter$ bash <<< `echo $l | sed -E 's/[a-z0-9]+([a-z]{3})-([0-9]+)\.([a-z]+)[^ ]+/first=\1 second=\2 third=\3/'`
bicb199:/ balter$ echo $first $second $third
abc 123 ghijk
```
