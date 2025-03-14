
This paper presents a comprehensive evaluation of deep learning models for predicting the effects of genetic variants on enhancer activity. Its key contributions include a benchmarking framework that covers nine datasets derived from three experimental methods, a systematic evaluation of several DNA foundation models—such as Gena-LM, DNABERT2, HyenaDNA, and the Nucleotide Transformer series—and four supervised models, including SEI, TREDNet, Enformer, and Borzoi. However, there exist some main limitations in their evaluations, analysis, and writing, as detailed below.  
  
  
Comments:  
The paper evaluates four DNA foundation models series but neglects more recent ones, such as Grover and Caduceus (both published in Jun/Jul 2024). The authors should either incorporate these newer models or clearly justify their exclusion. For single-cell foundation models, only Geneformer is evaluated. The rationale for selecting it without comparing it to other potential candidates needs clarification.  
  
The analysis focuses primarily on model architecture while overlooking other critical factors like differences in training paradigms, parameter counts, and datasets used for training. Attributing performance differences solely to architecture may oversimplify the underlying issues. The conclusion that “CNN models outperform more advanced architectures, such as transformers, on causative regulatory variant detection” seemingly oversimplified. Another interpretation might be that supervised functional genomics models (e.g., Enformer, Borzoi, SEI, TREDNet) are better suited for this task compared to self-supervised DNA LLMs. Adding a table comparing model size, architecture, pretraining tasks, etc. might help clarify whether architecture alone explains results.  
  
The paper categorizes HyenaDNA, Enformer, and Borzoi under hybrid models. However, HyenaDNA significantly differs from models like Enformer and Borzoi, as it does not use attention mechanisms and is considerably more lightweight. A revised categorization of different models or a more detailed discussion that highlights these differences would be beneficial.  
  
All experiments use a fixed input sequence length of 1 kb. This limited context may not adequately capture long-range genomic interactions. Incorporating experiments with varied context lengths could yield more informative insights.  
  
The manuscript lacks a clear description of the computational tasks. It seems the paper covers three tasks—regression (predicting log2-fold changes), classification (predicting up/down regulation), and causal SNP identification within LD blocks—should be introduced at the start, with further details on their biological significance, metrics, and task-specific baselines.  
  
There are no technical details regarding the adaptation of Geneformer which is originally designed for scRNA-seq data for DNA variant effect prediction.  
  
  
  
References  
  
Schiff, Yair, et al. "Caduceus: Bi-directional equivariant long-range dna sequence modeling." arXiv preprint arXiv:2403.03234 (2024).  
  
Sanabria, Melissa, et al. "DNA language model GROVER learns sequence context in the human genome." Nature Machine Intelligence 6.8 (2024): 911-923.