---
title: PiStatus
---

A tmux shortcut for monitoring a Raspberry Pi with PiHole.

```shell
#!/bin/sh

tmux new-session -d -s "pistatus"
tmux send-keys -t 0 "pihole -t" "C-m"
tmux split-window -v "htop"
tmux resize-pane -U 5
tmux -2 attach-session -t pistatus
```