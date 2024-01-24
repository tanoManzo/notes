1) ssh manzog2@biowulf.nih.gov
2) get node: sinteractive --gres=lscratch:20,gpu:v100:4 --mem=100g --cpus-per-task=4
3) change ssh config vscode cnXXXX & connect
4) connect to enviroment: 

source /data/manzog2/conda/etc/profile.d/conda.sh && source /data/manzog2/conda/etc/profile.d/mamba.sh


conda create -n envname --clone oldenv

mamba activate mimic_race_eth


ListerHill$202309




sinteractive --gres=lscratch:20 gpu:v100:1 --mem=32g --cpus-per-task=4


truncate from both 

#######################
**

# Tmux

Avoid interactive jobs getting killed when you lose connection!

  

To start:

### module load tmux

### tmux

  

To attach:

### module load tmux

### tmux attach

  

If you started more than one:

### tmux attach -t 0

or

### tmux attach -t 1

etc.

  

To scroll inside tmux:

### Ctrl+b, [

  

To detach manually (go back to original ssh shell, tmux still runs):

### Ctrl+b, d

# Interactive GPU nodes

See what gpus are available:

### freen | grep gpu

  

Get a v100x gpu node for 36 hours (the max), with 32g ram, and tunnel (for Jupyter):

### sinteractive -T --time=36:00:00 --mem=32g --gres=gpu:v100x:1

  

When you get the node, look for something like:

### “ssh  -L 44133:localhost:44133 [ondovbd@biowulf.nih.gov](mailto:ondovbd@biowulf.nih.gov)”

Paste this into a different local shell. Then Jupyter can use this port to tunnel from a browser. Note that if you lose the output with the port number (like 44133 above), you can check the shell variable $PORT1.

# Jupyter

Activate the conda env you want, then:

### module load jupyter

### jupyter notebook --no-browser --port $PORT1 2> jupyter.err &

  

Cat jupyter.err until you get the link, like:

### “http://localhost:44133/?token=baaae342a76b40c4c16689e2f0e777e5f84243945b249f91”

Paste the link into a browser on your local machine. Jupyter should come up.

**

#nih 


#knowledge #code #nih 