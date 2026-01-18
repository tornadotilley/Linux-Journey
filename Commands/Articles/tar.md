`tar` stands for tape archive. It is used to archive files into one large file. The options for `tar` are:

- `-x` - extracts the files from the archive. 
- `-f` - specifies the file
- `-z` - this is for gzip, compressing or decompressing, depending 
- `-C` - switches to the directory that we want to extract the file to
### Common Uses
```
[ttilley@somelinux ~]$ tar -xf archive.tar -C /some/other/directory
```


