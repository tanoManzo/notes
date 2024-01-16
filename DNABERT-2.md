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
First, although proven to be generalizable to other organisms, the pretraining was solely done on the human reference genome, omitting the sequence conservation and diversity across species. Second, k-mer tokenization resulted in information leakage and overall poor computational efficiency during pre-training, which hampers its scalability. Lastly, the simplistic DNABERT-XL solution—intended to bypass the restriction of 512 input sequences imposed by the learned positional embedding [Kenton and Toutanova, 2019]—fell short in handling long input sequences, both in efficiency and effectiveness. 

### Nucleotide Transformers limitations
Recently, Lopez et al. [2023] introduced Nucleotide Transformers (NT), a series of genome foundation models scaling from 500M to 2500M parameters. NT alleviated the first two limitations of DNABERT by pre-training on a large collection of genomes from 850 species and replacing overlapping k-mer tokenization with a non-overlapping version, substantially reducing tokenized sequence length. Despite this, a hard input length limitation still exist, while, as we will discuss in Sec. 2, non-overlapping k-mer tokenization also suffered from poor sample efficiency as it complicates the model’s task of aligning significantly distinct representations of near-identical inputs.

### DNABERT-2 better than DNABERT

- Replaces k-mer tokenization with Byte Pair Encoding (BPE) [Sennrich et al., 2016].
- Replacing learned positional embeddings with Attention with Linear Biases (ALiBi) [Press et al., 2021] incorporating Flash Attention [Dao et al., 2022].
- 56× less computational cost and 21× fewer parameters.

We introduce DNABERT-2, a multi-species genome foundation model that replaces k-mer tokenization with Byte Pair Encoding (BPE) [Sennrich et al., 2016], a data compression algorithm that has been widely used by large language models. We show that BPE effectively addresses the known issues of k-mer tokenization while maintaining the computational efficiency of non-overlapping tokenization. Moreover, DNABERT-2 overcomes the limitation of DNABERT by replacing learned positional embeddings with Attention with Linear Biases (ALiBi) [Press et al., 2021] to get rid of the input length limitation, incorporating Flash Attention [Dao et al., 2022] to increase computational efficiency, and adjusting model architecture to increase model capability. As a result of the efficient tokenizer and advanced model architecture, DNABERT-2 achieves comparable performance to the state-of-the-art model with approximately 56× less computational cost and 21× fewer parameters, identifying its computation- and sample- efficiency and enabling efficient fine-tuning on most consumer GPUs.

### Benchmarks
Existing works [Lopez et al., 2023] are either too trivial or too challenging, leading to similar scores for most models and failing to accurately reflect different models’ capabilities. The scarcity of high-quality benchmark datasets hampers evaluating and comparing different models and further hinders the development of novel techniques. To this end, we introduce Genome Understanding Evaluation (GUE), a standardized and comprehensive multi-species benchmark containing 28 datasets across 7 important genome analysis tasks on genomes of 4 species with input lengths ranging from 70 to 1000. All the datasets are elaborately calibrated with a series of strategies to ensure they are suitable for reflecting the capability level of existing genome foundation models.

### In brief 
1) We identify key obstacles in genome tokenization and provide deep insights, presenting a simple yet effective solution that balances the efficiency and effectiveness of genome foundation models; 
2) We introduce DNABERT-2, an efficient pre-trained foundation model for multi-species genome that delivers performance on par with the state-of-the-art model while being 21× smaller and utilizes approximately 56× less GPU time; 
3) We introduce Genome Understanding Evaluation (GUE), a standardized, comprehensive, and well-calibrated multi-species genome classification benchmark including 7 tasks and 28 datasets to facilitate research in genome foundation model

## Background

### Information Leaked issue
DNA sequences consist of 4 unique nucleotide bases: A, T, C, and G. A majority of genome language models [Ji et al., 2021; Lopez et al., 2023] utilize the k-mer tokenization technique, in which each contiguous k-length genome segment is considered as a token. During tokenization, a sliding window with window size k and stride t is employed to convert the original genome sequence into a series of k-mers.

![[Pasted image 20240116101815.png]]

To prevent the entire leakage of a masked token, at least k − 1 tokens on its left and right sides in total must be masked, which explains why Ji et al. [2021] opt to mask a continuous span of k tokens. Furthermore, to guarantee no leakage of a masked token, at least k tokens on both sides must be masked. 

### Overlapped Issue
If the search space is undesirably reduced due to information leakage, the model only needs to differentiate between a limited number of options. This results in poor sample efficiency, as the model may not be sufficiently challenged to learn the underlying patterns in the data. Also, the tokenized sequence for an input of length L consists of L − k + 1 tokens, each with a length of k. This results in a tokenized sequence with considerable redundancy and a length nearly equivalent to the original sequence, leading to low computation efficiency considering the quadratic computation complexity of Transformer-based [Vaswani et al., 2017] models. This becomes particularly problematic when attempting to scale up the model. Therefore, Lopez et al. [2023] proposed the non-overlapping k-mer tokenization.

### Non-overlapped Issue
Despite the two sequences originating from the same genomic segment, their tokenized representations bear little resemblance. This inconsistent behavior introduces unnecessary hurdles for the model during training, as it poses unnecessary difficulty for the model to align distinct representations of identical or near-identical inputs. Consequently, the inefficiency in learning from the data could impede the overall model performance.

### Byte-Pair Encoding (BPE) [Sennrich et al., 2016]

We propose to adapt SentencePiece [Kudo and Richardson, 2018], a subword tokenization framework widely used in natural language processing, to replace k-mer tokenization for genome sequences.

BPE iteratively merge frequent pairs of nucleotides and genome segments, forming a vocabulary of variable-length tokens that effectively represent the entire genome dataset. 
- First, it not only prevents information leakage but also significantly reduces the sequence length by approximately 5 times, substantially improving computational efficiency.
- Its robust tokenization result is beneficial for sample efficiency since it allows the model to focus on understanding the genome language semantics without being distracted by the distinct representations of the same input.
- Unlike k-mer tokenization, BPE doesn’t always produce tokens of length k. The model is challenged to predict both the number of nucleotides and the particular nucleotides themselves. This naturally transforms the masked language modeling objective into a T5-style [Raffel et al., 2020] "replace spans of text" objective, which has been demonstrated to be more effective than standard masked language modeling in various scenarios.

## Method

### Tokenizer 
DNABERT-2 adapts SentencePiece [Kudo and Richardson, 2018] with Byte Pair Encoding (BPE) [Sennrich et al., 2016] to perform tokenization for DNA sequences. SentencePiece is a language-agnostic tokenizer that considers each input as a raw stream without assuming any pre-tokenization, which matches greatly with genome sequences where the definitions of word and sentence do not exist.

BPE is a compression algorithm that has been widely used in the area of natural language processing as a word segmentation strategy. 
![[Pasted image 20240116112343.png]]
The iteration continues till we achieve the desired number of words in the vocabulary. Thus, the target vocabulary size plays a crucial role.

#### Vocabulary Size
Due to the significant difference between natural language and DNA sequence, vocabulary sizes that are commonly used in the NLP area [Kenton and Toutanova, 2019; OpenAI, 2023; Raffel et al., 2020; Vaswani et al., 2017] may not be appropriate for genome sequences. To determine the most suitable vocabulary size, we constructed 8 vocabularies with target sizes ranging from 2 8 to 2 15 on the multi-species genomes (see Sec. 4.1) to empirically evaluate the impact of varying vocabulary sizes. As indicated in Figure 3a, larger vocabularies tend to encompass more lengthy tokens, which enables the tokenizer to represent the same input sequence with fewer tokens.

![[Pasted image 20240116112615.png]]
Shorter tokenized sequences consequently reduce the computational cost (See Figure 3b), as the computational complexity of Transformers is quadratic in relation to the input sequence length. Therefore, from the computation efficiency perspective, a larger vocabulary size is favorable. However, a larger vocabulary leads to more sparse updates to the embedding layer, given that each token would be used less frequently, which might compromise the model’s performance. 

#### Performance vs Computational Efficiency
Figure 3c displays the performance of each variant, where the model performance is measured by the dataset- and task-average scores. As depicted in the figure, unlike computational efficiency, the model’s performance does not consistently improve as the vocabulary size increases. Therefore, we selected a vocabulary size of 2<sup>12</sup> = 4096 for training the final DNABERT-2 model, as it best balances model performance with computational efficiency among the candidates.

### Model  

DNABERT-2 adapts the Transformer Encoder architecture similar to BERT [Kenton and Toutanova, 2019]. We incorporate a series of recent advances in deep learning to increase the model’s efficiency and capability, including:
- Replacing learned positional embeddings with the Attention with Linear Biases (ALiBi) [Press et al., 2021] to overcome the input length limitation;
- Utilizing FlashAttention [Dao et al., 2022] and Low Precision Layer Normalization to increase computation and memory efficiency;
- Employing the Low-Rank Adaptation (LoRA) [Hu et al., 2021] in the fine-tuning stage (if necessary) for parameter-efficient training.

#### [[Attention with Linear Biases]]
Due to the permutation-invariant nature of the attention mechanism, explicit positional information is required in attention-based models. Existing solutions such as Sinusoidal [Vaswani et al., 2017], learned [Kenton and Toutanova, 2019], and Rotary [Su et al., 2021] positional embedding methods either suffer from input length restriction or poor extrapolation capability when applied to sequences longer than training data. Attention with Linear Biases (ALiBi) provides an efficient yet effective solution. Instead of adding position embeddings to the input, ALiBi adds a fixed set of static, non-learned biases to each attention calculation to incorporate positional information into attention scores. 

#### Flash Attention

