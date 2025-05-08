first boot failed because no boot entry
needed to load back into installer and:
- mount partitions, chroot /mnt
- update /boot/loader/loader.conf
- create /boot/loader/entries/arch.conf
- run bootctl and verify entry is detected
- exit chroot, unount partitions, reboot
