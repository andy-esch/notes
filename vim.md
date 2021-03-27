# Vim Tips & Tricks

## Table Of Contents

* [Tabs](#Tabs)
* [Splits](#Splits)
* [Jedi Vim](#jedi-vim)

**Other things**

* `vimrc`: My [`.vimrc`](https://github.com/andy-esch/dotfiles/blob/master/vimrc)
* `tmux`: I mostly use vim in multiple tmux windows, so I have the [christoomey/vim-tmux-navigator](https://github.com/christoomey/vim-tmux-navigator) plugin in my vimrc
* `powerline`: I also like [`powerline-status`](https://github.com/powerline/powerline) for vim, commandline, and tmux
* `psf/black`: I write a lot of Python in vim, so I use [psf/black](https://github.com/psf/black)


## Multiple Files in the Same Buffer

Multiple files can be opened in the same buffer by listing them after vim:

```bash
$ vim file1 file2 ...
```

To switch to different files, `:n` for next and `:prev` for previous. `:args` lists the files in the buffer.

Add a file to the buffer by typing `:argadd file`

Alternatively, tabs can be used by typing: `vim -p file1 file2 ...`. See more below.

## Tabs

### Open multiple files in tabs:

```bash
$ vim -p *.py
```

Or use an explicit list.

### Add New Tab when Already in Vim

```vim
:tabnew filename
```

### Tab Navigation

To navigate to the tab to the right, type `gt`.

To navigate to the tab to the left, type `gT`.

## Navigation

### Full Document

In normal mode:

* Go to the beginning of the document: `gg`
* Go to the end of the document: `G`
* Go to a spcific line `nG` (e.g., `51G` to go to line 51)

### Current Line

In normal mode:

* Go to the end of a line: `$`
* Go to the beginning of text in a line: `^`
* Go to the beginning of a line: `0` (zero)

TODO: add beginning of word, previous word, etc. etc.

### In current view

In normal mode, H, M, and L move the cursor to the Top (Highest), Middle, or Bottom (Lowest) part of the screen.

## Regex

<http://vimregex.com/>

## Splits


### Resize current split

Increase/decrease vertical height of current split

Increase current split by five lines
```vim
:res +5
```

Decrease the current splity by 10 lines
```vim
:res -10
```

More on resizing here: <http://vim.wikia.com/wiki/Resize_splits_more_quickly>

### Size all splits equally (only vertical?)

```vim
CTRL+w =
```

## Macros

Macros are complex operations that can be reduced to two keystrokes.

E.g., if a docstring needs to be added to all functions in a file

They are created by typing `q` in normal mode, then a letter identifier in a-z, followed by the series of vim keystrokes, and finally hitting `q` again.


```vim
qdoi"""<Esc>kbywj""pi"""<Esc>q
```

This creates a macro stored in d (triggered by typing `@d` in normal mode), that, starting at a `def func_name`, creates a line below the function, enters three quotes, goes up a line to yank the function name, goes down one line, pastes the function name, enters three more quotes, then exits the macro.

## Spelling

The following highlights 'misspellings':

```vim
:setlocal spell
```

Ref: https://robots.thoughtbot.com/vim-spell-checking

## Stop highlighting search

Typing

```vim
:nohl
```

stops the highlighting of words from searches from `/searchterm`

## Prettify JSON

This tip is pretty awesome. From <http://pascalprecht.github.io/2014/07/10/pretty-print-json-in-vim/>

```vim
:%!python -m json.tool
```

Note: The `%` means the command (`!python ...`) is applied to the whole document

## Redraw screen

Redraw/refresh screen if another process leaves artifacts:

```vim
:redraw!
```

If the syntax highlighting goes all wrong, this trick works to correct it (it reloads the file):

```vim
:e
```

`e` is short for `edit`. This is also great for loading changes to a file that happened outside the current session.

## Search

### Search for other instances of word under cursor

While in normal mode, press `*` (`SHIFT+*`).

It is possible to select what is under a visual selection:
  <https://vim.fandom.com/wiki/Search_for_visually_selected_text>

## Show current working directory

```
:cwd
```

Ref: <https://unix.stackexchange.com/a/8240>


## Jedi Vim

### Show documentation

This will show documentation (when in normal mode) for any function, class, or other
documented object that the cursor is over.

```
<Shift>+K
```

[Jedi Vim repo](https://github.com/davidhalter/jedi-vim)

## Another one

What will happen now?

## Bash Commands within Vim

Commands for bash can be run within vim:

```
:!bash-command
```

For example:

```
:!aws s3 cp localfile.py s3://bucket/path/
```


## Cut without copy


### Cut a line without copying

Just cut it into the "black hole register": `"_dd`


## Open a file while in vim

Option 1 - Open as a new tab

```
:tabnew /path/to/file
```

Option 2 - Open file

```
:e /path/to/file
```

## Copy contents of one file into current vim buffer

Pretty neat trick for appending the contents of one file into the currently open file.
Similar to `file1 >> file2` in bash.

```vim
:r /path/to/file
```

## Reload vimrc

```vim
:source ~/.vimrc
```
