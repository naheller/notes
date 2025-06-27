# system clock

docs: https://wiki.archlinux.org/title/System_time

## useful commands

- `hwclock --show`: view hardware clock. probably needs sudo prepended.
- `hwclock --systohc`: set hardware clock from software clock
- `timedatectl`: view software clock
- `timedatectl set-timezone <timezone>`: manually set timezone. example: America/New_York

## set timezone based on geolocation

1. use geolocation api: `https://ipapi.co/timezone`
2. pipe the output to set timezone command: `curl https://ipapi.co/timezone | timedatectl set-timezone`

## enable NTP 

Enter command `timedatectl set-ntp true`

NTP is the Network Time Protocol. Above command will enable a daemon that auto-syncs system time with a remote time server.

Note: Initially running this command did not seem to fix my time, but the time is now fixed. The only other command I ran was the time zone geolocation update.It could be that the clock refresh rate is slow enough that the update didn't reflect quickly enough for me to notice.
