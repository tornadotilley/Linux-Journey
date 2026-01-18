`ps` by default, shows us the processes running for our user only. 
```
[ttilley@somelinux ~]$ ps
		PID TTY        TIME CMD
	   2925	pts/0  00:00:00 fish
	  12981 pts/0  00:00:00 ps 
```

We can use different options, we get different outputs:
*A quick note: There are two styles of these commands, GNU and BSD. We will be using the BSD style, which does not include a dash.
- x - shows all of our processes running on the system
- ax - lists all running processes
- w - shows full command names
- u - verbose
- aux - shows all processes by every user
