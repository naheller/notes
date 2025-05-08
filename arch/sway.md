# sway window manager

wayland displayer server installed by default

## install swayvm
- needs systemd-login (already installed) and polkit

install polkit
- no further config needed (?)

install sway, foot, wmenu

copy sway config from /etc/sway/config to ~/.config/sway/config

copy font config from /etc/xdg/foot to ~/.config/foot/foot.ini 
- update font size

## start sway on login (nate user only)
add to .bash_profile:

if [-z "$WAYLAND_DISPLAY"] && [-n "$XDG_VTNR"] && ["$XDG_VTNR" -eq 1] ; then
exec sway
fi

## sway bar
update font in sway bar in ~/.config/sway/config:

in bar section, add "font pango:monospace bold
- just boldens existing font (i guess monospace is default) but adding a size seems to cause a different font *style* to display (i.e. monospace 11 bold)

either way, only top bar (which is using i3status) and workspace number tabs seem to be affected. the window titles are still not bold.

decided to switch from i3status to i3blocks for better default bar info:
- pacman -S i3blocks
- pacman -Rs i3status (-Rs removes package and unused deps)

in ~/.config/sway/config, update status_command to use i3blocks

add battery etc to i3blocks:
- copy /etc/i3blocks.conf to ~/.config/i3blocks/config
  - i3blocks-contrib repo has examples
- add entry:

```
[battery]
label=DIS
command=awk '{print $1 "%"}' /sys/class/power_supply/BAT0/capacity
interval=10

[discharge]
label=BAT
command=awk '{print $1*10^-6 " W"}' /sys/class/power_supply/BAT0/power_now
interval=10
```

note: without acpi, can check battery values directly in the /sys/.../BAT0 directory

### Time and date

```
[date]
#command=date '+%Y-%m-%d %H:%M:%S'
command=date '+%a %b %d'
interval=10

[time]
#command=date '+%Y-%m-%d %H:%M:%S'
command=date '+%I:%M %p'
interval=10
```

## Screen locker

1. Install `swaylock` package
2. Added keyboard shortcut $mod+x for locking screen in sway config

## Idle handler

1. Install `swayidle` package
2. Uncommented the existing swayidle example config in `~/.config/sway/config`, which does the following:
  - This calls `swaylock -f -c 000000` after 300 sec (5 min)
  - Turns off external displays (TODO: Understand how swaymsg works)
  - Locks screen before sleep (DONE: Implement sleep on idle)

