`locate` helps us find files. It works like this:
```
[ttilley@somelinux ~]$ locate <string>
```
`locate` can miss new files, because it checks its database for the existence of all files. Sometimes it might require a manual update to do so, using the `updatedb` command. 
### Options
- -i - ignore case
- -n - limit results to -n numbers
- -c - shows the number of matches
- -e - verifies that the file still exists
- -r - search using regular expressions

This command is also good for piping into grep:
```
[ttilley@somelinux ~]$ locate zip | grep bin
```

**Important**: Locate also has other variants, called **plocate** and **mlocate**. They are usually aliased to locate, but it is good to know.

