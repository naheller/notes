# zathura

## keybinds

i don't like the default half-page scroll keybinds of ctrl-d and ctrl-u. i'd like zathura to behave like less and just use d and u.

however d is already used for switching between one- and two-column views. also shift-d switches the column order in two-column view.

so new desired keyinds are:
- u: half-page up
- d: half-page down
- ctrl-d: switch one- or two-column view
- shift-d: toggle column order

zathura looks for config file at either:
- /etc/zathurarc
- ~/.config/zathura/zathurarc

what is keybind setting syntax?

keybind changes:
map <key> <function> <optional arg>

for example, to set desired keybinds:
map d scroll half-down
map u scroll half-up
map <C-d> toggle_page_mode
map <S-d> cycle-first-column
