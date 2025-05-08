# power management

## TLP

- install via pacman
- enable/start service
- config at /etc/tlp.conf
- uncomment BAT0 threshold lines

## power-profiles-daemon

switched to this from TLP because it seems more lightweight, and is used by EndeavourOS

also switched over because TLP was locking up the system when it tried to reboot, while I was investigating a [[slow-startup.md]].

- includes upower as a dependency
- must manually install `python-gobject` dependency in order to use `powerprofilesctl` CLI tool
- then run `systemctl [unmask, start, enable] power-profiles-daemon`

once installed, run `powerprofilesctl` to see currently active power profile
- initially set to "balanced"
- to set (and keep) "power saver" instead:
  - run `powerprofilesctl set power-saver`
  - on first set, creates file: `/var/lib/power-profiles-daemon/state.ini`
  - need to verify chosen profile persists between boots (verified)


## upower

this was installed as a dependency by ppd. i may be able to use this to output battery discharge rate to the sway bar. 
