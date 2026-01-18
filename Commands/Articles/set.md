`set`, without any arguments, shows us the shell and environment variables. The output is in alphabetical order. The set command allows us to manage shell behavior. 
```
[ttilley@somelinux ~]$ set
```

In shell scripting, there are several flags that are common:
- **-e** - stops the execution of a script if any command fails
- **-x** - prints every command to the terminal before executing, so that we can see what the script is doing
- **-u** - treats unset variables as an error
One of the most popular starting lines for bash scripting is:
`set -euxo pipefail`
