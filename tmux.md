[[nih/Biowulf|Biowulf]] 

## new session 
tmux new -s <name of the session>


## List of session 
tmux ls

## detached 
ctrl+b then d

## attached
tmux a 
tmux a -t <name of the session>

## kill session
tmux kill-session -t <name of the session>

## new window 
tmux new -t <name of the session>

## split pane
ctrl+b and %