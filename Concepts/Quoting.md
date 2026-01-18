Taking what we learned from [[Expansion]], let's now learn about quoting in 'bash'. Quoting lets us suppress whatever expansions are unwanted. Imagine if we wanted to to echo a dollar amount into a file, but the shell took it as a variable. That would be very limiting. Fortunately, we can put the text in quotes, letting the shell know that the input is just a string to go into a file.

```
[ttilley@somelinux ~]$ echo The total is $100.00
The total is 00.00
```

```
[ttilley@somelinux ~]$ echo 'The total is $100.00'
The total is $100.00
```

Before going out there and trying to put quotes on everything, you should be aware that there are two kinds of quotes, double and single. What's more, they accomplish different things. 
## Double Quotes

Double quotes allow us to almost all of the special characters lose their meaning. The exceptions are `$`, `\`, and the back-quote **(Obsidian will not let me write that character)**. This can allow us to work with files that have embedded spaces in the middle. Double quotes also preserves spaces, so that strings have the correct amount of spaces in them. 

```
[ttilley@somelinux ~]$ echo "How much    money?"
How much    money?
```

Now, we can use our knowledge of expansion to do something really cool! If we look at the following example, we will see.

```
[ttilley@somelinux ~]$ echo $(df -h)
Filesystem Size Used Avail Use% Mounted on tmpfs 1.6G 2.0M 1.6G 1%
/run /dev/sda2 94G 19G 71G 21% / tmpfs 7.8G 0 7.8G 0% /dev/shm tmpfs
5.0M 4.0K 5.0M 1% /run/lock /dev/sda1 975M 6.1M 969M 1% /boot/efi
/dev/sdb1 907G 574G 287G 67% /home tmpfs 1.6G 1.8M 1.6G 1%
/run/user/1000
```

```
[ttilley@somelinux ~]$ echo "$(df -h)"
Filesystem
Size Used Avail Use% Mounted on
tmpfs
1.6G 2.0M 1.6G
1% /run
/dev/sda2
tmpfs
tmpfs
/dev/sda1
/dev/sdb1
tmpfs
94G
7.8G
5.0M
975M
907G
1.6G
19G
0
4.0K
6.1M
574G
1.8M
71G
7.8G
5.0M
969M
287G
1.6G
21% /
0% /dev/shm
1% /run/lock
1% /boot/efi
67% /home
1% /run/user/1000
```

With the first example, `echo` took 49 arguments and just gave us one long string containing all of them. With quotes around the expansion, the command line saw that there was just one argument. Super neat!!!


## Single Quotes

With single quotes, it is much simpler. single quotes block all expansion. What is written within single quotes is what is printed to the terminal.
```
[ttilley@somelinux ~]$ echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER'
text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
```

## Escaping Characters

If we only want to qute a single character, we can use an escape character in front of a character that might otherwise cause an expansion (A special meaning in the shell). This is done by putting a `\` in front of the character. I do this all of the time when I want to make a filename that has a space in it. Below are some examples:

```
[ttilley@somelinux ~]$ echo "The balance for user $USER is: \$5.00"
The balance for user ttilley is: $5.00
```

Here, the shell would have recognized the `$` as a variable, instead of part of the string. With the inclusion of the `\`, we told the shell that we wanted it to recognize this particular character as only part of the text string. We can also use this technique to add characters to filenames, such as spaces, `$`, `!`, `&`, and many others. We can even include the same backslash character by typing `\\`. Bellow is a table taken from 'The Linux Command Line', detailing more backslash escape sequences. Some are the same as in python. 

![[Pasted image 20251221122535.png]]
