`su` lets us log in as another user. The syntax looks like this:

```
[ttilley@somelinux ~]$ su [-l] [user]
```

When we use the `-l`, we will be logged into another user's shell. 

We can also execute a command from another user account by using this syntax:
```
[ttilley@somelinux ~]$ su -c 'command'
```

`su` is largely deprecated, losing favor to to [[sudo]]. j