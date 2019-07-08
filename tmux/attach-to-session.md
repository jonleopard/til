# Attach to a Tmux session

In order to attach to a tmux session, you first need to know which session you'd like to attach to.
This is done by running `tmux ls`, which will list all tmux sessions. Once you know which session
you would like to attach to, run the following:

`$ tmux a -t <name>`

e.g. `tmux a -t 2`
