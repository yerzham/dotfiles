# Theming

### GTK theming with Wayland

#### Install the themes:

https://github.com/vinceliuice/Graphite-gtk-theme

`./install.sh -t teal`

https://github.com/vinceliuice/Tela-circle-icon-theme

`/install.sh manjaro`

#### Configuration

`.gtkrc-2.0`:
```
gtk-theme-name = "Graphite-teal:dark"
```
`.config/gtk-3.0/settings.ini`:
```
[Settings]
gtk-theme-name = "Graphite-teal:dark"
```

Set `GTK_THEME` environment variable to `Graphite-teal:dark` too.

Use `gsettings(1)` for setting the icon theme:
```
$ gsettings set org.gnome.desktop.interface icon-theme Tela-circle-manjaro
```
