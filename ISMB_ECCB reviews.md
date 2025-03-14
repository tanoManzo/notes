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


## Review 5
The authors consider the accuracy of different deep learning approaches to assess the effect of SNPs given 1000bp DNA fragments as input data. Results suggest that CNNs typically perform better than more general, longer context transformer models on this task, although there are some tasks where other architectures do well, e.g. causal SNP identification and enhancer region detection.  
  
I think it is potentially interesting to point out this kind of result. However, I think it is also important to acknowledge that the context here is very short for some of these models and also that some of these models are simply not designed for this task. In the conclusion the authors themselves say that “This further suggests that hybrid models should not be compared to CNN models based purely on the predictive power of regulatory variants, but evaluated fully in the context of the specific biological tasks”. Yet that is exactly what is done in the current paper?  
  
I think it is also important to make it clear that these models are trained on completely different kinds of data – so you are not only comparing architectures, you are comparing model + dataset. That makes things pretty complex in terms of benchmarking performance.  
  
Specific technical comments:  
  
1000bp fragments are a very short context for many of the transformer models. For example, Nucleotide Transformer uses non-overlapping 6-mers so 1000bp is only 167 tokens for the 1000 token context length it actually uses. GENA_LM uses Byte-Pair encoding meaning that the 1000bp probably only takes 150ish of the 512 token context length. Both of these models, because of their tokenization methods, are probably not suited for accurate individual nucleotide predictions. It would be interesting to see whether a longer context improves performance.  
  
Can you say something about why Borzoi is working well for the causal SNP problem?  
  
I’m not sure how the GeneFormer is used for these tasks. In the methods section it would be good to explain how the methods are used and fine-tuned specifically for this study rather than giving the long general descriptions of the methods.  
  
For the CNN models it would be good to explain in the methods section how they incorporate cell-type information for people not familiar. I'm not sure exactly how you have applied them in the tasks presented.  
  
Specific style comments:  
  
The methods section has a long summary of all the models. That is more like a background section than a methods section. You can just refer to the original papers which describe the methods. The methods section should describe what was done in this study specifically, what is needed to understand the results and datasets. A concise text description with citations, or a table, would be more suitable. Explaining the terminology used in the model description in the figures and tables would be useful (e.g. explaining the difference between all the different variants of each method).  
  
The discussion and results are quite repetitive with the same general points about CNNs and transformers is made multiple times.  
  
There is a lot of variation in the presentation styles used for the same types of data. A more uniform presentation style would make the results easier to digest for the reader.