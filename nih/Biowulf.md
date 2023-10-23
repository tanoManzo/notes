1) ssh manzog2@biowulf.nih.gov
2) get node: sinteractive --gres=lscratch:20,gpu:v100:4 --mem=100g --cpus-per-task=4
3) change ssh config vscode cnXXXX & connect
4) connect to enviroment: 

source /data/USER/conda/etc/profile.d/conda.sh && source /data/USER/conda/etc/profile.d/mamba.sh

mamba activate mimic_race_eth
Fall2022@ListerHill






sinteractive --gres=lscratch:20,gpu:v100:4 --mem=100g --cpus-per-task=4







#knowledge #code