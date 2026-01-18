The less command starts the less program inside of the shell. It lets us scroll backward and forward through text. 
Look at this code example:
`[me@somelinux ~]$ less /etc/passwd` 

Once the program is started, we can scroll down and up through the file. To quit the file, simply press q on the keyboard. 

If something gets scrambled in the terminal with `less`, just use the `reset` command. 

Here is an image with a table of key binds:
![[Pasted image 20251207204353.png]]

Less falls into the category of programs called "pagers". These programs allow for the easy viewing of long text files. 

There is a funny way of remembering this command for me. They say that 'less is more'.

There is a program called [[more]]. The more program is an older version of [[less]]. 