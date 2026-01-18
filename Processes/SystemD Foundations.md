*This is, by no means, a comprehensive guide on Systemd. This is just a page of notes that I have found useful in my learning.* 

Systemd is the init system on many Linux systems. It's job is to initialize the system and schedule the other processes that run in the background. It will always have a PID (Process ID) of 1, or PID1. The first thing to understand about systemd are ~={red}Units=~. 

#### Commands
- `[ttilley@somelinux ~]$ systemctl status [service name]` - checks the status of the service
- `[ttilley@somelinux ~]$ sudo systemctl start [service name]` - starts a service
- `[ttilley@somelinux ~]$ sudo systemctl stop [service name]` - stops a service
- `[ttilley@somelinux ~]$ sudo systemctl restart [service name]` - restarts a service
- `[ttilley@somelinux ~]$ sudo systemctl enable [service name]` - enables a service to start when the system starts 
- `[ttilley@somelinux ~]$ sudo systemctl disable [service name]` - disables a service from starting automatically


### Units

Units are resources that systemd is able to manage. This covers a broad spectrum, from services, to timers, to mounts, etc. There are many resources that can be managed by systemd. 

#### Services
Services are what they sound like, services. They are what are going on in the background. This includes SSH, Apache Web Server, etc. They all have what is called a .service file. 

#### Checking the Status of a Service

If we need to check the status of a service, then we should use the command; `systemctl status [service]`. The output would look something like this:
```
○ httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled; preset: disabled)
    Drop-In: /etc/systemd/system/httpd.service.d
             └─hardening.conf
     Active: inactive (dead)
       Docs: https://httpd.apache.org/docs/2.4/
```

This output means that the service is disabled and inactive. Disabled/Enabled indicates whether the service starts when the system starts. Active/Inactive indicates whether the service is running or not. The default status of each service will be determined by the distribution. 

### Service Files

Now, we will talk a bit about unit files. These are files that pertain to anything that systemd can manage. For all of the unit files, they have an extension that identifies them; .service for service, etc. These are just text files that tell systemd what to do with the service. There are three different systemd unit directories:

1. `/etc/systemd/system`  
2. `/run/systemd/system`
3. `/lib/systemd/system` 

These directories are organized in order of priority. The highest priority of these is the first, `/etc/systemd/system`. When a unit is installed, the default configuration will be stored in the `/lib/systemd/system` directory. If a change is made to the `/etc/systemd/system`, that change will take priority. It seems to me that, the best practice would be to keep the `/lib/systemd/system` as they are, and only change the `/etc/systemd/system` if I were to want to change the configuration.

#### Inside the Service Files
There are three sections to a service file. They are `[Unit]`, `[Service]`, and `[Install]`. These files are case-sensitive, and editing them is not advised unless you know what you are doing. **Always make backups!!!**. Below, I will go into the specific fields of the different sections. 

```
[Unit] #the general metadata
Description= #just a general descrioption of the file
Wants= #prerequisite for the process to start
After= #services that start after, and specifies the order
Documentation= #where the documentation lives

[Service] #the execution logic
Type= #the startup behavior of the process
ExecStart= #the path to the script that starts the service
User=/Group= #which user or groups under which the process should run
Restart= #if the process should restart automatically
Environment= #to set the environement variables

[Install] #enable or disable a behavior
WantedBy= #which "target" should trigger this device
Alias= Provides alternative names for the service
```

This would be an example .service file:
```
[Unit]
Description=Network Manager Wait Online
Documentation=man:NetworkManager-wait-online.service(8)
Requires=NetworkManager.service
After=NetworkManager.service
Before=network-online.target

[Service]
# `nm-online -s` waits until the point when NetworkManager logs
# "startup complete". That is when startup actions are settled and
# devices and profiles reached a conclusive activated or deactivated
# state. It depends on which profiles are configured to autoconnect and
# also depends on profile settings like ipv4.may-fail/ipv6.may-fail,
# which affect when a profile is considered fully activated.
# Check NetworkManager logs to find out why wait-online takes a certain
# time.

Type=oneshot
ExecStart=/usr/bin/nm-online -s -q
RemainAfterExit=yes

# Set $NM_ONLINE_TIMEOUT variable for timeout in seconds.
# Edit with `systemctl edit NetworkManager-wait-online`.
#
# Note, this timeout should commonly not be reached. If your boot
# gets delayed too long, then the solution is usually not to decrease
# the timeout, but to fix your setup so that the connected state
# gets reached earlier.
Environment=NM_ONLINE_TIMEOUT=60

[Install]
WantedBy=network-online.target

```

### Overriding and/or Editing .Service Files

There some situations in which one will want to edit configurations for systemd. There is a command for editing service files. It is as follows:

`sudo systemctl edit [service file name]`
- There is no need to give the path for the service file, because systemd already knows where it lives. 
This command takes you straight to a .override file to edit. This is because of the priority of the file. Anything found in that file will be top priority. If you wish to undo the changes at a later date, you can simply delete the file and restart the service. 

Below the start of the file, you will find a commented out version of the original file. This is for your reference while you are editing the file. When editing the file, you must edit above the point that says `#Edits below this line will be commented out`. You will write the section, `[Unit]`, and make the changes under that. 

There is another option for this command: `sudo systemctl edit --full [service name]`. This will give you the entire file as the base. When saved, there will be a copy made, and stored in the `/etc/systemd/system`. To make sure that the changes take effect, we will need to enter the command: `suod systemctl daemon-reload`. This will reload the running configuration. 





---
*Sources :*
1. *From 'Learn Linux TV' on Youtube*
	https://youtu.be/Kzpm-rGAXos?si=uQrSZDgI8jeVeTOk
2. *Google Gemini*
