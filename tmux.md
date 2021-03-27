

## Rename window

```
^b :rename-window <new_window_name>
```

## Resize a pane

This resizes the pane five cells downward (if possible).
```
^b :resize-pane -D 5
```

There's also -R (right), -L (left), and -U (up).

You can move once cell at a time by not specifying a number after the direction indicator.
```
^b :resize-pane -D
```
