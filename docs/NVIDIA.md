# How to work with Nvidia

### Loading nvidia drivers early
https://wiki.archlinux.org/title/NVIDIA#DRM_kernel_mode_setting

Important for everything else.

### Configure for Hyprland
https://wiki.hyprland.org/Nvidia/

In `hyprland.conf`:
```
env = LIBVA_DRIVER_NAME,nvidia
env = XDG_SESSION_TYPE,wayland
env = GBM_BACKEND,nvidia-drm
env = __GLX_VENDOR_LIBRARY_NAME,nvidia
env = WLR_NO_HARDWARE_CURSORS,1
```

Alternatively, set it for an executable wrapper (probably a better choice):
```
#!/bin/sh

cd ~

export XCURSOR_SIZE=24
export GTK_THEME=Adwaita:dark

export LIBVA_DRIVER_NAME=nvidia
export GBM_BACKEND=nvidia-drm
export __GLX_VENDOR_LIBRARY_NAME=nvidia
export WLR_NO_HARDWARE_CURSORS=1

exec Hyprland
```

And make a `.desktop` file for it under `/usr/share/wayland-sessions/`:
```
[Desktop Entry]
Name=WHyprland
Comment=An intelligent dynamic tiling Wayland compositor
Exec=<executable wrapper path>
Type=Application
```

### Hyprland suspend fix
https://wiki.archlinux.org/title/NVIDIA/Tips_and_tricks#Preserve_video_memory_after_suspend

Enable `nvidia-suspend.service` (and maybe also `nvidia-hibernate.service`) and add `/etc/modprobe.d/nvidia-power-management.conf`:
```
options nvidia NVreg_PreserveVideoMemoryAllocations=1
```
