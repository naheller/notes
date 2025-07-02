# neovim

ok i installed neovim. it does not appear to use my vanilla .vimrc because relative line nums are not showing up. 


## some things to look at first

- kickstart.nvim
- lazy.nvim
- snacks.vim - picker

## config file

it looks like neovim expects a config file at ~/.config/nvim/init.vim. This does not exist off a fresh install. Update June 2025: using `init.lua` instead.

the env variable `$MYVIMRC` points to the above init file. if i make changes to the file, i can reload any open editors with: `:reload $MYVIMRC`

## commands

- bp: previous buffer
- bn: next buffer
- e <filename>: edit (or create and edit) file
- checkhealth: run health checks and get some general info on neovim install
- verbose <command>: run command with verbose output
  - TODO: multi-line verbose output being cut off. figure out how to expand command region
- ls: list buffers
- b<num>: go to buffer <num>
- vs <filename>: vertical split
- sp <filename>: horizontal split

## clipboard

### copy

1. highlight text
2. use `"+y` to yank text into system clipboard

### paste

1. use `"+p` to paste text from system clipboard

According to `:checkhealth`, neovim has a clipboard tool called OSC 52 installed. This enables the copy functionality above. Docs state that this is bundled with neovim and will be used as a fallback if no other clipboard tool is found. OSC stands for Operating System Command.

TODO: Look into clipboard tools

- The `"` part of the command signals that we want to access a register.
- The `+` part of the command represents the register itself. There is apparently also a `*` register. This is where the result of the subsequent action will be stored.
- The `y` part of the command is the action to take - in this case, yanking.

## tabs and spaces

See `:tabstop` and `:shiftwidth` for more info

Recommended setup according to tabstop:
1. Always keep `tabstop` at 8
2. Set `shiftwidth` and `softtabstop` to desired value, like 4
3. Use `noexpandtab`

Note: above does not seem to make TABs enter 4 spaces. May need alternative approach.

## search and replace

Some regex:
- Search and replace on current line: `s/<existing-text>/<new-text>/g`
- Search and replace globally: `%s/<existing-text>/<new-text>/g`
- Search and replace across line range: `2,6/<existing-text>/<new-text>/g`
  - Example line range here being 2-6
- Note: Omitting `/g` in the above commands will replace only the *first* instance of the matching string on each line

## cool things

- shift-k: open man page in horizontal split for the word under the cursor (if one exists)

