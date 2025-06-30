# dotfiles

I have a `.dotfiles` folder in my home directory that's linked to a github repo. i'd like to symlink the files to the locations where their respective programs are looking for them. This is often in the `~/.config` folder, but could be elsewhere.

## stow

there is a program called `stow` that should handle the symlinking. the `.dotfiles` folder structure needs to be kind of specific for it to work. at the top level, there will be a folder for each program. For example, `.dotfiles/bash/.bashrc` or `.dotfiles/sway/.config/sway/config`.

The key here is that the folder structure directly under bash, sway, etc, should mirror that of the target directory structure (in this case the home directory). Note that if a target directory is not specified with the `-t` flag, the default target will be the direct parent of wherever the command is run.

Note: I need to run the stow command individually for each package. `stow sway`, `stow neovim`, etc.
