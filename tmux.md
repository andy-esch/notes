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

## Move window number

This changes the order of a window. Enter a number from 1 to N

```
^b ,
```


## Resize a pane

This resizes the pane five cells downward (if possible).
```
^b :resize-pane -D 5
```

There's also `-L` (left), `-R` (right), `-D` (down).

General format:

```
^b :resize-pane <direction_indicator> [num_cells]
```

You can move one cell at a time by not specifying a number after the direction indicator.
```
^b :resize-pane -D
