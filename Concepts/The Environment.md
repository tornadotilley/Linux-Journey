The environment, in simple terms, is data that the shell stores. These can affect the way that programs run and the behavior of the system. These are mostly **shell variables**. We can see the current environment by using the [[printenv]] command. Using this, we can see all of the variables that the shell has stored. 
```
[ttilley@somelinux ~]$ printenv
```
For a sorted output, you can also use the [[set]] command:
```
[ttilley@somelinux ~]$ set | less
```
There are two kinds of data in the environment, **environment variables** and **shell variables**. The shell variables are for the current instance of bash, while the environment variables are everything else. There are many variables that are interesting;
![[Pasted image 20251229223520.png]]
![[Pasted image 20251229223547.png]]
There are two kinds of shell sessions, login and non-login. 
- login - when we are prompted for our username and password
	- example - graphical environment, virtual console
	- the shell reads from these directories
	![[Pasted image 20251229224601.png]]
- non-login - when we are not 