TMUX

tmux stands for "terminal multiplexer," and it allows
multiple terminal sessions to be created, accessed,
and managed from a single screen. tmux may be detached
from a screen and continue running in the background,
then later reattached, facilitating long-running tasks
on remote servers. The software is built to be OS-agnostic
and is commonly used in UNIX-like environments, including
Linux and macOS. The project is an open-source initiative,
traditionally released under a BSD license.

Basic Configuration:
tmux.conf: Create a .tmux.conf file in your home directory
for user-level configurations. This is where you can
redefine key bindings, set tmux parameters, and include
custom scripts.

bash
touch ~/.tmux.conf

Reload Configuration: To apply new changes from .tmux.conf
without killing the tmux server, you can bind a key to
reload the configuration.

bash
bind r source-file ~/.tmux.conf

Comands

Session Management
Create New Session: tmux new-session -s session_name
Attach to Session: tmux attach -t session_name
List Sessions: tmux list-sessions
Detach from Session: Ctrl-b d
Kill Session: tmux kill-session -t session_name

Window Management
Create New Window: Ctrl-b c
Navigate to Next Window: Ctrl-b n
Navigate to Previous Window: Ctrl-b p
List Windows: Ctrl-b l
Rename Current Window: Ctrl-b ,
Select Window by Index: Ctrl-b 0 (or any number corresponding to the window index)
Kill Current Window: Ctrl-b &

Pane Management
Vertical Split: Ctrl-b %
Horizontal Split: Ctrl-b "
Switch to Next Pane: Ctrl-b o
Switch to Previous Pane: Ctrl-b ;
Resize Pane: Ctrl-b [arrow key] (press Ctrl-b followed by :resize-pane -D for more control)
Toggle Pane Zoom: Ctrl-b z
Swap Panes: Ctrl-b { or Ctrl-b }
Kill Pane: Ctrl-b x
Buffer and Clipboard
Enter Copy Mode: Ctrl-b [
Paste from Buffer: Ctrl-b ]
List Buffers: Ctrl-b =

Miscellaneous
Reload tmux.conf: Ctrl-b :source-file ~/.tmux.conf
Show Time: Ctrl-b t
tmux Command Prompt: Ctrl-b :
