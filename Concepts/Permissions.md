Here will be the notes on permissions. This is a very important subject for security and deserves its own list of commands. 

- `id` - display user identity 
- `chmod` - change a files mode 
- `umask` - set the default file permissions
- `su` - run a shell as another user
- `sudo` - execute a command as another user
- `chown` - change a file's owner
- `chgrp` - change a file's group ownership 
- `addgroup` - add a user or group to the system
- `usermod` - modify a user account
- `passwd` - change a user's password

### Users, Groups, and Everybody Else

In Unix security, users have permissions and belong to groups. If a user does not own a file or belong to certain groups, the user cannot change some files. The user can choose if the files that they own can be shared with the group or with others. If you are curious about your usergroups, you can use the command `id`. 
### File Types

At the beginning of the `ls` output, we see 10 characters, that might look like this: ![[Pasted image 20251222195204.png]]. In this example, the first character identifies the type of file. In this case it is a d for directory. Below are the meanings of the most common tags. 
- `-` regular file
- `d` directory
- `l` symbolic link - followed by dummy values
- `c` special file 
- `b` block special file 


### File Permissions

| Type | User | Group | Other |
| ---- | ---- | ----- | ----- |
| d    | rwx  | rwx   | rwx   |

- **r** - refers to a file being able to be opened and read
	-  Allows a directories contents to be listed.
- **w** - allows a file to be written to and edited, but it does not allow for the removal of files. 
	- files can be created, deleted, and executed if the **x** is also present. 
- **x** - allows a file to be executed, such as a bash script. 
	- allows a directory to be entered and for the directory metadata to be accessed.

It is also important to understand the octal expression of permissions. Below will be a chart showing all of these values. 
![[Pasted image 20260101213424.png]]

For a file to have 777, means that all have access to do whatever they want to with the file. A standard file will have the value of 644. The owner of the file can read and write, and everyone else can read the file. A permission of 700 means that the owner has full permission and everyone else cannot even read the file.



