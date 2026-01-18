_This is the article for [alias](app://obsidian.md/alias)_  
`alias` allows us to create our own commands. If we were to enter three separate commands on the same line, that would be a lot of typing. With aliasing, we can make all of those one word. The syntax would look something like this:

`[ttilley@somelinux ~]$ alias goo='cd /usr; ls; cd -`

To execute all of these commands at one time, we now only have to enter the command:

`[ttilley@somelinux ~]$ goo`

To remove an alias, use the following syntax:

`[ttilley@somelinux ~]$ unalias goo`

**A note about aliasing!!!** Aliasing this way only lasts until the shell session is closed. After that, all will be removed. Soon, we will be going over how to make permanent changes.

- For further reading, the _'Bash Reference Manual'_ is a great reference work.
    - [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
- _Bash FAQ_
    - [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)