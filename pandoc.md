# pandoc

i think this was deleted before. looking for a minimal way to create blog posts from md files. the cli tool `pandoc` looks like a good way to generate html files.

## installation

looking at the `pandoc-bin` aur package. going to install according to process outlined at [[aur.md]].

the install went fine and i was able to generate an html file with the `-o` output flag. using the `-s` flag creates a standalone html file with all sorts of predefined wrapper elements and styles.

## templates

The `-s` flag creates a bunch of wrapper content, but i was to define a custom blog post template. here I should also be able to reference frontmatter values with interpolated variables.
