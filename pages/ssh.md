# SSH

With few exceptions, any bash shell commands you learn can be run on another machine / computer you connect to. `ssh` (secure shell protocol) is a ubiquitous protocol for connecting to other machines remotely. Here is the basic pattern for establishing a connection:

## standard (explicit) connection

`[sudo] ssh user@ip [-p PORT]`, where `sudo` *may* be required, {user} is the username, {ip} is the IP address, and PORT is the optional port number. In all cases (username, IP, port), they should be the values from the *other* machine, not from *your* machine. Example:

`sudo ssh john@78.324.122.6 -p 4667`

## configured connection

To avoid typing details every time, you can create an ssh directory on your computer `mkdir -p ~/.ssh`, create a 'config' file `touch ~/.ssh/config`, and write the details in that config file:

```bash
Host example-computer
  HostName 78.324.122.6
  User john
  Port 4667
```

## demo connection

![ssh](../assets/ssh.gif)

# Utility

Being able to connect to any computer (even headless machines without a screen / keyboard) and control is via the command line is a very powerful tool. Some users learn the command line specifically to better work with remote machines in this way.