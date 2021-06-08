# tmux

## Resources

* [tmux cheatsheet](https://gist.github.com/andreyvit/2921703)

## Command Interfaces

* Command prompt: `^b :`
* Scroll within a pane: `^b [` — and then j/k for going up/down.
* Zoom: `^b z` (makes current page full terminal)
* Rename window: `^b ,`
* Search within 

## Rename window

```
^b :rename-window <new_window_name>
```

Or

```
^b ,
```


## Resize Pane

This will resize a pane upward to include 10 more cells
```
^b :resize-pane -U 10
```

There's also `-L` (left), `-R` (right), `-D` (down).

General format:

```
^b :resize-pane <direction_indicator> [num_cells]
```

## Navigate to pane #

Tmux supports navigating to a pane by typing the prefix (CTRL+b) and typing q. Then typing the number of the pane (which are displayed after typing CTRL+b q)

This navigates to pane 1:

```
^b q 1
```
