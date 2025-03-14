## Reviewer 1

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

## Reviewer 2

This manuscript by Manzo et al. describes a benchmark study of various deep learning models on the task of variant effect prediction, in particular the effect of single nucleotide polymorphisms on enhancer activity. It compares various deep learning approaches from seemingly simple CNNs to more advanced transformer architectures on a benchmark data set with training data extracted from ENCODE and validation data compiled from the literature. The main finding is that CNN-based models perform across the board better than transformers, even though the latter catch up a bit when being properly fine-tuned.  
  
Overall, this appears to be an interesting study, the benchmark is comprehensive w.r.t. the architectures considered. The results are plausible, perhaps not overly surprising, but of course it’s always beneficial to have empirical evidence instead of mere speculation.  
  
On the flip side, however, due to its very nature as a pure benchmark paper, the manuscript lacks technical novelty. Furthermore, it is not quite polished yet and at times hard to follow in detail.  
  
To be specific:  
- The description of experimental methodology needs quite a bit guesswork. First, it is not obvious  what is done at training time, what is done at prediction time w.r.t. features/response. It looks like  a prediction of enhancer activity (as numerical value) is done for every 1kb fragment and only the evaluation calculates log2-fold changes from pairs of reference/alternative sequence. If that is so, then it’s not quite clear what the relationship of “training data” (which seems to have enhancers with binary labeling) and the validation data is. I guess the models are all originally just trained to distinguish enhancer from control in a binary classification task, and the rest is just a matter of post-processing the output, but even if that is correct, it should be described more explicitly. In a similar manner, it is never spelled out which objective the fine-tuning is trying to optimize.  
  
- The quality of the figures is poor, which is actually a major point for an empirical paper. All figures would greatly benefit from an enlarged (font) size, but in particular Fig. 4 is completely unreadable in a printout in its current form, and even on screen it requires an entirely different zoom than the main text. I suggest to enlarge this one to spanning both columns, especially since it introduces the main visualization type that is used throughout the supplement.  
  
- Section 4.1 (written as 3.1 for some reason) contains textual description of all compared architectures. While such information is appreciated in principle, it would probably fit better to the supplement, as it is . The space could be used for more important information (see points above).  
  
- The heatmap visualization of the classification results (Fig. 2, 4, Supplement) is unnecessarily complicated as column 1 and column 3 show the same information, so do column 2 and column 4.  
Furthermore, it might be a good idea to already include there a measure that aggregates the entire confusion matrix. The study in Fig. 6 later on then uses F1.  
  
- Related to the previous point, the manuscript does use different performance measures, but is a bit inconsistent at times and justifications for specific choices are missing. For instance, does Fig. 5 use the area under the curves for the classification tasks, but Fig. 6 uses F1? What is the point of using both AU-ROC and AU-PR when the data is almost balanced anyway? Why are both measures used only in this study on one cell line?  
  
- Sometimes the wording does not quite match the numbers shown in the plots. While it is true CNN-based methods outperform transformers by and large, the absolute performance of all methods is low. Pearson correlation of 0.25 and binary classification accuracy of 0.6 does not justify statements such as “CNN-based models, …, excel in predicting variant effects.”.  
Also, it seems that TREDNet is quite good in the regression, but not very competitive for enhancer detection and variant classification task (cf. Fig. 5, 6), but this becomes apparent only from inspecting the plots in detail. Any speculation why that is?