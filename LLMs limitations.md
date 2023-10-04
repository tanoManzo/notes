
High Pre-Training Costs


Fine-Tuning Overhead: Fine-tuning entire LLMs requires the same amount of memory as pre-training, rendering it infeasible for many practitioners. When adapting an LLM via full-model fine tuning, an individual copy of the model must be stored (consuming data storage) and loaded(expending memory allocation, etc.) for each task.


High Inference Latency: (1) low parallelizability since the inference procedure proceeds one token at a time and (2) large memory footprints, due to the model size and the transient states needed during decoding (e.g., attention key and value tensors).


Tasks Not Solvable By Scale: Given the current progress, one may question whether there are limits we deem impossible to overcome with in the current paradigm of scaling data/model sizes of autoregressive Transformer-based LLMs.
