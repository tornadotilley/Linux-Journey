SSH is a great way to connect to remote systems because it is an encrypted protocol. Its default port is 22. if there is ever any trouble with ssh, like an ip address change, then the following command might be very helpful:

```
[ttilley@somelinux ~]$ **``ssh-keygen -R some_remote_system -f ~/.ssh/known_hosts``**
# Host remotesystemname found: line 12
/home/user/.ssh/known_hosts updated.
Original contents retained as /home/user/.ssh/known_hosts.old
```