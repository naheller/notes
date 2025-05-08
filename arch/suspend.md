# Suspending the system

This happens when I close the laptop lid. I'd also like it to happen after X minutes of idle time.

## systemd config

Systemd should handle the low level stuff. Sway and swayidle can "hint" to systemd that a suspend should happen, but that's it. 

There's a config file at /etc/systemd/logind.conf with a couple relevant lines:

```
#IdleAction=ignore
#IdleActionSec=30min
```

Instead of uncommenting these, advice is to leave this file alone and create a personal override at /etc/systemd/logind.conf.d/suspend.conf

After adding these lines, need to adjust them as desired. Trying this:

```
IdleAction=suspend
IdleActionSec=15min
```

After making this change, need to restart the systemd-logind service with `sudo systemctl restart systemd-logind`

## sway config

Now sway needs to "hint" to systemd that we're in an idling state. Adding the following line to /.config/sway/config:

`exec swayidle idlehint 1`

But since there's already `exec swayidle ...` block in there, i'd add the new bit like this:

```
exec swayidle ... \
... \
... \
idlehint 1
```

Then need to log out and back in, since apparently `exec` lines only run on login.

TODO: Figure out difference between exec and exec-always
