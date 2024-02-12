

Noncoding genomic variations constitute the majority of disease and other trait-associated [[single-nucleotide polymorphisms 1]] (SNPs) but characterizing their functional effects remains a challenge. 


Recent progress on prioritizing functional noncoding variants has been made by integrating evolutionary conservation and genomic and [[chromatin annotations 1]] at the position of interest. 

Such approaches are valuable for prioritizing sequence variants; however, current methods except for a parallel work have not been able to extract and utilize regulatory sequence information de novo for noncoding-variant function prediction, which requires precise [[allele 1]]-specific prediction with single-nucleotide sensitivity. In fact, no previous approach predicts functional effects of noncoding variants from only genomic sequence, and no method has been demonstrated to predict with single-nucleotide sensitivity the effects of noncoding variants on [[transcription factor (TF) binding 1]], [[DNA accessibility 1]] and [[histone marks of sequences 1]].

A quantitative model accurately estimating binding of chromatin proteins and histone marks from DNA sequence with single-nucleotide sensitivity is key to this challenge. This is especially true because although motifs have been used for variant detection with limited success, they show substantially less predictive power than evolutionary features and chromatin annotation. Furthermore, multiple sources of evidence indicate that in vivo TF binding depends upon sequence beyond traditionally defined motifs. For example, TF binding can be influenced by cofactor binding sequences, chromatin accessibility and structural flexibility of binding-site DNA. DNase I–hypersensitive sites (DHSs) and histone marks are expected to have even more complex underlying mechanisms involving multiple chromatin proteins. Therefore, accurate sequence-based prediction of chromatin features requires a flexible quantitative model capable of modeling such complex dependencies— and those predictions may then be used to estimate functional effects of noncoding variants.

To address this fundamental problem, here we developed a fully sequence-based algorithmic framework, DeepSEA (deep learning–based sequence analyzer), for noncoding-variant effect prediction. We first directly learn regulatory sequence code from genomic sequence by learning to simultaneously predict large-scale chromatin-profiling data, including TF binding, DNase I sensitivity and histone-mark profiles (Fig. 1). This predictive model is central for estimating noncoding-variant effects on chromatin. We introduce three major features in our deep learning–based model: integrating sequence information from a wide sequence context, learning sequence code at multiple spatial scales with a hierarchical architecture, and multitask joint learning of diverse chromatin factors sharing predictive features. To train the model, we compiled a diverse compendium of genome-wide chromatin profiles from the Encyclopedia of DNA Elements (ENCODE) and Roadmap Epigenomics projects, including 690 TF binding profiles for 160 different TFs, 125 DHS profiles and 104 histone-mark profiles (Supplementary Table 1). In total, 521.6 Mbp of the genome (17%) were found to be bound by at least one measured TF and were used as a regulatory information–rich and challenging set for training our DeepSEA regulatory code model.

![[Pasted image 20231119134708.png]]
Integrating wider sequence context is critical because sequence surrounding the variant position determines the regulatory properties of the variant and thus is important for understanding functional effects of noncoding variants. Whereas previous studies for TF binding prediction have focused on small sequence windows directly associated with the binding sites11,12, we found increasing the context sequence size to 1 kbp substantially improved performance of our model (Supplementary Fig. 1). The multilayer hierarchically structured model allows us to scale to such long sequence input and learn sequence dependencies at multiple scales.

We share learned predictive sequence features across all chromatin profile predictors with a multitask model. In addition to greatly increasing computational efficiency, this multitask architecture allows predictive strength to be shared across a wide range of chromatin feature profiles for TF binding, DHSs and histone marks. For example, a sequence feature that is effective for recognizing binding of a specific TF can be simultaneously used by another predictor for a physically interacting TF.

Next we evaluated how well DeepSEA can predict chromatin features from holdout genomic sequences (Fig. 2a and Supplementary Table 2). We found that DeepSEA predicted chromatin features with high accuracy, including TF binding sites, for which the median area under the curve (AUC) was 0.958. Our method also enabled high-performance sequence-based prediction of both DHSs (median AUC = 0.923) and histone modifications (median AUC = 0.856).

![[Pasted image 20231119140423.png]]

Sequence elements informative of chromatin feature prediction for any sequence can be identified through the ‘in silico saturated mutagenesis’ approach. Through computational mutation scanning along all potential single-nucleotide substitutions, the approach analyzes the effects of each base substitution on chromatin feature predictions, thereby identifying which sequence features are most informative for a specific chromatin effect prediction (Supplementary Fig. 3).

![[Pasted image 20231119141231.png]]To enable systematical evaluation of the predicted chromatin effects of single-nucleotide alteration in noncoding sequence, we devised a high-throughput data–based evaluation protocol using allelic imbalance information from digital genomic footprinting (DGF) DNase-seq data on ENCODE cell lines13. Allelic imbalance—when one allele is observed in DNase-seq data significantly more often than the other allele at a heterozygous site for a single-cell-type sample—indicates different DNase I sensitivities of the two alleles. The pipeline identified 57,407 allelically imbalanced SNPs from 35 cell types with DHS predictors in DeepSEA. We used these allelically imbalanced SNPs as the standards for evaluating the DHS prediction in DeepSEA at singlenucleotide sensitivity. 

The DeepSEA model accurately predicted the more DNase I–sensitive allele with the DHS classifier for the corresponding cell type, even though the model was trained on only the reference genome and not on the variant data—a result supporting highly accurate prediction of the effect of even a single-nucleotide change (Fig. 2b,c). Moreover, the accuracy robustly increased as we retained only high-confidence predictions by raising the threshold of absolute predicted probability difference (Fig. 2c and Supplementary Table 4). For example, for confidently predicted allelically imbalanced SNPs with probability difference greater than 0.1 (6,726 variants), the model achieved >95% accuracy. On a smaller-scale evaluation, with histone-mark QTLs identified from Yoruba lymphoblastoid cells, we similarly observed that the confidently predicted allelically imbalanced SNPs were highly consistent with estimated QTL effects (Supplementary Fig. 4). Thus our model is capable of delivering high-confidence prediction of chromatin effect of genomic variants on the basis of genomic sequence alone.

Furthermore, our model could accurately predict the effect of individual SNPs on TF binding with the DeepSEA TF binding classifiers, as demonstrated for several SNPs with experimentally validated known effects on TF binding. For the breast cancer risk locus SNP rs4784227 (ref. 14), we identified the increased affinity of FOXA1 as the strongest effect of C-to-T alteration consistently in all five cell types for which we have learned predictors for FOXA1. For an SNP associated with the inherited blood disorder α thalassemia15, the model predicted that the alteration of T to C creates a binding site for GATA1. For an isolated pancreatic agenesis mutation16, we predicted the deleterious effect to FOXA2 binding with A-to-G alteration.

Finally, we extended DeepSEA to prioritize functional SNPs on the basis of the predicted chromatin effect signals. This is, to our knowledge, the first approach for prioritization of functional variants using de novo regulatory sequence information. DeepSEA allows us to produce classifiers with superior performance in predicting trait-associated variants from population genetics studies (for example, disease-associated genome-wide association study (GWAS) SNPs) without relying on any annotation information by combining de novo sequence-based chromatin effect predictions with evolutionary conservation information.

DeepSEA models were accurate even when only chromatin effect predictions were used as input, and adding evolutionary conservation information (also used by all other methods) provided a further performance improvement to DeepSEA-based classifiers. Interestingly, DeepSEA chromatin predictions were more informative for common noncoding variants such as eQTLs and trait-associated (GWAS) variants, whereas the evolutionary conservation information was more informative for noncoding mutations from HGMD, which are more likely to be deleterious and under significant purifying selection.

Our method’s capability of making de novo predictions based on the exact sequence-change information also allowed us to predict the effects of insertions or deletions (indels). Evaluated on HGMD indels, the model trained with HGMD SNPs could prioritize HGMD indels against nearby control 1000 Genomes indels with high accuracy, without any training on indels (Supplementary Fig. 8).

## Method

### Model design and training

A deep convolutional network is a type of multilayer neural network. As is typical in a deep neural network, the model is organized by a sequential layer-by-layer structure executing a sequence of functional transformations. Each layer consists of a number of computational units called neurons. Each neuron receives input from a set of previous-layer neurons or input data and outputs a single value. All neurons in a layer together constitute an internal feature representation or output of that layer. The deep convolutional network model features sequential alternating convolution and pooling layers that extract sequence features at different spatial scales, followed by one fully connected layer that integrates information from the full-length sequence and a sigmoid output layer that computes probability output for each individual chromatin factor feature. Each layer of the deep convolutional network executes a linear transformation of the output from the previous layer by multiplying a weight matrix, followed by a nonlinear transformation. The weight matrix is learned during training to minimize predictive errors. The basic layer types in our model are convolution layer, pooling layer and fully connected layer.


A pooling layer computes the maximum value in a window of spatially adjacent convolution layer outputs for each kernel, with a step size equal to the size of the pooling window so it reduces the size of the output and allows learning sequence features at a higher spatial scale in the next convolution layer. 

DeepSEA uses three convolution layers with 320, 480 and 960 kernels, respectively (for detailed specifications see Supplementary Note). Higher-level convolution layers receive input from larger spatial ranges and are capable of representing more complex patterns than the lower layers. On top of the third convolution layer we added a fully connected layer in which all neurons receive input from all outputs of the previous layer, integrating information from the full length of 1,000 bp. This fully connected layer computes ReLU(WX), where X is the input and W is the weight matrix for the fully connected layer. The last layer, the sigmoid output layer, makes predictions for each of the 919 chromatin features (125 DNase features, 690 TF features, 104 histone features) and scales predictions to the 0–1 range by the sigmoid function.

### Training of the DeepSEA model

To train the model, we minimized the objective function, which is defined as the sum of negative log likelihood (NLL) and regularization terms for controlling overfitting. L2 regularization term is defined to be the sum of squares of all the weight matrix entries. ‖H<sup>−1</sup>‖<sub>1</sub> is defined to be the L1 norm of all the output values of the last layer (fully connected layer) before the output layer. Additionally, the optimization is subjected to regularization constraints that for any layer m and neuron n, or the L2 norm of weights for any neuron must not be larger than a specified value.

### Data for training DeepSEA

Training labels were computed from uniformly processed ENCODE and Roadmap Epigenomics data releases.

To prepare the input for the deep convolutional network model, we split the genome into 200-bp bins. For each bin we computed the label for all 919 chromatin features; a chromatin feature was labeled 1 if more than half of the 200-bp bin is in the peak region and 0 otherwise.

We focused on the set of 200-bp bins with at least one TF binding event, resulting in 521,636,200 bp of sequences (17% of whole genome), which was used for training and evaluating chromatin feature prediction performance. Each training sample consists of a 1,000-bp sequence from the human GRCh37 reference genome centered on each 200-bp bin and is paired with a label vector for 919 chromatin features. The 1,000-bp DNA sequence is represented by a 1,000 × 4 binary matrix, with columns corresponding to A, G, C and T. The 400-bp flanking regions at the two sides provide extra contextual information to the model.

Training and testing sets were split by chromosomes and strictly nonoverlapping. Chromosome 8 and 9 were excluded from training to test chromatin feature prediction performances, and the rest of the autosomes were used for training and validation. 4,000 samples on chromosome 7 spanning the genomic coordinates 30,508,751–35,296,850 were used as the validation set. All hyperparameters were selected on the basis of log likelihood of the validation set data. The validation set data was not used for training or testing.

The GRCh37/hg19 genome assembly was used for all analyses in this study.

### In silico saturated mutagenesis for analyzing predictive sequence features

To discover informative sequence features within any sequence, we performed computational mutation scanning to assess the effect of mutating every base of the input sequence (3,000 substitutions on a 1,000 bp sequence) on chromatin feature predictions. The effect of a base substitution on a specific chromatin feature prediction was measured by log2 fold change of odds or where P0 represents the probability predicted for the original sequence and P1 represents the probability predicted for the mutated sequence.

### Evaluation of the single-nucleotide sensitivity of chromatin feature prediction

Alignment files of ENCODE digital genomic footprinting (DGF) data were downloaded from http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeUwDgf/.

Variants were called with VarScan 2 (ref. 20) using default settings on DGF samples with at least 200 million total mapped reads. We then filtered the called variants to retain only variants with at least 20 reads supporting existence of each of the alleles and at least 100 reads in total.

To detect allelically imbalanced variants, we ran Fisher’s exact test to compute the P value under the null hypothesis of two alleles being equal. Variants with P <0.01 and reference allele frequency larger than 0.7 or less than 0.4 were retained for downstream analysis. This pipeline found roughly the same amount of reference allele–biased and alternative allele– biased variants. The DeepSEA predictions for the reference and alternative alleles were made by the DHS predictor for the same cell type as the DGF samples.

### Functional SNP prioritization

For positive standards we used single-nucleotide substitution variants annotated as regulatory mutations in the HGMD professional version 2014.4 (ref. 17), eQTL data from the GRASP 2.0.0.0 database with a P-value cutoff of 1 × 10−10 (ref. 1) and GWAS SNPs downloaded from the NHGRI GWAS Catalog on 17 July 2014 (ref. 18). Coding variants were filtered on the basis of the UCSC build hg19 knownGene track22 . 

To compute predicted chromatin effects of variants using the DeepSEA model, for each SNP, we obtained the 1,000-bp sequence centered on that variant based on the reference genome (specifically, the sequence is chosen so that the variant was located at the 500th nucleotide). Then we constructed a pair of sequences carrying either the reference or alternative allele at the variant position. To compute features for each positive and negative standard SNP, based on the chromatin feature predictions for every pair of sequences carrying a reference and an alternative allele, respectively, we computed 2 × 919 predicted chromatin effect features, which are the absolute differences between probability values and the relative log fold changes of odds.

The predicted chromatin effect features were computed for both forward and complementary sequences and then averaged.

### DeepSEA functional significance score

The functional significance score is computed on the basis of DeepSEA chromatin effect predictions and evolutionary information–derived scores. Specifically, the DeepSEA functional significance score for a variant is defined as the product of the geometric mean E value for predicted chromatin effects and the geometric mean E value for evolutionary conservation features. E values measure significance for each individual chromatin feature and evolutionary information–derived score. Specifically, for each predicted chromatin feature of a variant, we computed the E value as the proportion of 1000 Genomes SNPs19 with higher predicted chromatin effect magnitude on the same chromatin feature. The magnitude of the predicted chromatin effect on a chromatin feature for a variant is computed as the product of the absolute difference between probability values and the relative log fold change of odds. For each evolutionary conservation score, the E-value is the proportion of 1000 Genomes SNPs with higher score.

1,000,000 randomly selected 1000 Genomes SNPs were used for computing the empirical background distributions for the 919 predicted chromatin effect features and the four evolutionary information–derived scores. Functional significance scores were evaluated with the same evaluation standards as used in the functional variant prioritization models.

References
1. Leslie R, O’Donnell CJ, Johnson AD. Bioinformatics. 2014; 30:i185–i194. [PubMed: 24931982]
2. Ritchie GR, Dunham I, Zeggini E, Flicek P. Nat Methods. 2014; 11:294–296. [PubMed: 24487584]
3. Kircher M, et al. Nat Genet. 2014; 46:310–315. [PubMed: 24487276]
4. Fu Y, et al. Genome Biol. 2014; 15:480. [PubMed: 25273974]
5. Lee D, et al. Nat Genet. 2015; 47:955–961. [PubMed: 26075791]
6. Slattery M, et al. Trends Biochem Sci. 2014; 39:381–399. [PubMed: 25129887]
7. Benveniste D, Sonntag HJ, Sanguinetti G, Sproul D. Proc Natl Acad Sci USA. 2014; 111:13367–
13372. [PubMed: 25187560]
8. Whitaker JW, Chen Z, Wang W. Nat Methods. 2015; 12:265–272. [PubMed: 25240437]
9. ENCODE Project Consortium. Nature. 2012; 489:57–74. [PubMed: 22955616]
10. Kundaje A, et al. Nature. 2015; 518:317–330. [PubMed: 25693563]
11. Arvey A, Agius P, Noble WS, Leslie C. Genome Res. 2012; 22:1723–1734. [PubMed: 22955984]
12. Ghandi M, Lee D, Mohammad-Noori M, Beer MA. PLoS Comput Biol. 2014; 10:e1003711.
[PubMed: 25033408]
13. Neph S, et al. Nature. 2012; 489:83–90. [PubMed: 22955618]
14. Cowper-Sal·lari R, et al. Nat Genet. 2012; 44:1191–1198. [PubMed: 23001124]
15. De Gobbi M, et al. Science. 2006; 312:1215–1217. [PubMed: 16728641]
16. Weedon MN, et al. Nat Genet. 2014; 46:61–64. [PubMed: 24212882]
17. Stenson PD, et al. Hum Genet. 2014; 133:1–9. [PubMed: 24077912]
18. Welter D, et al. Nucleic Acids Res. 2014; 42:D1001–D1006. [PubMed: 24316577]
19. Abecasis GR, et al. Nature. 2012; 491:56–65. [PubMed: 23128226]
20. Koboldt DC, et al. Genome Res. 2012; 22:568–576. [PubMed: 22300766]
21. McVicker G, et al. Science. 2013; 342:747–749. [PubMed: 24136359]
22. Karolchik D, et al. Nucleic Acids Res. 2014; 42:D764–D770. [PubMed: 24270787]
23. Siepel A, et al. Genome Res. 2005; 15:1034–1050. [PubMed: 16024819]
24. Pollard KS, Hubisz MJ, Rosenbloom KR, Siepel A. Genome Res. 2010; 20:110–121. [PubMed:
19858363]
25. Cooper GM, et al. Genome Res. 2005; 15:901–913. [PubMed: 15965027]
26. Davydov EV, et al. PLoS Comput Biol. 2010; 6:e1001025. [PubMed: 21152010]

#nih #research #paper #good4pub #knowledge 