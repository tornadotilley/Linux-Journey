`lsblk` stands for list block. This refers to storage blocks. In its default form without arguments, it shows us our storage options and how much space is on each.
```
[ttilley@somelinux ~]$ lsblk  
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINTS  
sda 8:0 0 111.8G 0 disk  
├─sda1 8:1 0 976M 0 part /boot/efi  
│ /  
└─sda3 8:3 0 14.9G 0 part [SWAP]  
sdb 8:16 0 931.5G 0 disk  
├─sdb1 8:17 0 922.2G 0 part /home  
└─sdb2 8:18 0 9.3G 0 part  
sr0 11:0 1 1024M 0 rom  
Next, we’ll reinsert the flash drive and run lsblk again:  
[ttilley@somelinux ~]$ lsblk  
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINTS  
sda 8:0 0 111.8G 0 disk  
├─sda1 8:1 0 976M 0 part /boot/efi  
│ /  
└─sda3 8:3 0 14.9G 0 part [SWAP]  
sdb 8:16 0 931.5G 0 disk  
├─sdb1 8:17 0 922.2G 0 part /home  
└─sdb2 8:18 0 9.3G 0 part  
sdc 8:32 1 3.8G 0 disk  
sr0 11:0 1 1024M 0 rom  
We now see a new device (sdc) has been added to the list. The device name will remain  
the same as long as it remains physically attached to the computer and the computer is  
202
```
