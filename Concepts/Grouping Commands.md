Grouping commands is a great way to save some time and space. It can be used in tandem with [[Redirection]]. We make a list of the commands that we want to execute, with all of the output from all of the commands going to one single file. 
Example:
`[ttilley@somelinux ~]$ { command1; command2; command3; } > logfile.txt`

For the syntax, the curly brackets need the whitespace around them. The final command must be terminated with either a `;`  or a `\`. 