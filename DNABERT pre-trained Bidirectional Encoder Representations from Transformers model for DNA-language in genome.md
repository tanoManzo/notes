Yanrong Ji et al.
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

CNN is usually unable to capture semantic dependency within long-range contexts, as its capability to extract local features is limited by the filter size. RNN models (LSTM, GRU), although able to learn long-term dependency, greatly suffer from [[vanishing gradient]] and low-efficiency problem when it sequentially processes all past states and compresses contextual information into a bottleneck with long input sequences. 

To address the above limitations, we adapted the idea of Bidirectional Encoder Representations from Transformers (BERT) model (Devlin et al., 2018) to genomic DNA setting and developed a deep learning method called DNABERT. We demonstrate that DNABERT resolves the above challenges by (i) developing general and transferable understandings of DNA from the purely unlabeled human genome, and utilizing them to generically solve various sequencerelated tasks in a ‘one-model-does-it-all’ fashion; (ii) globally capturing contextual information from the entire input sequence with attention mechanism; (iii) achieving great performance in data-scarce scenarios; (iv) uncovering important subregions and potential relationships between different cis-elements of a DNA sequence, without any human guidance; (v) successfully working in a crossorganism manner. Since the pre-training of DNABERT model is resource-intensive (about 25 days on 8 NVIDIA 2080Ti GPUs), as a major contribution of this study, we provide the source code and pretrained model on GitHub for future academic research.


BERT is a transformer-based contextualized language representation model that has achieved superhuman performance in many natural language processing (NLP) tasks. It introduces a paradigm of pre-training and fine-tuning, which first develops general-purpose understandings from massive amount of unlabeled data and then solves various applications with task-specific data with minimal architectural modification. DNABERT follows the same training process as BERT.

![[Pasted image 20231125120954.png]]

Similar to BERT, DNABERT also adopts pre-training—fine-tuning scheme (Fig. 1c). However, we significantly modified the pretraining process from the original BERT implementation by removing next sentence prediction, adjusting the sequence length and forcing the model to predict contiguous k tokens adapting to DNA scenario. During pre-training, DNABERT learns basic syntax and semantics of DNA via self-supervision, based on 10 to 510- length sequences extracted from human genome via truncation and sampling. For each sequence, we randomly mask regions of k contiguous tokens that constitute 15% of the sequence and let DNABERT to predict the masked sequences based on the remainder, ensuring ample training examples. We pre-trained DNABERT with cross-entropy loss: L ¼ PN i¼0 y0 i logðyiÞ. Here, y0 i and yi are the ground-truth and predicted probability for each of N classes. The pre-trained DNABERT model can be fine-tuned with task-specific training data for applications in various sequence- and token-level prediction tasks. We fine-tuned DNABERT model on three specific applications—prediction of promoters, transcription factor binding sites (TFBSs) and splice sites—and benchmarked the trained models with the current state-of-the-art tools.

**Tokenization** 
Instead of regarding each base as a single token, we tokenized a DNA sequence with the k-mer representation, an approach that has been widely used in analyzing DNA sequences. The k-mer representation incorporates richer contextual information for each deoxynucleotide base by concatenating it with its following ones. The concatenation of them is called a k-mer. For example, a DNA sequence ‘ATGGCT’ can be tokenized to a sequence of four 3-mers: fATG, TGG, GGC, GCTg or to a sequence of two 5-mers: fATGGC, TGGCTg. Since different k leads to different tokenization of a DNA sequence. In our experiments, we respectively set k as 3,4,5 and 6 and train 4 different models: DNABERT-3, DNABERT4, DNABERT-5, DNABERT-6. For DNABERT-k, the vocabulary of it consists of all the permutations of the k-mer as well as 5 special tokens: [CLS] stands for classification token; [PAD] stands for padding token, [UNK] stands for unknown token, [SEP] stands for separation token and [MASK] stands for masked token. 

We used the same model architecture as the BERT base, which consists of 12 Transformer layers with 768 hidden units and 12 attention heads in each layer, and the same parameter setting across all the four DNABERT models during pre-training. We trained each DNABERT model with mixed precision floating point arithmetic on machines with 8 Nvidia2080Ti GPUs.

Fine-tuning For each downstream application, we started from the pre-trained parameters and fine-tuned DNABERT with task-specific data. We utilized the same training tricks across all the applications, where the learning rate was first linear warmed-up to the peak value and then linear decayed to near 0. We utilized AdamW with fixed weight decay as optimizer and employed dropout to the output layer. We split training data into training set and developing set for hyperparameter tuning. For DNABERT with different k, we slightly adjusted the peak learning rate.

For sequences longer than 512, we split them into pieces and concatenate their representations as the final representation. This allows DNABERT to process extralong sequences (DNABERT-XL). DNABERT with k ¼ 3, 4, 5, 6 achieved very similar performances with slight fluctuations. In all experiments, we report results of kmer ¼ 6 since it achieves the best performance.


### DNABERT-Prom effectively predicts proximal and core promoter regions

Predicting [[gene promoters]] is one of the most challenging bioinformatics' problems. We began by evaluating our pre-trained model on identifying proximal promoter regions. To fairly compare with existing tools with different sequence length settings, we fine-tuned two models, named DNABERT-Prom-300 and DNABERT-Prom-scan, using human [[TATA]] and non-TATA promoters of 10 000 bp length, from Eukaryotic Promoter Database (EPDnew) (Dreos et al., 2013).

![[Pasted image 20231126120407.png]]

We used 70 bp, centered around TSS, of the Prom300 data and compared with CNN, CNNþLSTM and CNNþGRU. DNABERT-Prom-core clearly outperformed all the three baselines across different datasets (Fig. 2c–g), clearly demonstrating that DNABERT can be reliably fine-tuned to accurately predict both the long proximal promoters and shorter core promoters, relying only on nearby sequence patterns around the TSS region. To further demonstrates the effectiveness of DNABERT-XL, we also conducted experiments on 301 bp-long sequences and 2001 bp-long sequences. Experiments shows that the model achieves a better performance in predicting 2001 bp-long sequences.


### DNABERT-TF accurately identifies transcription factor binding sites


NextGen sequencing (NGS) technologies have facilitated genomewide identification of gene regulatory regions in an unprecedented way and unveiled the complexity of gene regulation. An important step in the analyses of in vivo genome-wide binding interaction data is prediction of [[TFBS]] in the target cis-regulatory regions and curation of the resulting TF binding profiles.

We thus fine-tuned DNABERT-TF model to predict TFBSs in the ChIP-seq enriched regions, using 690 TF ChIP-seq uniform peak profiles from ENCODE database (Dunham et al., 2012) and compared with wellknown and previous published TFBS prediction tools, including DeepBind(Alipanahi et al., 2015), DeepSEA(Zhou and Troyanskaya, 2015), Basset (Kelley et al., 2016), DeepSite(Zhang et al., 2020), DanQ(Quang and Xie, 2016) and DESSO (Khamis et al., 2018).


To evaluate whether our method can effectively distinguish polysemouscis-regulatory elements, we focused on p53 family proteins (which recognize same motifs) and investigated contextual differences in binding specificities between TAp73-alpha and TAp73- beta isoforms. We overlapped p53, TAp73-alpha and TAp73-beta ChIP-seq peaks from Gene Expression Omnibus (GEO) dataset GSE15780 with binding sites predicted by our P53Scan program (Koeppel et al., 2011; Yoon et al., 2002) and used the resulting ChIP-seq-characterized BS (35 bp) to fine-tune our model.

DNABERT-TF achieved near perfect performances (0.99) on binary classification of individual TFs (Supplementary Table S2). Using input sequences with a much wider context (500 bp), DNABERTTF effectively distinguished the two TAp73 isoforms with an accuracy of 0.828 (Supplementary Table S2). In summary, DNABERTTF can accurately identify even very similar TFBSs based on the distinct context windows.


### DNABERT-viz allows visualization of important regions, contexts and sequence motifs

To overcome the common ‘black-box’ problem, deep learning models need to maintain interpretability, while exceling in performance in comparison to traditional methods. Therefore, to summarize and understand important sequence features on which fine-tuned DNABERT models base classification decisions on, we developed DNABERT-viz module for direct visualization of important regions contributing to the model decision.

![[Pasted image 20231126122200.png]]
Figure 4a shows the learned attention maps of three TAp73-beta response elements, where DNABERT-viz accurately determines both positions and scores of TFBS predicted by P53Scan in an unsupervised manner. We then aggregated all heatmaps to produce attention landscapes on test sets of Prom-300 and ENCODE 690 TF. 

![[Pasted image 20231126122331.png]]


#attention #nlp #nih #research #paper #good4pub #knowledge 