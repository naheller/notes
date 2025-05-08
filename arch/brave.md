# Brave

Originally installed manually using steps outlined in [[aur.md]].

## First run 

Upon running `brave` in the terminal, shown error "Missing X server or $DISPLAY"

Following steps fixed the issue:
1. Ran brave in terminal with flag `-ozone-platforn=wayland`
2. One brave starts, navigate to brave://flags
3. Set Preferred Ozone Platform to "auto"
4. Restart brave

TODO: Find brave config file and determine whether this Ozone setting can be persisted via the file alone.

## Brave sync

Noticed that, despite adding browser to sync chain and syncing settings, many of the settings don't seem to match the setup on my Mac.
