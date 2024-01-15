Zhou et al.,

## Abstract 

### General 
Decoding the linguistic intricacies of the genome pre-trained foundational models such as [[DNABERT pre-trained Bidirectional Encoder Representations from Transformers model for DNA-language in genome]] and [[The Nucleotide Transformer - Building and Evaluating Robust Foundation Models for Human Genomics]] have made significant strides in this area.

### Issue
Existing works have largely hinged on k-mer, fixed-length permutations of A, T, C, and G, as the token of the genome language due to its simplicity. However, we argue that the computation and sample inefficiencies introduced by k-mer tokenization are primary obstacles in developing large genome foundational models.

### Contribution 
We propose to replace k-mer [[tokenization]] with Byte Pair Encoding (BPE), a statistics-based data compression algorithm that constructs tokens by iteratively merging the most frequent co-occurring genome segment in the corpus, which benefits from the computational efficiency of non-overlapping **tokenization**. 

DNABERT-2 is a refined genome foundation model that adapts an efficient tokenizer and employs multiple strategies to overcome input length constraints, reduce time and memory expenditure, and enhance model capability.

We propose the Genome Understanding Evaluation (GUE), a comprehensive multi-species genome classification dataset that amalgamates 28 distinct datasets across 7 tasks, with input lengths ranging from 70 to 1000.

### Results 
Compared to DNABERT, while being 3× more efficient, DNABERT-2 outperforms it on 23 out of 28 datasets, with an average improvement of 6 absolute scores on GUE. The code, data, and pre-trained model are publicly available at https://github.com/Zhihan1996/DNABERT_2.


## Introduction

### State of the art 
#### Upstream 
Transformer-based foundation models can capture complex relationships and dependencies in DNA sequences, opening new avenues for understanding **transcriptional regulation [Li et al., 2023], non-coding genetic variants associated with human diseases and traits [Rozowsky et al., 2023], and the functional effects of regulatory elements [Smith et al., 2023].**

#### Downstream 
**Downstream applications, including promoter prediction [Le et al., 2022; Zhang et al., 2022], gene expression prediction [Avsec et al., 2021], DNA methylation prediction [Jin et al.,2022], chromatin state analysis [Lee et al., 2022], promoter-enhancer interaction prediction [Chen et al., 2022; Ni et al., 2022], TF-DNA binding prediction [Wang et al., 2022], variant effect prediction [Rozowsky et al., 2023], gene network prediction [Theodoris et al., 2023] and more.** 

### DNABERT [Ji et al., 2021] limitations 
