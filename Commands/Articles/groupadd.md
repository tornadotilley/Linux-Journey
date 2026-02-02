`groupadd` lets us add groups to the system. 

```
[ttilley@somelinux ~]$ sudo groupadd newgroup
```

Using the -g option lets us specify the group id
```
[ttilley@somelinux ~]$ sudo groupadd -g 10000 newgroup
```

Using the -r option will let us create system groups, which pull the group id from the range of valid system id's. 
```
[ttilley@somelinux ~]$ sudo groupadd -r newgroup
```

