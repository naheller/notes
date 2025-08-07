# fonts

Fonts are typically installed at:

Manually installed:
Single user: ~/.local/share/fonts/
All users: /usr/local/share/fonts/

Installed via package manager (don't edit directly):
All users: /usr/share/fonts

Package manager method is recommended for easy update/removal.

## since using archinstall script

Initially using basic system monospace font. This was set in both the configs for foot and for waybar. It also looks like Firefox and Brave may have installed some fonts and icons as deps.

## waybar icons

Waybar css suggests using FontAwesome for icons.

- To install: pacman -S otf-font-awesome
- Pacman put the font at /usr/share/fonts
- Used FA in waybar css

In order to use the icons with battery, for example, update the battery section of the waybar config:

```
"format": "{icon} {capacity}%",
"format-icons": ["\uf243","\uf242", "\uf240"]
```

## back in the day: manual arch install

on first successful boot
- view system fonts: cat /usr/share/kbd/consolefonts
- change font: setfont <font-name>
- persist font: /etc/vconsole.conf >> FONT=sun12x22

...but none of the fonts were big enough
