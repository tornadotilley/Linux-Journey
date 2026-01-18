*This article will function as a landing page that will link all of the file directories in my note taking.*

The Linux file system is uses a ==hierarchical directory structure==. At the top, there is the root directory. It is represented by `/`. More information can be found in the flowchart:
[[The Linux File System Structure.canvas|The Linux File System Structure]]


There are some files that begin with a `.`, eg.: `.config`, `.bashrc` 

Here is a list of directories:
- `/` - the parent of all directories.
	- [[root]] `/root` - the home directory of the root user
	- [[bin]] `/bin` - binary directories where many executable programs live 
		- example - `ls`, `cp`, `mv` 
	- [[boot]] `/boot` - ==device files== that represent hardware and pseudo-devices
		- examples - `sda1`, `null`, `zero`
	- [[dev]] `/dev` - 
	- [[etc]] `/etc` - ==configuration files== live here
		- examples - `passwd`, `fstab`
	- [[home]] `/home` - the user home directories live here
		- `/home/user`
	- [[lib]] `/lib` - the shared libraries live here, needed by the [[bin]] and the and the [[sbin]]. 
	- [[media]] `/media` - the mount points for removable media
	- [[mnt]] `/mnt` - contains the mount points for the temporary media 
	- [[opt]] `/opt` - optional software packages
	- [[proc]] `/proc` - virtual files that provide information about the processes running on the system
	- [[run]] `/run` - these are temporary files that are cleared on reboot 
		- referred to as **run-time variables**
	- [[usr]] `/usr` - this is where the installed **software and program libraries live** 
		- multi user applications live here 

### Child Directories
Any of the directories contained within another directory is a child directory. 

### Top-Level Directories
The top-level directories are the directories under the `/` directory. These contain two types of data, **static** and **variable/dynamic**. These two can be defined as below:
- Static Data - data that cannot be modified, unless explicitly done so.
- Variable/Dynamic - data that can be modified as needed by various system processes. 
- Persistent - data that remains after a reboot.
- Runtime - data from a process that or the system that is deleted on reboot. 

