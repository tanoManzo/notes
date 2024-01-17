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

## split pane vertically
ctrl+b and %

## split pane horizontally
ctrl+b and ""

## move between panes
ctrl+b and q

## change pane size
ctrl+b and ctrl

## change layout
ctrl+b and alt+1 or 2 or ..5

## Best to move
ctlr+b and w

