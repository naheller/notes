make IWD provide DHCP functionality:

file: /etc/iwd/main.conf

[General]
EnableNetworkConfiguration=true

[Network]
NameResolvingService=systemd

(Network section should be optional since systemd is default)

start IWD service:
- systemctl start iwd.service

ACCESS DENIED! sudo not installed
- couldn't install sudo because no internet
- start IWD as root, connected to network
- SSIDS/passwords stored in /var/lib/iwd

show running services:
- systemctl --type=service --state=running

...connected to internet, but

- able to ping 1.1.1.1, but not google.com
- DNS not set up, systemd used by default, but service wasn't started
  - also need to ENABLE this and iwd.service so they start on boot
- systemctl start systemd-resolved.service
- restart iwd.service
- ping google works! installed sudo

## Connect to wifi network

View devices: `device list`
Scan for networks: `station <device-name> scan`
- Example: `station wlan0 scan`
View scanned networks: `station wlan0 get-networks`
Connect: `station wlan0 connect <ssid>`
