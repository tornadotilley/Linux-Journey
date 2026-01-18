When the system starts, the kernel starts the init.init system, which then starts **systemd**. Systemd manages all of the background processes in the system, many called *daemons*. The kernel then maintains information about all of these by assigning them a process ID (PID). For more information, check out the [[SystemD Foundations]] article.

When we want to view the processes running on our system, we can use the [[ps]] command with the 'x' option. 
```
[ttilley@somelinux ~]$ ps
		PID TTY        TIME CMD
	   2925	pts/0  00:00:00 fish
	  12981 pts/0  00:00:00 ps 
```
For this output, we get a some strange output that we need to interpret:

- PID - Process ID
- TTY - Controlling terminal
- TIME - Refers to CPU time
- CMD - The related command
With the '**x**' option, we get a new field, called STAT.
- STAT - Refers to the state of the process. 
	- R - Running
	- S - Sleeping
	- D - Uninterruptible sleep
	- T - Stopped
	- Z - Zombie process
	- < - High priority process
	- N - Low priority process

