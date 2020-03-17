```
bind-key -n M-Left select-pane -L
bind-key -n M-Down select-pane -D
bind-key -n M-Up   select-pane -U
bind-key -n M-Right select-pane -R
bind-key -n F12 copy-mode
bind-key C-n new-window
set-option -g history-limit 50000
```
("C-" or ^+letter ) = Ctrl key combination
 
Ctrl-B ?            help (enters copy mode)
Ctrl-B x            kill pane
Ctrl-B &            kill window

^B [  ->enter copy mode
        #----
        #       Alt-W
        #       Ctrl-Space
        #       ^B ]
        #       Ctrl-R reverse (upward) search
        #       Ctrl-S forward (downward) search
        #----
ESC   ->quit copy mode

```
