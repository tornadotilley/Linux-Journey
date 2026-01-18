### Redirecting Standard Output
**Standard output is represented by stdout** 
The concept of understanding standard I/O (input/output) is very important when learning the command line. When we input a command, the output is displayed on the screen. This is helpful of course, but what if I want to re-purpose that output for something else? That is where redirection comes into play. By redirecting the output of a command into a file, or even another command, we can boost our command-line efficiency. 

Here is an example of a file redirection:

`[ttilley@somelinux ~]$ ls -l /usr/bin > ls-output.txt`

We can then open that file in text editor, like Neovim, or use [[less]]. 

If we try to append something to the file using the above syntax however, it will delete the contents of the file. To avoid this, we will use the below syntax:

`[ttilley@somelinux ~]$ ls -l /usr/bin >> ls-output.txt`

Using the `>>` operator appends to the file, instead of overriding everything that was there originally. 

For the `>` operator, there is a cool trick that we can use. Just by using the `>` operator without a preceding command, we can **truncate** a file, or create a file if it does not already exist. 

`[ttilley@somelinux ~]$ > output.md 

### Standard Error
If we want to send the error output of a command to a file, we cannot use the syntax of the standard output. This is because the the standard error output uses a different stream. That is why it still goes to the screen. 

Redirecting standard error is not as easy, due to its lack of a simple operator like the `>`. This is where we must reference its file descriptor. In this case, it would be a 2. The syntax would look something like this:

`[ttilley@somelinux ~]$ ls -l /bin/usr 2> ls-error.txt`

If we want to redirect both at the same time, it would look something like this:

`[ttilley@somelinux ~]$ ls -l /bin/usr > ls-error.txt 2>&1`

**Important Note!!! The redirection must always follow this order!!!** 

### A Simpler Way
There is a more streamlined version of this, using a newer version of 'bash':

`[ttilley@somelinux ~]$ ls -l /bin/usr &> ls-output.txt` 

The same, of course, would also apply to appending a file, like this:

`[ttilley@somelinux ~]$ ls -l /bin/usr &>> ls-output.txt` 


--- 

### Disposing of Unwanted Output

We can dispose of unwanted output by sending it to a file called `/dev/null`. This acts as a black hole for all unwanted output. `/dev/null` is also referred to as the "bit bucket". It is written like this:

`[ttilley@somelinux ~]$ ls -l /bin/usr 2> /dev/null`  

---

### Redirecting Standard Input


For the command [[cat]], we can use it to redirect standard input. This is done by the following syntax:

`ttilley@somelinux ~]$ cat < sometext.txt`

By using the `<` operator, we are changing the source of the standard input from the keyboard to the file. In this case, the file was created on the spot, and then the input was taken and given to us by the `cat` command. 

---

### Pipelines

This is a fundamental part of redirection. If we use the `|` (pipe) operator, the standard output of a command is 'piped' to the standard input of another. The following syntax accomplishes this:

`[ttilley@somelinux ~]$ ls -l /usr/bin | less` 

This is very useful when searching for files, text strings within files, etc. 

*I will leave this screenshot from The Linux Command Line, by William Shotts:*
![[Pasted image 20251214232514.png]]

---

### Filters

The `|` operator can be used to 'Filter' out other outputs from other commands used in a sequence. This is very handy as well:

`[ttilley@somelinux ~]$ ls -l /usr/bin | sort | less`

Filtering commands change the output in some way, and use that as their output. In the above example, we have sorted the output to make better since of it. For another example, we have the [[uniq]] command. This command displays a list of the contents of the file. If we use it in our 'pipeline', it would look something like this:

`[ttilley@somelinux ~]$ ls /bin /usr/bin | sort | uniq | less`



