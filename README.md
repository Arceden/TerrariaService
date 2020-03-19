# TerrariaService
Service script for Terraria dedicated servers.
This service script lets you start, stop and save the server while running it in the background to avoid using programs like tmux and screen.

## Setup
Make sure that you have downloaded the dedicated terraria server from https://terraria.org before using the TerrariaService.

### Repository and configuration files
```bash
# Clone the repository to a directory such as /opt/
$ git clone https://github.com/Arceden/TerrariaService
$ cd TerrariaService/
```

```bash
# Copy the example files without the example extension and edit the files.
$ cp config.cfg.example config.cfg
$ cp terraria.service.example terraria.service
```

### Systemd setup
```bash
# Create symbolic link for systemctl
$ ln -s /opt/TerrariaService/terraria.service /etc/systemd/system/terraria.service
$ systemctl daemon-reload

# Test the service
$ systemctl status terraria
> Active: inactive (dead)
```

### Sysvinit setup
```bash
# Create symbolic link for service commands
$ ln -s /opt/TerrariaService/terraria.service /etc/init.d/terraria

# Test the command
$ service terraria state
> Server is offline
```

### Validate files
Before starting the service, run the following command to avoid problems with missing files or wrong permissions. If it does not work, try fixing it manually with ```chown```.
```bash
# Validate server en service files
$ service terraria checkfiles
```

## Usage
The start command can be used to start the server. The service will prompt to generate new files if any are missing, such as the serverconfig.txt file for the terraria server.
The automaticly generated serverconfig.txt will enable the terraria server setting "autogenerate" so that a world will automaticly be generated on startup if the world missing.


For more information about the commands, execute the help command.
```bash 
$ service terraria help
```
