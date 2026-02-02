`userdel` lets us delete a user from the system. The syntax is very simple:
```
[ttilley@somelinux ~]$ sudo userdel -r dani
```

`userdel -r` will delete the user from the system and from `/etc/shadow` (which has all of the passwords)