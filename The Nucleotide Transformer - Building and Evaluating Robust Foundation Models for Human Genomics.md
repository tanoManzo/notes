Dalla-Torre et al. (InstaDeep, Nvidia, TUM)

## Abstract 
Closing the gap between measurable genetic information and observable traits is a longstanding challenge in genomics. 
1. We present an extensive study of foundation models pre-trained on DNA sequences, named the Nucleotide Transformer, integrating information from 3,202 diverse human genomes, as well as 850 genomes from a wide range of species, including model and non-model organisms. 
2. We show that the representations alone match or outperform specialized methods on 11 of 18 prediction tasks, and up to 15 after fine-tuning. Despite no supervision, the transformer models learnt to focus attention on key genomic elements, including those that regulate gene expression, such as enhancers. 
3. Finally, We demonstrate that utilizing model representations alone can improve the prioritization of functional genetic variants.

## Intro
Foundation models in artificial intelligence (AI) refer to large models incorporating millions of parameters and trained on vast amounts of data, which can be adapted for an array of predictive purposes.

One way they achieve a general understanding of language is by solving billions of cloze tests in which, given a sentence with some blanked-out words, they are rewarded by suggesting the correct word to fill the gap. This approach is referred to as masked language modelling [1].

Early examples of foundation models leveraging this objective in biology were trained on protein sequences by tasking LMs to uncover masked amino acids in large protein sequence datasets [3, 4, 5]. Trained protein LMs applied to downstream tasks, in what is called transfer learning, showed an aptitude to compete and even surpass previous methods for protein structure [3, 4] and function predictions [6, 7], even in data scarce regiments [8].

Beyond protein sequences, the dependency patterns embedded in DNA sequences are fundamental to the understanding of genomic processes, from the characterization of regulatory regions to the impact of individual variants in their [[haplotypic context]].

Large foundation models trained on sequences of nucleotides appear to be the natural choice to seize the opportunity in genomics research, with attempts to explore different angles recently proposed [18, 19, 19, 20].

[18] Y. Ji, Z. Zhou, H. Liu, and R. V. Davuluri, “Dnabert: pre-trained bidirectional encoder representations from transformers model for dna-language in genome,” Bioinformatics, vol. 37, no. 15, pp. 2112–2120, 2021. 
[19] M. T. Zvyagin, A. Brace, K. Hippe, Y. Deng, B. Zhang, C. O. Bohorquez, A. Clyde, B. Kale, D. Perez-Rivera, H. Ma, et al., “Genslms: Genome-scale language models reveal sars-cov-2 evolutionary dynamics.,” bioRxiv, 2022. 
[20] C. Outeiral and C. M. Deane, “Codon language embeddings provide strong signals for protein engineering,” bioRxiv, 2022

We built four distinct foundation language models of different sizes, ranging from 500M up to 2.5B parameters, and pre-trained them on three different datasets encompassing the Human reference genome, a collection of 3,200 diverse human genomes, and 850 genomes from several species (Table 6).

![[Pasted image 20231208144544.png]]


## Results

![[Pasted image 20231208152431.png]]