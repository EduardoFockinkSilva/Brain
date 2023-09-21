# TMUX

## Introduction

`tmux`, an acronym for "Terminal Multiplexer," allows users to create, manage, and navigate multiple terminal sessions from a single terminal window. It facilitates background task execution, session sharing, and seamless continuity during remote administration. tmux is OS-agnostic, highly configurable, and widely used in UNIX-like environments such as Linux and macOS. It is released under the BSD license and has an active open-source community.

[Official Website](https://github.com/tmux/tmux/wiki)

## Pre-Installation Configuration

Before installing `tmux`, it's often advantageous to check for existing configurations. The `tmux` package manager, `tpm`, provides an extended library of plugins and configurations.

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

## Basic and Advanced Configuration

### tmux.conf

The `.tmux.conf` file stored in your home directory is the central configuration file for `tmux`. This file allows extensive customization, from key bindings to tmux pane behaviors.

```bash
touch ~/.tmux.conf
echo "set -g mouse on" >> ~/.tmux.conf
```

### Reload Configuration

To hot-reload your `.tmux.conf` without terminating ongoing tasks within tmux sessions, you can either bind a key to execute the reload or do it manually.

```bash
tmux source-file ~/.tmux.conf
```

## Commands and Key Bindings

### Session Management
- Spawn New Session: `tmux new-session -s <session_name>`
- Re-attach to a Session: `tmux attach -t <session_name>`
- Enumerate Sessions: `tmux list-sessions`
- Detach Without Terminating: `Ctrl-b d`
- Close Session: `tmux kill-session -t <session_name>`

### Window (Pane Group) Management
- Instantiate New Window: `Ctrl-b c`
- Scroll Through Next Window: `Ctrl-b n`
- Scroll Through Previous Window: `Ctrl-b p`
- Enumerate All Windows: `Ctrl-b l`
- Rename the Active Window: `Ctrl-b ,`
- Direct Window Selection: `Ctrl-b <window_index>`
- Terminate Current Window: `Ctrl-b &`

### Pane (Sub-Window) Management
- Vertical Partition: `Ctrl-b %`
- Horizontal Partition: `Ctrl-b "`
- Cycle Through Panes: `Ctrl-b o`
- Inverse Pane Navigation: `Ctrl-b ;`
- Custom Pane Resizing: `Ctrl-b :resize-pane -D 10` (Moves pane down by 10 cells)
- Fullscreen Pane Toggle: `Ctrl-b z`
- Swap Panes: `Ctrl-b {` or `Ctrl-b }`
- Pane Termination: `Ctrl-b x`

### Buffers and Clipboard
- Activate Copy Mode: `Ctrl-b [`
- Insert from Clipboard: `Ctrl-b ]`
- Buffer Listing: `Ctrl-b =`

### Miscellaneous
- Reapply tmux.conf: `Ctrl-b :source-file ~/.tmux.conf`
- Time Display: `Ctrl-b t`
- Command-Line tmux: `Ctrl-b :`

## Best Practices
- Use tmux sessions for grouping related windows.
- Leverage the `.tmux.conf` to create a personalized workflow.
- Regularly update tmux and its plugins to stay in line with the latest features and security patches.
