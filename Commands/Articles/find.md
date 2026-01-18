*The find command is a very expansive program. This article is far from finished, but more is coming.*
`find`, in its simplest use-case, finds files in directories for us. As an argument, it takes a directory to search for a file. By default, it will just make a list of all of the files in the directory. The basic structure of the command is as follows:
```
[ttilley@somelinux ~]$ find <path> <expression> <action>
```
One of the most common ways of using `find`, to find files of only a certain type. 
```
[ttilley@somelinux ~]$ find ~/Documents -name "*.pdf"
```
This is a very powerful command, with many utilities. At the end of finding, we can then take an action, using the -exec flag. 
```
[ttilley@somelinux ~]$ find ~/Documents -name "*.pdf" -exec mv {} ~/somedirectory \;
```
The same thing can be accomplished using:
```
[ttilley@somelinux ~]$ find ~/Documents -name "*.pdf" -exec mv -t ~/somedirectory {} +
```
It is also good practice to see what the find command will output before committing. 
```
[ttilley@somelinux ~]$ find ~/Documents -name "*.pdf" -ls
```

There are many parameters for the command to go by, such as type, size, name, wordcount, etc.

### Finding Files by Type

Using the `-type` option, we can specify the kinds of files that we want to test for.
- b - block special device
- c - character special device
- d - directory
- f - regular file
- l - symbolic link

### Finding Files by Size

Using the `-size` flag, we can search for files by size. 
- b - 512-byte blocks; the default 
- c - bytes
- w - 2-byte words
- k - kilobytes (1024 bytes)
- M - megabytes (1048576 bytes)
- G - gigabytes (1073741824 bytes)

### Find Tests
![[Pasted image 20260101140601.png]]
![[Pasted image 20260101140629.png]]
*This was taken from the 'TLCL', by William Shots.*

### Operators 
![[Pasted image 20260101141243.png]]


### Best Practices
Find can be used for many things involving files. Below will be some examples that can be very useful. 
```
[ttilley@somelinux ~]$ find ~ -print
```

```
[ttilley@somelinux ~]$ find ~ -type f -name '*.bak' -print
```
This command will find all f type (regular) files, that end with the text .bak, and print all of the matches out. If we change the `-print` command for the `-delete` command, it will delete all of the matching entries. 
```
[ttilley@somelinux ~]$ find ~ -type f -name '*.bak' -delete
```
The same command can be expressed like this:
```
[ttilley@somelinux ~]$ find ~ -type f and -name '*.bak' -delete
```
Below is a screenshot of a better explanation of this:
![[Pasted image 20260101221919.png]]


### User-Defined Actions

We can specify other actions to be taken, by using the `-exec` command. It is written like this:
```
exec <command> {} ;
```

The {} and the ; have special meaning, so they must be single quoted or escaped to avoid any unwanted expansion. 

```
find ~ -type f -name 'foo*' -exec ls -l '{}' ';'
```

### **';' vs +**
The `-exec` launches a new instance of the command specified. There is a bit of inefficiency if we use a ';' at the end of our statement, because it will cause the command to be executed once for each file. This could take some time if we have hundreds of files to use the command on. For this, we could use the +. This first builds a list of the matching files and then executes the command one time.
```
find ~ -type f -name 'foo*' -exec ls -l '{}' ';'
```
vs 
```
find ~ -type f -name 'foo*' -exec ls -l '{}' +
```

### Xargs Use
We can also use `xargs` command. For more information on that specific command, check it out on the [[xargs]] note.
```
[ttilley@somelinux ~]$ find ~ -type f -name 'foo*' -print | xargs ls -l
```
