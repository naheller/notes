# DNS

Covered starting and enabling `systemd-resolved` service in [[iwd]].

## Symlinking resolv.conf

Having enabled the service, no further configuration was needed to get online. However I ran into a "connection refused" error when installing the `flyctl` AUR package while setting up FreshRSS. The issue seems to have been Golang, a dependency.

According to this github [issue](https://github.com/superfly/flyctl/issues/764) and the Arch [wiki](https://wiki.archlinux.org/title/Systemd-resolved#DNS), Golang expects DNS values to be found in `resolv.conf`, which is left empty in favor of `systemd-resolved`.

I need to replace `resolv.conf` with a symlink to a local stub at `/run/systemd/resolve/stub-resolv.conf`. Details including the command itself can be found in the wiki above. After doing this, the `flyctl` install succeeded. 
