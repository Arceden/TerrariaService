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

# Enable auto startup (optional)
$ systemctl enable terraria
```

### Local bin
It is recommended to make a symbolic link in the local bin in order to use the terraria service comands.
```bash
# Create symbolic link for the local bin
$ ln -s /opt/TerrariaService/terraria /usr/local/bin/terraria

# Example usage
terraria help
```

### Validate files
Before starting the service, run the following command to avoid problems with missing files or wrong permissions. If it does not work, try fixing it manually with ```chown```.
```bash
# Validate server en service files
$ service terraria checkfiles
```

## Usage
Available commands
Command|Description
-|-
start|Starts the server
stop|Stops the server
save|Saves the server if active
exit|Saves the world and stops the server
checkfiles|Validates the service and server files
state|Displays the server state
kill|Kills the server process
help|Shows the help message
