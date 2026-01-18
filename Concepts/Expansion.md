*From an LLM*
"Expansion is the process where the shell transforms parts of a command line into more specific or complex forms before executing the command."

*My words:*
I like to think of this as though it were a human language, or even a programming language. Just as a word in a sentence can have a completely different context based on the words around it, the same concept applies to BASH. Look at the following example:

```
[ttilley@somelinux ~]$ echo some words
some words
```

```
[ttilley@somelinux ~]$ echo *
Desktop Documents Music Pictures Public Templates Videos
```

Instead of echoing the `*` character, it 'expanded' the meaning into something else. A wildcard is used to list or copy all of the files in the directory, and it functions the same right here. 

- This works by using **pathname expansion**. Another example of expansion is the `~` symbol. When using this symbol, it expands into the [[home]] directory of the user. 

- For more symbols that can be expanded, check out the [[Wildcards]] article. There are many of them that would be very useful to anyone there. 

Another concept is **arithmetic expansion**. This is just a way of saying that the shell can do math. The syntax is as follows:

`[ttilley@somelinux ~]$ echo $(( 2+2 ))` 

There are other operators for different arithmetic operations. 
![[Pasted image 20251220174424.png]]

### 
We will now cover **brace expansion**. For you to see what it is, here is an example:

```
[ttilley@somelinux ~]$ echo Front-{A,B,C}-Back`
Front-A-Back Front-B-Back Front-C-Back
```

It is essentially a list of strings or integers that do not contain any whitespace. There are some pretty cool things that we can do with this, like go through a list of number, like in python. 

```
[ttilley@somelinux ~]$ echo Number_{1..5}
Number_1 Number_2 Number_3 Number_4 Number_5
```

The leading portion in the pattern, is called the *preamble*, the later being called the *postscript*. From bash version 4.0, integers can be 0 padded as well. It looks like this `{01..15}`. 

The order can be reversed if you choose to order it that way. It might look like this:

```
[ttilley@somelinux ~]$ echo {Z..A}
Z Y X W V U T S R Q P O N M L K J I H G F E D C B A
```

There are also nested brace expansions:
```
[ttilley@somelinux ~]$ echo a{A{1,2},B{3,4}}b
aA1b aA2b aB3b aB4b
```

This is really cool, but you may have one question... When do I use this??!! Fortunately, Mr. Shotts has given us a great use-case. If we would like to make many directories at once, that follow a specific format, we could use:

```
[ttilley@somelinux ~]$ mkdir Photos
[ttilley@somelinux ~]$ cd Photos
[ttilley@somelinux Photos]$ mkdir {2007..2009}-{01..12}
[ttilley@somelinux Photos]$ ls
2007-01 2007-07 2008-01 2008-07 2009-01 2009-07
2007-02 2007-08 2008-02 2008-08 2009-02 2009-08
2007-03 2007-09 2008-03 2008-09 2009-03 2009-09
2007-04 2007-10 2008-04 2008-10 2009-04 2009-10
2007-05 2007-11 2008-05 2008-11 2009-05 2009-11
2007-06 2007-12 2008-06 2008-12 2009-06 2009-12
```

Now, we will be covering **parameter expansion**. This is referring to variables. Because we are already familiar with python, we know what that is. Basically, a variable is a small chunk of data that the computer can store in memory. We can see a list of available variables like this:

`[ttilley@somelinux ~]$ printenv | less`

Let's now go onto **command substitution**. This allows us to use the output of a command as an expansion. 

```
[ttilley@somelinux ~]$ echo $(ls)
Desktop Documents ls-output.txt Music Pictures Public Templates
Videos
```

```
[ttilley@somelinux ~]$ ls -l $(which cp)
-rwxr-xr-x 1 root root 71516 2007-12-05 08:58 /bin/cp
```

This technique can also be used in pipelines

```
[ttilley@somelinux ~]$ file $(ls -d /usr/bin/* | grep zip)
/usr/bin/bunzip2:
symbolic link to `bzip2'
/usr/bin/bzip2:
ELF 32-bit LSB executable, Intel 80386,
version 1 (SYSV), dynamically linked (uses shared libs), for
GNU/Linux 2.6.9, stripped
/usr/bin/bzip2recover: ELF 32-bit LSB executable, Intel 80386,
version 1 (SYSV), dynamically linked (uses shared libs), for
GNU/Linux 2.6.9, stripped
/usr/bin/funzip:
ELF 32-bit LSB executable, Intel 80386,
version 1 (SYSV), dynamically linked (uses shared libs), for
GNU/Linux 2.6.9, stripped
/usr/bin/gpg-zip:
Bourne shell script text executable
/usr/bin/gunzip:
symbolic link to `../../bin/gunzip'
/usr/bin/gzip:
symbolic link to `../../bin/gzip'
/usr/bin/mzip:
symbolic link to `mtools'
```

