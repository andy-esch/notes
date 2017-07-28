

## ARGS

Multiple files can be opened in the same buffer by listing them after vim:

```bash
vim file1 file2 ...
```

To switch to different files, `:n` for next and `:prev` for previous. `:args` lists the files in the buffer.

Add a file to the buffer by typing `:argadd file`

## Navigation

In normal mode, H, M, and L move the cursor to the Top (Highest), Middle, or Bottom (Lowest) part of the screen.

## Regex

http://vimregex.com/

## splits

More on resizing here: <http://vim.wikia.com/wiki/Resize_splits_more_quickly>

### Resize current split

Increase vertical height of current split

```
:res +5
```

### Size all splits equally (only vertical?)

```
CTRL+w =
```

## Macros

Macros are complex operations that can be reduced to two keystrokes.

E.g., if a docstring needs to be added to all functions in a file

They are created by typing `q` in normal mode, then a letter identifier in a-z, followed by the series of vim keystrokes, and finally hitting `q` again.


qdoi"""<Esc>kbywj""pi"""<Esc>q

This creates a macro stored in d (triggered by typing `@d` in normal mode), that, starting at a `def func_name`, creates a line below the function, enters three quotes, goes up a line to yank the function name, goes down one line, pastes the function name, enters three more quotes, then exits the macro.
