*This is the article for [[alias]]*
`alias` allows us to create our own commands. If we were to enter three separate commands on the same line, that would be a lot of typing. With aliasing, we can make all of those one word. The syntax would look something like this:

`[ttilley@somelinux ~]$ alias goo='cd /usr; ls; cd -`

To execute all of these commands at one time, we now only have to enter the command:

`[ttilley@somelinux ~]$ goo` 

To remove an alias, use the following syntax:

`[ttilley@somelinux ~]$ unalias goo` 

### Making Permanent Aliases

Aliases are not permanent by default. If you want to alias a command for good, then you need to ad it to your .bashrc file. For example, if I want to alias `ls -la`, then I would add the following to my .bashrc file:
```
alias=
```

- For further reading, the *'Bash Reference Manual'* is a great reference work. 
	- http://www.gnu.org/software/bash/manual/bashref.html
- *Bash FAQ*
	- http://mywiki.wooledge.org/BashFAQ
