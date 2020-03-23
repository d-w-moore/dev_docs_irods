# TMUX

Description

`tmux` is a text based UI for connecting / disconnecting / multiplexing
to multiplex tty sessions within the same terminal window. It is similar
to the older GNU screen but slightly more modern.

`tmux` is useful tool when you'd like to
  - keeping related TTY sessions together simultaneously visible 
    (for example, during debugging)

  - preserving a session  (in a way, a better `nohup`)
    ^B-d will detach from a session

Usage examples:
---

```
tmux ls         - list available pre-existing sessions for attaching
tmux a -t0      - attach to session #0
tmux            - create a new session

```

---

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

Ctrl-B "            Create new pane by diving terminal window vertically
Ctrl-B %            Create new pane by diving terminal window horizontally
Ctrl-B ?            help (enters copy mode)
Ctrl-B x            kill pane
Ctrl-B &            kill window
Ctrl-B d            detach current session
Ctrl-B D            select session to detach from a menu
                    (useful when sessions are active elsewhere and are limiting
                    the current session's ability to resize)
```

---

## COPY mode (for search 

```
^B [  ->enter copy mode
ESC   -> quit copy mode

Within copy mode:
        #
        #       BEGIN SELECTION:        Ctrl-Space            
        #       COPY                    Alt-W
        #       PASTE                   ^B ]                    
        #       Ctrl-R                  reverse (upward) search
        #       Ctrl-S                  forward (downward) search

```
