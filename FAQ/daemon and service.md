
__What is a __Process?__

__What is Daemon?__

A daemon is a background, non-interactive program. It is detached from the keyboard and display of any interactive user. The word daemon for denoting a background program is from the Unix culture; it is not universal.

A daemon is a computer program that runs as a background process, rather than being under the direct control of an interactive user.

__What is a Service?__

A service is a program which responds to requests from other programs over some inter-process communication mechanism (usually over a network). A service is what a server provides. For example, the NFS port mapping service is provided as a separate portmap service, which is implemented as the portmapd daemon.

A service doesn't have to be a daemon, but usually is. A user application with a GUI could have a service built into it: for instance, a file-sharing application.

That name comes from Client Server Model. It means that an application runs as a service on a server, and a client version of the application is used to access the service. For example an Apache HTTP server application is a service on a server and a Chrome Browser is a client on a PC.


### Video 
a process is the command that gets run 


https://askubuntu.com/questions/192058/what-is-technical-difference-between-daemon-service-and-process

[How to Create a Daemon on Linux](https://www.makeuseof.com/create-daemons-on-linux/)
[Creating a Linux service with systemd](https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6)
[How to create a systemd service in Linux](https://linuxhandbook.com/create-systemd-services/)
