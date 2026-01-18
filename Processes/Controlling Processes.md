When we launch a program from the terminal, the process usually takes the terminal session away from us. Here are a few tricks and keyboard shortcuts that will help with that:
- Launch the program followed by &:
	- `[ttilley@somelinux ~]$ steam &`
	- This can also be done with multiple programs
- Using the [[fg]] command, followed by the '%' is, followed by the job number will return the process to the foreground.
- CTRL+Z - pauses the program
- CTRL+C - stops the program

### Background Processes
When a process gets put into the background, it becomes a job. We can see these processes by using the [[jobs]] command. 

### Process Priority
We can change the process priority, which is how much CPU that a process can use. We can use the [[nice]] command to launch a program with a specific priority, and the [[renice]] command to readjust the priority of a program that is already running. -20 is the most favorable and 19 is the least favorable. 