# AUR

I'd like to use Brave on Arch, but it's only available on AUR. So I need to get that working.

## Installing AUR packages

As an Arch user it's good practice to try and download and compile the build files manually. The Arch wiki has steps to do this. But for the sake of time, I'd like to make use of yay to get things going quickly.

TODO: Practice installing an AUR package manually

## Installing packages manually

I should learn to do this before relying on yay for everything AUR.

1. Install `base-devel`
2. Git clone the package repo (I'm using the ~/AUR folder)
3. Run `makepkg` in the repo folder
4. Run pacman -U package_file (the .pkg.tar.zst file)

First tested with the [[brave.md]] package. See there for more details.

## Upgrading packages

1. Git pull latest in repo
2. Follow steps 3 and 4 above

## Yay

I'll follow the yay readme for the following steps.

DONE: Get copy/paste working correctly across apps/windows, so I can do something useful like copy the readme URL here. 

Whether or not i'm using yay, it looks like i'll need the `base-devel` package group installed (Note June 2025: `base-devel` is included as part of the desktop profile during archinstall).

I'll also need git, which i already have. Fun fact: the `--needed` flag to pacman installs makes sure that any packages in the install list that already exist in the system are not reinstalled.

TL;DR is that I'll clone down the yay repo, cd into it, and run `makepkg -si` there. 

QUESTION: Where should I keep the yay repo folder?

## Paru

Paru is an alternative for Yay that's written in rust. To download or upgrade:

1. git clone https://aur.archlinux.org/paru.git
2. cd paru
3. makepkg -si

# commands

- paru <package>: interactiively search and install package
