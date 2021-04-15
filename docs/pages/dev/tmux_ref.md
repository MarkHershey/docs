# tmux References

All commands in tmux are triggered by a **prefix key** followed by a **command key**. By default, tmux uses `C-b` as prefix key. `C-b` means pressing ++ctrl+b++ at the same time. Usually, people will configure `C-a` (aka. ++ctrl+a++ ) as their alternative prefix key.

## Default Shortcuts

??? info "References"
    - [A Quick and Easy Guide to tmux](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

### panes

- `<prefix> %` split pane left and right
- `<prefix> "` split pane top and bottom
- `<prefix> <arrow keys>` navigates between panes
- `C-d` close pane


### windows

- `<prefix>  c` create a new window
- `<prefix>  p` navigates to previous window
- `<prefix> n` navigates to next window
- `<prefix>  <number>` navigates to specific window


### sessions

- to quit a session, close all panes
- to detach a session, `<prefix>  d`
- `tmux ls` list sessions
- `tmux attach -t 0` attach to "0"
- `tmux new -s [NEW_SESSION_NAME]` create a new session with the specified name
- `tmux rename-session -t 0 database`


---

## `.tmux.conf` Customizations

??? info "References"
    - [Oh my tmux! My self-contained, pretty & versatile tmux configuration](https://github.com/gpakosz/.tmux)
    - [Productive Mouse-Free Development](https://pragprog.com/titles/bhtmux2/tmux-2/)
    - [Making tmux Pretty and Usable - A Guide to Customizing your tmux.conf](https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/)
    - [The Definitive Guide to Customizing the Tmux Status Line](https://medium.com/hackernoon/customizing-tmux-b3d2a5050207)

### panes

- `<prefix> |` split pane left and right
- `<prefix> -` split pane top and bottom
- `alt <arrow keys>` navigates between panes
- `C-d` close pane

### others

- `<prefix> r` reload tmux config
- `<prefix> m` toggle mouse mode
- `<prefix> [` enter scrolling mode
    - `q` quit scrolling mode
