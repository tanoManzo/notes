accepted on February 1, 2021, Bioinformatics

**Motivation:**
Gene regulatory code is highly complex due to the existence of polysemy and distant semantic relationship, which previous informatics methods often fail to capture especially in data-scarce scenarios.

**Results:**
DNABERT, to capture global and transferrable understanding of genomic DNA sequences based on up and downstream nucleotide contexts. We compared DNABERT to the most widely used programs for genome-wide regulatory elements prediction and demonstrate its ease of use, accuracy and efficiency. We show that the single pre-trained transformers model can simultaneously achieve state-of-the-art performance on prediction of promoters, splice sites and transcription factor binding sites, after easy fine-tuning using small task-specific labeled data.

DNABERT enables direct visualization of nucleotide-level importance and semantic relationship within input sequences for better interpretability and accurate identification of conserved sequence motifs and functional genetic variant candidates. Finally, we demonstrate that pre-trained DNABERT with human genome can even be readily applied to other organisms with exceptional performance. We anticipate that the pre-trained DNABERT model can be fined tuned to many other sequence analyses tasks. 



## Intro
Deciphering the language of DNA for hidden instructions has been one of the major goals of biological research (Andersson and Sandelin, 2020). While the genetic code explaining how DNA is translated into proteins is universal, the regulatory code that determines when and how the genes are expressed varies across different cell-types and organisms (Nirenberg et al., 1965). Same cis-regulatory elements (CREs) often have distinct functions and activities in different biological contexts, while widely spaced multiple CREs may cooperate, resulting in context-dependent use of alternative promoters with varied functional roles. Such observations suggest existence of [[polysemy]] and distant semantic relationship within sequence codes, which are key properties of natural language. 

Previous linguistics studies confirmed that the DNA, especially the non-coding region, indeed exhibits great similarity to human language, ranging from alphabets and [[lexicons]] to grammar and [[phonetics]] (Brendel and Busse, 1984; Head, 1987; Ji, 1999; Mantegna et al., 1994; Searls, 1992; 2002).  However, how the semantics (i.e. functions) of CREs vary across different contexts (up and downstream nucleotide sequences) remains largely unknown. 

Many computational tools have been developed by successfully applying deep learning techniques on genomic sequence data to study the individual aspects of cis-regulatory landscapes, including DNA-protein interactions, chromatin accessibility, non-coding variants. 

To better model DNA as a language, an ideal computational method should (i) globally take all the contextual information into account to distinguish polysemous CREs; (ii) develop generic understanding transferable to various tasks; (iii) generalize well when labeled data is limited. However, both CNN and RNN architectures fail to satisfy these requirements (Fig. 1a) (Bengio et al., 2013; LeCun et al., 2015).

