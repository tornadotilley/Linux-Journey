`tar` stands for tape archive. It is used to archive files into one large file. The options for `tar` are:

- `-c` - creates a tarball
- `-C` - switches to the directory that we want to extract the file to
- `-f` - specifies the file
- `-p` - preserves the file permissions (important if creating a tarball as a normal user)
- `-r` - appends files to the end of an extant tarball
- `-t` - lists the contents of the tarball
- `-v` - verbose mode
- `-x` - extracts the files from the archive. 
- `-z` - this is for gzip, compressing or decompressing, depending 
### Common Uses
```
[ttilley@somelinux ~]$ tar -xf archive.tar -C /some/other/directory
```


