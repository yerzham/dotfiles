# How to make SDDM work with Hyprland
https://wiki.archlinux.org/title/SDDM#Running_under_Wayland

While using `sddm-git` from AUR while `sddm` v0.20 is not released, put this in `/etc/sddm.conf.d/10-wayland.conf`:
```
[General]
DisplayServer=wayland
GreeterEnvironment=QT_WAYLAND_SHELL_INTEGRATION=layer-shell

[Wayland]
CompositorCommand=<path to hyprland wrapper or hyprland itself>
```
