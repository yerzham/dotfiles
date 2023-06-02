# How to make Waylock work with Hyprland

### Lock on sleep

Executable `waylock_wrapper`:
```
#!/bin/sh

export XDG_RUNTIME_DIR=/run/user/$(id -u)
echo $XDG_RUNTIME_DIR
export WAYLAND_DISPLAY=wayland-1

waylock -fork-on-lock
```

Sleep hook service at `/etc/systemd/system/sleep@.service`:
```
[Unit]
Description=Lock the screen
Before=sleep.target

[Service]
User=%I
Type=forking
ExecStartPost=/usr/bin/sleep 1
ExecStart=<path to waylock_wrapper>

[Install]
WantedBy=sleep.target
```

Enable the hook service for the user:
```
$ sudo systemctl enable sleep@<user>
```
