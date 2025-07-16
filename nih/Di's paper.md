## in the abstract 
Can you indicate which type of correlation (e.g., pearson) to the sentence: "..average correlation of 0.54.."

## in the intro
to the sentence: 

"Here to assess the functional roles of intronic and intergenic variants in the dorsolateral prefrontal cortex (DLPFC), we developed a deep learning model that integrates large-scale complementary epigenomic profiles of bulk and single cell levels"

I would add a comma after "Here, to assess.....", and I would use dash as you did in the abstract "single-cell" instead of "single cell"

## In Results 
### section: Deep Learning profiles ... 
do you have an explanation to the drop in performance from enhancer to silencer for the sentence: "(AUPRC) of 0.885 for enhancers and 0.637 for silencers on average"

### section: AD-associated ..

To the sentence at page 5: "This trend also was observed in blood cells ( SL loci vs all other loci) 40, key modulars of immune systems." I will change it in "This trend was **ALSO** observed in blood cells ( SL loci vs all other loci) 40, key **MODULATORS** of immune systems."

### section: SL-locuc radSVN

The sentence: "The exception cluster (the “pink” in Figure 4A) contains the genes upregulated across multiple cell types in the AD DLPFC, with an example of _MAPT_ which is upregulated in AD excitatory and inhibitory neurons, microglia and oligodendrocytes."

can be improved: "The exception cluster (the “pink” in Figure 4A) comprises genes that are upregulated across multiple cell types in the AD DLPFC. Notably, _MAPT_ serves as an example, showing increased expression in AD excitatory and inhibitory neurons, microglia, and oligodendrocytes."

### section: **Deep learning identifies AD causal variants through accurately quantifying their regulatory impacts.**

I would change the word "through" with the word "by" in the title of the section.

## Methods

### section: predicting silencer and enhancer..

In the section you say: " we adapted TREDNet" but in the discussion you say "we developed a deep learning framework, TREDNet"

When you say: "Candidate silencers were the DNase-seq peaks overlapping H3K27me3 peaks but not H3K27ac peaks in the central 400bp, together with the H3K27me3 peaks not overlapping H3K27ac peaks." 
It seems that you are taking H3k27me3 peaks not overlapping H3K27ac as candidate silencers. So the overlaping of DNase-seq and H3K27me3 seems unnecessary. Maybe I got wrong this sentence.

This sentence is unclear: "To predict enhancers and silencers for 9 cellular contexts, TREDNet model consist of 19 output nodes with the activation function of “softmax”, corresponding to silencers and enhancers for nine cellular contexts, as well as controls." 
Please clarify why 19 and not 18 (probable 9 enh, 9 sil, 1 control). Please if you add the description of a layer in the node "softmax layer" consider adding also other layers' description, (e.g., linear layer + softmax). Please consider motivating the choice of softmax as activation function over the others. 

Please clarify the threshold Csi, so the sentence: "In a cellular context c_s_i, was the prediction score corresponding to a false positive rate (FPR) of 0.05 among test samples wherein 90% were controls" 
It is unclear if it is a threshold or a prediction score. 

### section: DeltaActivity of regulatory variants
Several studies use the log ratio. Can you motivate the choice of the difference (e.g., mut-wild) instead of ration (e.g., mut/wild)?


### section: Predicting gene expression in AD ..

please motivate the choice of a linear lasso. Sentence: "We applied the Lasso linear model (from scikit-learning library, with the setting of alpha =0.0001, precompute=True, max_iter=1000 and selection=‘random’) to predict AD subtype gene expression using three input types: (1) gene expression profiles, (2) regulatory impact profiles, and (3) a combination of both."