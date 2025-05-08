# Slow startup experience

Noticed that startup time was taking longer than expected. 30 sec firmware.

Went into bios and moved SSd to #1 in boot order
- also disabled bluetooth, microphone, camera, io, but haven't verified change
- turned on ecure boot, but then arch failed to load, so disabled again.
- enabled something like "kernel DMA" just for fun
  - haven't verified/noticed any behavior changes attributable to this

After boot order update, boot time much faster, subjectively.
- However, unable to run `systemd-analyze` becayse TLP service was still running as part of the boot process. unable to stop with `systemctl stop tlp.service`
- reboot appears stuck waiting for TLP
  - can see shutdown process trying to kill TLP
- had to hard shutdown with button
- same issue on next boot; disabled TLP service
- issue ceased; able to verify faster boot

After above issue, removed TLP package and `/etc/tlp/conf.pacsave`. Replaced with power-profiles-daemon as detailed in [[power-mgmt.md]].

## WTF addendum

Noticed that TLP was still blocking shutdown even after package removal! On subsequent boot, system hung while loading up arch.
- Fixed by reenabling io devices in BIOS
- TLP no longer blocking shutdown 
  - Actually suspect that TLP was not the issue here

