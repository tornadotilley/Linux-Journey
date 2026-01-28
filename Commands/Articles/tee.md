`tee` lets us write the standard output of one command to 1 or more files. 
```
[ttilley@somelinux ~]$ ls | tee file1.txt file2.txt file3.txt
```
We could also grab the input from echo:
```
[ttilley@somelinux ~]$ echo 'I love Linux!!' | tee file1.txt file2.txt file3.txt
```
If we want to write to a file that requires sudo privileges, we can add sudo to the beginning of the tee command:
```
[ttilley@somelinux ~]$ ls | sudo tee file1.txt file2.txt file3.txt
```
### Flags

- `-a` - used to append the output to a file
- `-i` - ignores interrupts
