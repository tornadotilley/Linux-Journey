`chmod` changes the permissions mode of a file or a directory. This uses octal or symbolic notation for changing the modes. This can be explained in the below table:


| Octal | Binary | File Mode |
| ----- | ------ | --------- |
| 0     | 000    | ---       |
| 1     | 001    | --x       |
| 2     | 010    | -w-       |
| 3     | 011    | -wx       |
| 4     | 100    | r--       |
| 5     | 101    | r-x       |
| 6     | 110    | rw-       |
| 7     | 111    | rwx       |
If we were to pass the argument 600, we would be granting only the user permission to read and write, and taking away permission from all other users and groups. 

![[Pasted image 20251222195936.png]]

We can also specify who is affected. If we do not pass an argument, then the shell assumes all. Using the `-` or `+`, we can assign or take away permissions. Using the = sign will also assign the specified permissions. 

![[Pasted image 20251223081138.png]]
