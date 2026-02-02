`useradd` lets us add another user to the machine. This command needs to be used with `sudo`. 
```
[ttilley@somelinux ~]$ sudo useradd dani
```

A great way to use this command is to add the a home directory and the default user shell, by using the -m and -s commands at the same time.

```
[ttilley@somelinux ~]$ sudo usermod -m -s /bin/bash dani
```