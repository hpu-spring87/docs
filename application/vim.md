[TOC]

# [Overview](https://en.wikipedia.org/wiki/Vim_(text_editor))
## History
Initial release in November 1991.

## Help
`:help` help facility built-in
`vimtutor` : basic commands tutorials

## Features and improvements over vi
### Customization
Part of Vim's power is that it can be extensively customized.
- Change basic interface
- Define personalized key mappings
- Abbreviations to automate sequences of keystrokes
- Call internal or user defined functions

Plugins available that will extend or add new functionality to Vim.
- Vim's internal scripting language - vimscript (viml)
- Lua, Perl, Python, Raccket, Ruby, and Tcl

### Search and replace
- Change each "foo" to "bar" in the current line: `:s/foo/bar/g` and have confirm : `:s/foo/bar/gc`
- Change each "foo" to "bar" in all the lines: `:%s/foo/bar/g` and have confirm: `:%s/foo/bar/gc`
- Change each "foo" to "bar" for all lines from line 5 to line 12: `:5,12s/foo/bar/gc`

### Copy and paste
- Config at `.vimrc` : `xnoremap p pgvy` it mean *p* will replay with *pgvy*, *p* to paste and *gv* to re-select what was originally selected, *y* to copy it again.
- Paste multiple copy: *<number>p* e.g: *30p* to paste 30 time of copy text.

### Others
- Completion
- Comparison and merging of files - vimdiff
- Extended regular expressions
- Graphic user interface - gvim
- Spell checking
- Folding
- Tabbed windows
- Unicode and other multilanguage support
- Syntax highlight
- etc.

## [Documentation](http://vimdoc.sourceforge.net/htmldoc/usr_toc.html)
[summary](http://vimdoc.sourceforge.net/)
http://vim.wikia.com/wiki/Vim_Tips_Wiki
http://vim.wikia.com/wiki/Vim_documentation
http://vim.wikia.com/wiki/Vim_scripts
http://www.vim.org/docs.php
[Books](http://iccf-holland.org/click5.html)


# Getting started



# Editing Effectively




# Tips and Tricks
## [Work with multiple files](http://stackoverflow.com/questions/53664/how-to-effectively-work-with-multiple-files-in-vim)

## Show hidden characters like carriage return and linefeed

`vim -b <file>`: show carriage return

`:set list`: to show linefeed

# Tuning Vim
## Vim script
Vim script (viml) is the scripting language built into Vim. Based on the ex editor language of the original vi editor.

Vim script files are stored in plain text format and the file name extension is .vim.

## Plug-in manager
- [pathogen](http://www.vim.org/scripts/script.php?script_id=2332)
- [Vundle](https://github.com/neovim/neovim)
- [NeoVundle](https://github.com/Shougo/neobundle.vim)
- [Vim-plug](https://github.com/junegunn/vim-plug)



## [.vimrc template](http://www.vimbits.com/)
- http://alvinalexander.com/linux-unix/vimrc-vim-example-commands-configuration-file
- [change color of vim](http://alvinalexander.com/linux/vi-vim-editor-color-scheme-colorscheme)
`:colorscheme delek` or `:colo delek`
`:syntax on`
- Copy text and paste and recopy it to paste more time: `xnoremap p pgvy`
- [.vimrc template](http://amix.dk/vim/vimrc.html)
- [A good vimrc](http://dougblack.io/words/a-good-vimrc.html)
- [.vimrc template 2](http://spf13.com/post/perfect-vimrc-vim-config-file)
- [ultimate configuration](https://github.com/amix/vimrc)

Example:

```vim
set number
colo delek
syntax on
set backup
set backupdir=/tmp/vim
set dir=/tmp/vim/swap
set hlsearch
set incsearch
set ignorecase
set expandtab
set smarttab
set shiftwidth=2
set tabstop=2
set autoindent
set smartindent
set wrap
```

# [NeoVim](https://github.com/neovim/neovim) - A new generation of Vim
Neovim is a refactor of Vim, that strives to be a superset of Vim.
- Neovim shares the same configuration syntax with Vim.
- Neovim can execute plugins asynchronously.
- Neovim's plugins can also be written in any language.