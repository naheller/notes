## testing sudo on nate user

"nate is not in the sudoers file"
need ot make sudoers file at /etc/sudoers (?)
- use visudo to edit /etc/sudoers
- add wheel group to sudoers (as root):
  - %wheel ALL=(ALL) ALL
- note: /etc/sudoers was invisible to nate user, but present and full of stuff as root

*risky* decided to enable passwordless sudo for wheel
made sure to use visudo
- needed to specify editor: export EDITOR=vim
  - do i need to make this permanent?
- visudo -> uncomment wheel line

now sudo works!
