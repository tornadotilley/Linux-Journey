`xargs` takes the standard input from one command and makes it into an argument list for another command. 
```
[ttilley@somelinux ~]$ find ~ -type f -name 'foo*' -print | xargs ls -l
```
The amount of arguments for this command are not infinite. To look at the limit, use `xargs --show-limits`. 