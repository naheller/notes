# removable drives like usb and sd

## viewing device info

- `fdisk -l`: list partition tables for devices
- `lsblk --fs`: output info about filesystems
- `lspci -k`: show info about PCI buses and devices connected to them. `-k` shows the kernel drivers handling each device.

## flashing image to device

i've used the `dd` tool to flash the arch iso to a usb stick. i think the same method works for sd cards. the below command was used for arch:

flash image: `dd bs=4M if=<path-to-mage> of=<path-to-drive> conv=fsync oflag=direct status=progress`

## setting up garlicOS and ROMs on anbernic rg35xx

1. extract 7zip file with `7z e <path-to-file>`. should now have a `garlic.img`.
2. flash garlicOS to sd card using command above.
    - `dd 

## mounting and unmounting devices

make sure to target the entire device, rather than any of its partitions.

unmount: `umount <path-to-device>`

## formatting device

trying the gparted GUI tool.
