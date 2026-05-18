## Projects Description

### Project 1: Decoding Transcription Factor Binding in Enhancers with Deep Learning
Enhancers are non-coding regions of the genome that regulate gene expression by
recruiting transcription factors (TFs) to specific DNA sequences. This project centers on
understanding how TFs are configured within enhancers, using DeepFootprinting, a pipeline
We developed that combines Convolutional Neural Networks (CNNs) with DeepSHAP to
pinpoint TF binding sites at base-pair resolution. The analysis draws on multi-modal genomic
data such as TF ChIP-seq, histone marks like H3K27ac, and DNase Hypersensitivity Sites
(DHS), to build a picture of enhancer activity.
A major focus of the work is understanding variant effects: how genetic variants can disrupt
TF binding motifs and, in turn, alter enhancer function. The intern will get hands-on
experience with real multi-omics datasets and state-of-the-art interpretability methods, sitting
at the crossroads of regulatory biology and deep learning.

Skills gained: CNNs, DeepSHAP, ChIP-seq/DHS data analysis, variant effect prediction,
Python, and genomics pipelines.

Essential Literature:
- Avsec, Ž., Weilert, M., Shrikumar, A., et al. (2021). Base-resolution models of transcription-factor binding reveal soft motif syntax. Nature Genetics, 53, 354-366. https://doi.org/10.1038/s41588-021-00782-6
- Jindal GA, Farley EK. Enhancer grammar in development, evolution, and disease: dependencies and interplay. Dev Cell. 2021 Mar 8;56(5):575-587. doi: 10.1016/j.devcel.2021.02.016. PMID: 33689769; PMCID: PMC8462829.
### Project 2: Unraveling the Regulatory Landscape of C9orf72 in ALS
The most common genetic cause of ALS is a hexanucleotide (G4C2) repeat expansion in
the first intron of the C9orf72 gene, found in roughly 40% of familial ALS cases. This
expansion is thought to drive disease through a mix of haploinsufficiency and toxic
gain-of-function effects from repeat RNA and dipeptide repeat proteins. This project uses
AlphaGenome, a hybrid Transformer/CNN model, to integrate RNA-seq, histone
modification, and open chromatin data in order to characterize the regulatory architecture of
the C9orf72 locus.
The intern will work with publicly available data from ENCODE alongside experimental data
coming from an ongoing NIH collaboration, with real potential to connect computational
findings to wet lab validation. The overarching goal is to map the regulatory elements at this
locus and figure out whether the repeat expansion interferes with any of them — a question
with direct relevance to therapeutic strategies.

Skills gained: Transformer/CNN genomic models, RNA-seq and epigenomic data integration,
ENCODE data retrieval, regulatory element annotation, NIH collaboration exposure.

Essential Literature:
- Liu Y, Huang Z, Liu H, Ji Z, Arora A, Cai D, Wang H, Liu M, Simko EAJ, Zhang Y, Periz G, Liu Z, Wang J. DNA-initiated epigenetic cascades driven by C9orf72 hexanucleotide repeat. Neuron. 2023 Apr 19;111(8):1205-1221.e9. doi: 10.1016/j.neuron.2023.01.022. Epub 2023 Feb 22. Erratum in: Neuron. 2023 Apr 19;111(8):1345. doi: 10.1016/j.neuron.2023.03.035. PMID: 36822200; PMCID: PMC10121948.
- 

### Project 3: Biology-Aware DNA Tokenization for Genomic Language Models
Most DNA tokenizers (k-mer, BPE, and similar approaches) are built around statistical
patterns with no real biological awareness baked in. This project takes a different angle:
what if TF binding motifs served as tokens, the same way words carry meaning in natural
language? The goal is to build a tokenizer grounded in biology and then benchmark it
against existing methods by training and evaluating Transformer models like DNABERT and
DNABERT-2 on standard genomic prediction tasks.
There is also a direct connection to Project 1, the TF motif catalog produced by
DeepFootprinting will feed directly into the tokenizer vocabulary, creating a feedback loop
between experimental discovery and model design. This is a genuinely novel project for
someone who enjoys building new tools and thinking about how biological knowledge can
improve machine learning.

Skills gained: NLP tokenization methods, Transformer model training, DNABERT(2),
Nucleotide Transfore and genomic language models, Python/HuggingFace, genomic
benchmark evaluation.