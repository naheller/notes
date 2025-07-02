# power management

Update June 2025: Following the fresh archinstall, I'm no longer using PPD. Upower is still installed, however, as a dependency of waybar. This time I'll be trying cpu-autofreq. 

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

## auto-cpufreq

As of the June 2025 archinstall, I'll be trying out cpu-autofreq as a minimal power mgmt solution. It's on the [[aur]] and i've installed it using paru.

After install I need to enable the service with `systemctl enable --now auto-cpufreq` so it starts automatically.

Then, I created a config file at `~/.config/auto-cpufreq/auto-cpufreq.conf`, symlinked from my dotfiles repo. The contents of the config file were pasted from an example in the package github readme.

Running `sudo auto-cpufreq --monitor` pulls up a dashboard showing cpu and battery stats. It also seems to be using the settings defined in the config file I created. 
