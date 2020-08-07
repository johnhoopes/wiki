<!-- TITLE: Bash Scripting -->
<!-- SUBTITLE: A quick summary of Bash Scripting -->

# While Loop
```
while [ $i -lt 4 ]
do
xterm &
i=$[$i+1]
done
```

# For Loop
```
for fn in `cat filenames.txt`; do
    echo "the next file is $fn"
    cat $fn
done
```