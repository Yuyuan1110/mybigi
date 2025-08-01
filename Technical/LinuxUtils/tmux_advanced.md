---
tags: Linux, Utils, tmux
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `tmux` Advanced Usage

This note covers more advanced `tmux` features. For a basic introduction, see [[tmux]].

## Scripting `tmux`

You can script `tmux` to create a standard development environment.

Create a shell script (`dev.sh`) with the following content:

```bash
#!/bin/bash

# Set the session name
SESSION="development"

# Start a new, detached tmux session
tmux new-session -d -s $SESSION

# Window 1: "Editor"
tmux rename-window -t $SESSION:0 'Editor'
tmux send-keys -t $SESSION:0 'vim' C-m

# Window 2: "Shell"
tmux new-window -t $SESSION:1 -n 'Shell'

# Split the second window and run a server
tmux split-window -h -t $SESSION:1
tmux send-keys -t $SESSION:1 'npm run dev' C-m

# Attach to the session
tmux attach-session -t $SESSION
```

Make the script executable (`chmod +x dev.sh`) and run it (`./dev.sh`) to launch your pre-configured environment.

## Synchronize Panes

`tmux` can send the same command to multiple panes simultaneously.

1.  Arrange your panes as desired.
2.  Press **`Ctrl+b`** then **`:`** to open the `tmux` command prompt.
3.  Type `setw synchronize-panes` and press Enter.

Now, whatever you type in one pane will be mirrored in all other panes in that window. This is useful for running the same command on multiple servers.

Run the command again with `setw synchronize-panes off` to disable it.

## Customizing `tmux` (`.tmux.conf`)

You can customize `tmux` by creating a configuration file at `~/.tmux.conf`.

Here are some common customizations:

```conf
# Set a new prefix key (e.g., Ctrl+a)
set -g prefix C-a
unbind C-b
bind C-a send-prefix

# Enable mouse mode
set -g mouse on

# Use vim keybindings in copy mode
setw -g mode-keys vi

# More intuitive split-pane commands
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %
```

After saving the file, you can reload the configuration with:
**`Ctrl+b`** then **`:`** and type `source-file ~/.tmux.conf`.