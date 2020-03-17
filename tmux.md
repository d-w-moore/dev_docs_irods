TMUX - a handy text based UI for connecting / disconnecting / multiplexing
terminal sessions.  (Like the older GNU screen but more modern)

## A simple configuration

The following minimal `~/.tmux.conf` offers some extra conveniences

```
bind-key -n M-Left select-pane -L
bind-key -n M-Down select-pane -D
bind-key -n M-Up   select-pane -U
bind-key -n M-Right select-pane -R
bind-key -n F12 copy-mode
bind-key -n new-window
set-option -g history-limit 50000
```

## Some tips for basic operations and navigation:

```
(C-<other_key> or ^+letter ) = Ctrl key combination
(M-<other_key>)
Ctrl-B ?            help (enters copy mode)
Ctrl-B x            kill pane
Ctrl-B &            kill window
Ctrl-B d            detach current session
Ctrl-B D            select session to detach from a menu
                    (useful when sessions are active elsewhere and are limiting
                    the current session's ability to resize)
```

## COPY mode


```
^B [  ->enter copy mode
        #----
        #       BEGIN SELECTION:        Ctrl-Space            
        #       COPY                    Alt-W
        #       PASTE                   ^B ]                    
        #       Ctrl-R reverse (upward) search
        #       Ctrl-S forward (downward) search
        #----
ESC   ->quit copy mode

```
