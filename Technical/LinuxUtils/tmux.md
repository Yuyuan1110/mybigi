---
tags: Linux, Utils, tmux, screen
alias: []
created: 2025-07-02
updated:
source:
---

# `tmux` Command Note
`tmux` is an open-source terminal multiplexer for Unix-like operating systems. It allows multiple terminal sessions to be accessed simultaneously in a single window, this feature like `screen` but `tmux` is more modern.

## Command Basic Usage
Command format:
```bash
tmux // to create new window
tmux new -t new_session // you can named your window(or session), default session is 0
```

Option:
`tmux ls`: list all session.
`tmux attach`: resume sesssion

Inside session:

```
C-b c // create session
C-b n // next session
C-b p // pervious session
C-b d // deattach
C-b % // vertical split panel
C-b " // harizontal split panel
C-b <direct key> // select panel, can use ~/.tmuc.confll to bind hjkl key to replace direct key.
C-b ! // distill panel to independ window.

```