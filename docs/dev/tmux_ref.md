# tmux References

All commands in tmux are triggered by a **prefix key** followed by a **command key**. By default, tmux uses `C-b` as prefix key. `C-b` means pressing `Ctrl` + `b` at the same time.

### about panes 

- `C-b %` split pane left and right
- `C-b "` split pane top and bottom
- `C-b <arrow key>` navigates between panes
- `C-d` close pane


### about windows

- `C-b c` create a new window
- `C-b p` navigates to previous window
- `C-b n` navigates to next window
- `C-b <number>` navigates to specific window


### about sessions 

- to quit a session, close all panes
- to detach a session, `C-b d`
- `tmux ls` list sessions
- `tmux attach -t 0` attach to "0"
- `tmux new -s [NEW_SESSION_NAME]` create a new session with the specified name
- `tmux rename-session -t 0 database`


--- 

??? info "References"
    - [A Quick and Easy Guide to tmux](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)