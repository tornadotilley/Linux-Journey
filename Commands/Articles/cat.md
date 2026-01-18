`cat` can be used to display the contents of a file in the terminal. If we use: `[ttilley@somelinux ~]$ cat sometext.txt`, we will get the contents of the file as output. 

The basic syntax for this command is:
`[ttilley@somelinux ~]$ cat sometext.txt` 

We can also use `cat` to redirect output to a file. 

`[ttilley@somelinux ~]$ cat sometext.txt > someothertext.txt` 



`cat` can also be used to read several files at once. 
`[ttilley@somelinux ~]$ cat sometext1.txt sometext2.txt` 

---
### A little Deeper Into the `cat` Command

If we type the `cat` command without arguments, it will wait for our input. This is helpful in making short text files, like so:

`[ttilley@somelinux ~]$ cat < sometext.txt` 

We can tell cat that we are done by typing `CTRL+D`. 

This will prompt us for our input, and we can open the same file later on. 
*This blew my mind when I first learned about this!!!*

