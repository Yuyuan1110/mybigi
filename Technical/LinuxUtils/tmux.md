---
tags: 
  - Linux
  - Utils
  - tmux
  - screen
alias: []
created: 2025-07-02
updated: 2025-08-01
source:
---

# `tmux` Command Note
`tmux` is a terminal multiplexer. It lets you create and manage multiple terminal sessions within a single window, allowing you to detach from and re-attach to them later.

For more advanced usage, see [[tmux_advanced]].

## Command Basic Usage

### Session Management

- **`tmux`** or **`tmux new`**: Start a new `tmux` session.
- **`tmux new -s <session_name>`**: Start a new, named session.
- **`tmux ls`**: List all running `tmux` sessions.
- **`tmux attach -t <session_name>`**: Attach to a specific session.
- **`tmux detach`** (or press `Ctrl+b` then `d`): Detach from the current session.

### Inside `tmux`: The Prefix Key

All `tmux` commands are preceded by a prefix key. The default prefix is **`Ctrl+b`**.

### Basic Window and Pane Management

- **`Ctrl+b` `c`**: Create a new window.
- **`Ctrl+b` `n`**: Move to the next window.
- **`Ctrl+b` `p`**: Move to the previous window.
- **`Ctrl+b` `w`**: List windows to choose from.

- **`Ctrl+b` `%`**: Split the current pane vertically.
- **`Ctrl+b` `"`**: Split the current pane horizontally.
- **`Ctrl+b` `o`**: Cycle to the next pane.
- **`Ctrl+b` `x`**: Close the current pane.
- **`Ctrl+b` `$`**: Rename session, can also using `ctrl+b :rename-session -t old-name new-name`
