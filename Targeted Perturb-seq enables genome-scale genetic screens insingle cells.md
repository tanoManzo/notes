## **Background and Motivation**

Single-cell CRISPR screens (like Perturb-seq and CROP-seq) have revolutionized functional genomics by enabling researchers to link genetic perturbations to transcriptomic changes at single-cell resolution. However, these approaches face two major limitations:

- **High sequencing costs:** Whole-transcriptome profiling is expensive, limiting the number of perturbations and cells that can be analyzed.
    
- **Low sensitivity:** Weak gene expression changes and effects on lowly expressed genes are often missed due to limited sequencing depth per gene and per cell[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Innovation: TAP-seq (Targeted Perturb-seq)**

TAP-seq addresses these challenges by focusing sequencing coverage exclusively on a panel of genes of interest, rather than the entire transcriptome[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://northumbrialibrarysearch.hosted.exlibrisgroup.com/primo-explore/fulldisplay?docid=TN_cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=northumbria&lang=en_US&search_scope=default_scope&adaptor=primo_central_multiple_fe&query=creator%2Cexact%2C+Kee%2C+Carmon+%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c6402-c87a2698f267609897b36922fdf5d723d3f0d067a6093f6e36607763c736d0943&offset=0). This targeted approach offers several advantages:

- **Massive increase in sensitivity:** By concentrating sequencing reads, TAP-seq detects weak effects and changes in lowly expressed genes that standard Perturb-seq often misses.
    
- **Dramatic reduction in cost:** Sequencing requirements are reduced by up to 50-fold, making genome-scale screens feasible.
    
- **Platform independence:** TAP-seq is compatible with various single-cell RNA-seq platforms, including 10X Genomics, Drop-seq, and others[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **High throughput:** Enables routine analysis of thousands of CRISPR perturbations in a single experiment[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://northumbrialibrarysearch.hosted.exlibrisgroup.com/primo-explore/fulldisplay?docid=TN_cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=northumbria&lang=en_US&search_scope=default_scope&adaptor=primo_central_multiple_fe&query=creator%2Cexact%2C+Kee%2C+Carmon+%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c6402-c87a2698f267609897b36922fdf5d723d3f0d067a6093f6e36607763c736d0943&offset=0)[4](https://cnu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01CNU_INST%3AVersion2&lang=en&search_scope=MyInst_and_CI&adaptor=Primo+Central&tab=Everything&query=sub%2Cequals%2C+RNA+%2CAND&mode=advanced&offset=70).
    

## **Methodology**

**1. Experimental Design**

- Cells are transduced with a pooled CRISPR guide RNA (gRNA) library, with each cell typically receiving a single gRNA.
    
- After perturbation, single-cell RNA-seq libraries are prepared.
    
- Instead of sequencing the whole transcriptome, TAP-seq uses PCR to selectively amplify a pre-defined set of target genes from the cDNA, focusing sequencing on these genes[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[5](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).
    
- Both the identity of the perturbation (gRNA) and the expression levels of the targeted genes are read out for each cell.
    

**2. Evaluation and Benchmarking**

- The authors designed primer panels targeting between 74 and 198 genes, covering a wide range of expression levels and cell types (including K562 cells and mouse cell lines)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- With TAP-seq, 87–96% of sequencing reads mapped to the selected targets, compared to only a small fraction in whole-transcriptome approaches[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- Even with a larger panel of 1,000 genes, mapping rates remained high (81%)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- TAP-seq captured gRNA identity with 95% efficiency, outperforming standard Perturb-seq (39% efficiency)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

**3. Sensitivity and Performance**

- TAP-seq achieves the same statistical power for detecting differential gene expression at **19–49 times lower sequencing depth** compared to Perturb-seq[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- The method can detect absolute expression changes as small as ~0.03 UMI/cell (about one transcript molecule per cell)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- TAP-seq robustly distinguishes cell subtypes and differentiation stages, even with as few as 100 sequencing reads per cell[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Key Applications and Results**

**1. Enhancer–Target Gene Mapping**

- The authors used TAP-seq to functionally map 1,778 putative enhancers across 2.5% of the human genome.
    
- By perturbing these enhancers and profiling the effects on nearby gene expression, they generated high-confidence enhancer–target gene maps based on functional evidence, not just chromatin or 3D genome predictions[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- They found that **enhancer–target associations are determined by both 3D chromatin contact frequency and epigenetic state**, allowing accurate prediction of enhancer targets genome-wide[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

**2. Precision and False Positives**

- TAP-seq’s targeted approach reduces the multiple hypothesis testing burden, increasing precision and reducing false positives compared to hypothesis-free (whole-transcriptome) screens[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- The authors recommend hypothesis-driven analysis for single-cell CRISPR screens to maximize sensitivity and reliability[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Technical Insights and Recommendations**

- TAP-seq’s modular design allows easy adaptation to different gene panels and experimental questions.
    
- The method is robust across cell types, including primary cells and cell lines[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- The authors provide detailed guidelines for experimental design, including panel size, sequencing depth, and statistical analysis, to optimize TAP-seq screens[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Conclusions and Impact**

- **TAP-seq enables genome-scale, single-cell CRISPR screens with transcriptomic readouts at a fraction of the cost and with much higher sensitivity than previous methods.**
    
- The approach is broadly applicable to mapping gene regulatory networks, dissecting enhancer function, and identifying cell states and subtypes.
    
- By making large-scale, high-resolution functional genomics screens practical, TAP-seq accelerates the discovery of gene function and regulatory mechanisms in health and disease[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://northumbrialibrarysearch.hosted.exlibrisgroup.com/primo-explore/fulldisplay?docid=TN_cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=northumbria&lang=en_US&search_scope=default_scope&adaptor=primo_central_multiple_fe&query=creator%2Cexact%2C+Kee%2C+Carmon+%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c6402-c87a2698f267609897b36922fdf5d723d3f0d067a6093f6e36607763c736d0943&offset=0)[4](https://cnu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01CNU_INST%3AVersion2&lang=en&search_scope=MyInst_and_CI&adaptor=Primo+Central&tab=Everything&query=sub%2Cequals%2C+RNA+%2CAND&mode=advanced&offset=70)[5](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).
    

**In summary:**  
TAP-seq is a transformative advance for single-cell CRISPR screening, enabling sensitive, cost-effective, and scalable genetic screens that can map regulatory elements and gene networks with unprecedented resolution and efficiency.


## **Figure 1: TAP-seq Design and Targeting Efficiency**

- **Panel a:**  
    Schematic overview of the TAP-seq method. This illustration shows how, after pooled CRISPR perturbation, single-cell RNA-seq libraries are generated. Instead of sequencing the entire transcriptome, TAP-seq uses targeted PCR to amplify only genes of interest from each cell’s cDNA, focusing sequencing coverage on these targets rather than the whole transcriptome.
    
- **Panel b:**  
    Experimental workflow for TAP-seq, including CRISPR perturbation, single-cell encapsulation, cDNA synthesis, targeted amplification, and sequencing.
    
- **Panel c:**  
    Bar plots showing the fraction of sequencing reads mapping to target genes for different primer panels and cell types. Across panels targeting 74–198 genes, 87–96% of reads map to the intended targets, demonstrating high specificity and efficiency. Even with a larger 1,000-gene panel, mapping remains high (81%)-indicating low off-target amplification[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **Panel d:**  
    Comparison of TAP-seq and whole-transcriptome sequencing for quantifying gene expression. Scatter plots or correlation coefficients demonstrate that TAP-seq quantification is highly reproducible (Pearson R = 0.98 between replicates) and correlates well with whole-transcriptome data, validating the method’s accuracy[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Figure 2: Sensitivity and Performance of TAP-seq**

- **Panel a:**  
    Schematic or summary of the experimental design for benchmarking TAP-seq against whole-transcriptome Perturb-seq. Both approaches are run in parallel using the same CRISPR perturbation pool and cell population.
    
- **Panel b:**  
    Box plots or histograms showing the number of cells and sequencing reads per gRNA for TAP-seq vs. Perturb-seq. TAP-seq achieves high coverage per gRNA with much lower sequencing depth, highlighting its efficiency[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **Panel c:**  
    Bar graph comparing the efficiency of gRNA capture between TAP-seq and standard Perturb-seq. TAP-seq captures gRNA identity in 95% of cells, compared to 39% for standard Perturb-seq, and 89% for Perturb-seq with targeted gRNA amplification[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **Panel d:**  
    Plots showing the statistical power for detecting differential gene expression as a function of sequencing depth. TAP-seq achieves equivalent power at 19–49 times lower sequencing depth than Perturb-seq, demonstrating its superior sensitivity for both strong and weak gene expression changes[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Figure 3: Genome-scale Functional Mapping of Enhancer–Target Gene Pairs**

- **Panel a:**  
    Schematic of the large-scale enhancer perturbation experiment. All 1,778 putatively active enhancers in two regions of the human genome (chromosomes 8 and 11) are targeted with CRISPR, and effects on nearby gene expression are measured using TAP-seq.
    
- **Panel b:**  
    Heatmap or matrix showing enhancer–target gene associations. Each row represents an enhancer, each column a gene, and each cell the effect size or statistical significance of the enhancer’s perturbation on gene expression. This visualizes the functionally mapped enhancer–target gene network, revealing both known and novel regulatory relationships[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **Panel c:**  
    Analysis of the determinants of enhancer–target associations. Plots demonstrate that both 3D chromatin contact frequency (e.g., Hi-C data) and epigenetic state (e.g., histone marks) contribute to the likelihood and strength of enhancer–target gene connections, supporting the idea that both proximity and chromatin context are important[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Figure 4: Cell Type and State Identification at Low Sequencing Depth**

- **Panel a:**  
    Schematic or summary of downsampling experiments to test how well TAP-seq can distinguish cell types and states at varying sequencing depths.
    
- **Panel b:**  
    Clustering results showing that even with as few as 100 reads per cell, TAP-seq reliably distinguishes cell types and differentiation stages, matching ground truth labels from deeply sequenced reference data.
    
- **Panel c/d:**  
    Quantitative comparison of TAP-seq and whole-transcriptome approaches for cell type identification at different sequencing depths. TAP-seq achieves similar or better performance at 7–12-fold lower sequencing depth, demonstrating its efficiency for cell state mapping[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Summary Table**

|Figure|Main Focus|Key Message|
|---|---|---|
|1|TAP-seq method and targeting efficiency|TAP-seq robustly and specifically amplifies target genes, with high mapping and reproducibility|
|2|Sensitivity and gRNA capture|TAP-seq is more sensitive and captures gRNA identity more efficiently than Perturb-seq|
|3|Enhancer–target gene mapping|TAP-seq enables genome-scale, functional mapping of enhancer–gene relationships|
|4|Cell state identification at low depth|TAP-seq distinguishes cell types/states with minimal sequencing, outperforming whole-transcriptome|

**In summary:**  
Each figure demonstrates a key advantage of TAP-seq: Figure 1 validates the method’s specificity and reproducibility; Figure 2 shows its sensitivity and efficiency; Figure 3 highlights its power for large-scale functional genomics (e.g., enhancer mapping); Figure 4 proves its ability to resolve cell types and states at extremely low sequencing cost[1](https://pubmed.ncbi.nlm.nih.gov/32483332/)[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[4](https://lmu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01LMU_INST%3AHannon&lang=en&search_scope=Main_CDI&adaptor=Primo+Central&query=null%2C%2CDVD%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c375t-ce475158c4406dc4ef7c2859bc79a1dc75d4a84362f500dad5e080b5688535683&offset=0).

## Comprehensive Overview of Extended Data Figures in the TAP-seq Paper

The Extended Data Figures in "Targeted Perturb-seq enables genome-scale genetic screens in single cells" (PMID: 32483332) provide critical technical validations, statistical analyses, and biological insights that complement the main findings. Below is a detailed breakdown organized by thematic groups and their relationship to the main figures.

## **1. Technical Validation**

**Related Main Figure:** Figure 1  
**Extended Data Figures:** 1–5

## **Extended Data Figure 1**

- **Content:** Bioanalyzer traces comparing TAP-seq libraries to standard 10X Genomics libraries.
    
- **Purpose:** Validates the quality and size distribution of TAP-seq libraries, confirming that targeted amplification does not introduce biases or artifacts[1](http://europepmc.org/article/MED/32483332).
    

## **Extended Data Figure 2**

- **Content:** Target gene selection across three primer panels (74–198 genes) for different cell types (K562, mouse cell lines, primary cells).
    
- **Purpose:** Demonstrates the flexibility of TAP-seq across cell types and primer panel sizes, ensuring broad applicability[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Extended Data Figure 3**

- **Content:** Analysis of a larger 1,000-gene panel with 81% mapping efficiency.
    
- **Purpose:** Shows scalability of TAP-seq to genome-scale screens while maintaining high specificity[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Extended Data Figure 4**

- **Content:** Superior sensitivity of TAP-seq at 10–100× lower sequencing depth compared to whole-transcriptome methods.
    
- **Purpose:** Quantifies the cost-effectiveness and sensitivity gains of TAP-seq, critical for large-scale screens[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Extended Data Figure 5**

- **Content:** Reproducibility (Pearson _R_ = 0.98) and correlation with whole-transcriptome data (Pearson _R_ = 0.56–0.86).
    
- **Purpose:** Confirms that TAP-seq reliably reproduces gene expression patterns observed in untargeted approaches[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

**Complement to Main Findings:** These figures establish TAP-seq as a robust and reproducible method, validating its technical performance across cell types, panel sizes, and sequencing depths[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).

## **2. Statistical Performance**

**Related Main Figure:** Figure 2  
**Extended Data Figures:** 6–8

## **Extended Data Figure 6**

- **Content:** gRNA capture efficiency (95% in TAP-seq vs. 39% in standard Perturb-seq) and gene-specific coverage.
    
- **Purpose:** Highlights TAP-seq’s ability to reliably link perturbations to transcriptomic changes, reducing dropout rates[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Extended Data Figure 7**

- **Content:** Statistical test selection for differential expression analysis (e.g., MAST vs. Wilcoxon).
    
- **Purpose:** Identifies optimal statistical frameworks for detecting weak effects, crucial for enhancer-target mapping[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

## **Extended Data Figure 8**

- **Content:** Precision-recall curves showing equivalent performance at 19–49× lower sequencing depth.
    
- **Purpose:** Quantifies TAP-seq’s ability to detect subtle expression changes (as low as 0.03 UMI/cell) with high precision[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    

**Complement to Main Findings:** These figures underpin the statistical rigor of TAP-seq, demonstrating its superiority over whole-transcriptome approaches in sensitivity and cost efficiency[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).

## **3. Biological Applications**

**Related Main Figures:** Figures 3–4  
**Extended Data Figures:** 9–10

## **Extended Data Figure 9**

- **Content:** Detailed analysis of enhancer-target pairs (ETPs), including genomic distribution, validation against published enhancer maps, and machine-learning predictions.
    
    - Subpanels:
        
        - **9a,b:** Design and validation of enhancer perturbations.
            
        - **9e,f,g:** Enhancer proximity to TSS and expression levels of intervening genes.
            
        - **9h,i:** Genome-wide predictions of ETPs using 3D contact frequency and epigenetic features[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).
            
- **Purpose:** Provides functional evidence for enhancer-target relationships, surpassing predictions from chromatin conformation data alone[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).
    

## **Extended Data Figure 10**

- **Content:** Cell type identification with minimal sequencing (100 reads/cell) and comparison to whole-transcriptome methods.
    
- **Purpose:** Demonstrates TAP-seq’s utility in resolving cell subtypes and differentiation stages at ultra-low sequencing depths[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).
    

**Complement to Main Findings:** These figures showcase TAP-seq’s biological relevance, enabling functional enhancer mapping and cell state analysis in diverse contexts[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).

## **Summary Table**

|Thematic Group|Extended Data Figures|Key Contribution|
|---|---|---|
|Technical Validation|1–5|Validates library quality, panel flexibility, and reproducibility.|
|Statistical Performance|6–8|Establishes sensitivity, statistical frameworks, and cost efficiency.|
|Biological Applications|9–10|Maps enhancer-target networks and enables cell typing at low sequencing depth.|

## **How Extended Data Figures Enhance the Main Paper**

- **Technical Validation:** Confirms TAP-seq’s robustness across cell types and experimental scales, addressing potential concerns about targeted amplification[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **Statistical Performance:** Provides the mathematical foundation for TAP-seq’s sensitivity, ensuring reliable detection of weak regulatory effects[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/).
    
- **Biological Applications:** Expands on functional enhancer mapping and cell state identification, directly linking genetic perturbations to phenotypic outcomes[2](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)[3](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5).
    

By integrating these extended analyses, the paper solidifies TAP-seq as a transformative tool for genome-scale functional genomics in single cells.

### Citations:

1. [http://europepmc.org/article/MED/32483332](http://europepmc.org/article/MED/32483332)
2. [https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)
3. [https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5)
4. [https://cdn.10xgenomics.com/image/upload/v1660261285/support-documents/CG000234_TechnicalNote_CellTypeAnnotationUsingATAC_RevB.pdf](https://cdn.10xgenomics.com/image/upload/v1660261285/support-documents/CG000234_TechnicalNote_CellTypeAnnotationUsingATAC_RevB.pdf)
5. [https://pubmed.ncbi.nlm.nih.gov/32483332/](https://pubmed.ncbi.nlm.nih.gov/32483332/)
6. [https://edoc.mdc-berlin.de/id/eprint/24063/1/24063oa.pdf](https://edoc.mdc-berlin.de/id/eprint/24063/1/24063oa.pdf)
7. [https://www.nature.com/articles/s41586-024-08443-4](https://www.nature.com/articles/s41586-024-08443-4)
8. [https://www.biorxiv.org/lookup/content/full/2024.01.13.575500v1](https://www.biorxiv.org/lookup/content/full/2024.01.13.575500v1)
9. [https://academic.oup.com/nar/article/53/D1/D1099/7815638](https://academic.oup.com/nar/article/53/D1/D1099/7815638)
10. [https://www.nature.com/articles/s41556-025-01626-9](https://www.nature.com/articles/s41556-025-01626-9)
11. [https://www.protocols.io/view/mapping-enhancer-gene-interactions-with-direct-cap-d6759hq6.html](https://www.protocols.io/view/mapping-enhancer-gene-interactions-with-direct-cap-d6759hq6.html)
12. [https://www.nature.com/articles/s41587-020-0470-y](https://www.nature.com/articles/s41587-020-0470-y)
13. [https://www.nature.com/articles/s41586-024-07517-7](https://www.nature.com/articles/s41586-024-07517-7)
14. [https://academic.oup.com/bioinformatics/article/40/9/btae535/7750392](https://academic.oup.com/bioinformatics/article/40/9/btae535/7750392)
15. [https://pmc.ncbi.nlm.nih.gov/articles/PMC5181115/](https://pmc.ncbi.nlm.nih.gov/articles/PMC5181115/)
16. [https://www.nature.com/articles/s41467-024-55428-y](https://www.nature.com/articles/s41467-024-55428-y)
17. [https://www.biorxiv.org/content/10.1101/503367v1](https://www.biorxiv.org/content/10.1101/503367v1)
18. [https://www.biorxiv.org/content/10.1101/2024.01.13.575500v1](https://www.biorxiv.org/content/10.1101/2024.01.13.575500v1)
19. [https://experiments.springernature.com/articles/10.1038/s41592-023-02144-y](https://experiments.springernature.com/articles/10.1038/s41592-023-02144-y)
20. [https://github.com/josephreplogle/guide_calling](https://github.com/josephreplogle/guide_calling)
21. [https://www.nature.com/articles/s41587-023-01964-9](https://www.nature.com/articles/s41587-023-01964-9)
22. [https://www.agilent.com/cs/library/usermanuals/public/2100_Bioanalyzer_Expert_USR.pdf](https://www.agilent.com/cs/library/usermanuals/public/2100_Bioanalyzer_Expert_USR.pdf)
23. [https://pmc.ncbi.nlm.nih.gov/articles/PMC9546772/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9546772/)
24. [https://www.agilent.com/cs/library/applications/5989-1165EN.pdf](https://www.agilent.com/cs/library/applications/5989-1165EN.pdf)
25. [https://www.biorxiv.org/content/10.1101/2023.01.29.526143v1.full](https://www.biorxiv.org/content/10.1101/2023.01.29.526143v1.full)
26. [https://www.broadinstitute.org/files/publications/2024/05/nihms-1816171.pdf](https://www.broadinstitute.org/files/publications/2024/05/nihms-1816171.pdf)
27. [https://www.biorxiv.org/content/biorxiv/early/2023/11/13/2023.11.09.563812/DC1/embed/media-1.pdf?download=true](https://www.biorxiv.org/content/biorxiv/early/2023/11/13/2023.11.09.563812/DC1/embed/media-1.pdf?download=true)
28. [https://ipmb.sinica.edu.tw/microarray/index.files/Agilent%202100%20Bioanalyzer%20user%20guide.pdf](https://ipmb.sinica.edu.tw/microarray/index.files/Agilent%202100%20Bioanalyzer%20user%20guide.pdf)
29. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10830412/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10830412/)
30. [https://pmc.ncbi.nlm.nih.gov/articles/PMC9800413/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9800413/)
31. [https://www.sciencedirect.com/science/article/pii/S2666166723000837](https://www.sciencedirect.com/science/article/pii/S2666166723000837)
32. [https://www.sciencedirect.com/science/article/pii/S0092867422005979](https://www.sciencedirect.com/science/article/pii/S0092867422005979)
33. [https://www.nature.com/articles/s41586-023-06936-2](https://www.nature.com/articles/s41586-023-06936-2)
34. [https://durham-repository.worktribe.com/preview/1200581/37528.pdf](https://durham-repository.worktribe.com/preview/1200581/37528.pdf)
35. [https://www.nature.com/articles/s41477-024-01741-9](https://www.nature.com/articles/s41477-024-01741-9)
36. [https://www.rna-seqblog.com/tap-seq-increasing-the-scale-and-precision-of-functional-genomics-crispr-cas9-screens-with-targeted-single-cell-rna-sequencing/](https://www.rna-seqblog.com/tap-seq-increasing-the-scale-and-precision-of-functional-genomics-crispr-cas9-screens-with-targeted-single-cell-rna-sequencing/)
37. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10030154/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10030154/)
38. [https://www.nature.com/articles/s41587-022-01522-9](https://www.nature.com/articles/s41587-022-01522-9)
39. [https://www.sciencedirect.com/science/article/pii/S0092867416316105](https://www.sciencedirect.com/science/article/pii/S0092867416316105)
40. [https://pmc.ncbi.nlm.nih.gov/articles/PMC7652380/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7652380/)
41. [https://www.nature.com/articles/s41586-023-06570-y](https://www.nature.com/articles/s41586-023-06570-y)
42. [https://www.nature.com/articles/s41592-024-02360-0](https://www.nature.com/articles/s41592-024-02360-0)
43. [https://www.urmc.rochester.edu/MediaLibraries/URMCMedia/research/for-researchers/shared-resource-labs-facilities/rochester-genomics-center/images/Interpretation-of-BioanalyzerPPT_071921_Final_SD_EMP.pdf](https://www.urmc.rochester.edu/MediaLibraries/URMCMedia/research/for-researchers/shared-resource-labs-facilities/rochester-genomics-center/images/Interpretation-of-BioanalyzerPPT_071921_Final_SD_EMP.pdf)
44. [https://www.nature.com/articles/s41564-023-01462-3](https://www.nature.com/articles/s41564-023-01462-3)
45. [https://www.biorxiv.org/content/10.1101/2024.12.08.627374v1.full-text](https://www.biorxiv.org/content/10.1101/2024.12.08.627374v1.full-text)
46. [https://www.sciencedirect.com/science/article/pii/S1016847824001729](https://www.sciencedirect.com/science/article/pii/S1016847824001729)
47. [https://github.com/argschwind/TAPseq](https://github.com/argschwind/TAPseq)
48. [https://www.bioconductor.org/packages/devel/bioc/vignettes/TAPseq/inst/doc/tapseq_target_genes.html](https://www.bioconductor.org/packages/devel/bioc/vignettes/TAPseq/inst/doc/tapseq_target_genes.html)
49. [https://www.nature.com/articles/s41592-021-01252-x](https://www.nature.com/articles/s41592-021-01252-x)
50. [https://pmc.ncbi.nlm.nih.gov/articles/PMC11569274/](https://pmc.ncbi.nlm.nih.gov/articles/PMC11569274/)
51. [https://www.biorxiv.org/content/10.1101/2024.05.31.596895v1.full.pdf](https://www.biorxiv.org/content/10.1101/2024.05.31.596895v1.full.pdf)
52. [https://www.bakerlab.org/wp-content/uploads/2022/11/s41587-022-01510-z.pdf](https://www.bakerlab.org/wp-content/uploads/2022/11/s41587-022-01510-z.pdf)
53. [https://www.sciencedirect.com/science/article/pii/S0092867420312538](https://www.sciencedirect.com/science/article/pii/S0092867420312538)
54. [https://www.nature.com/articles/s41586-022-05046-9](https://www.nature.com/articles/s41586-022-05046-9)
55. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10584689/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10584689/)
56. [https://www.annualreviews.org/doi/abs/10.1146/annurev-genet-072920-013842](https://www.annualreviews.org/doi/abs/10.1146/annurev-genet-072920-013842)
57. [https://www.nature.com/articles/s41551-024-01204-8](https://www.nature.com/articles/s41551-024-01204-8)
58. [https://chiulab.med.harvard.edu/sites/projects.iq.harvard.edu/files/li_et_al_nature_24.pdf](https://chiulab.med.harvard.edu/sites/projects.iq.harvard.edu/files/li_et_al_nature_24.pdf)
59. [https://www.sciencedirect.com/science/article/pii/S1016847823001796](https://www.sciencedirect.com/science/article/pii/S1016847823001796)
60. [https://www.biorxiv.org/content/10.1101/2024.07.12.603288v2.full-text](https://www.biorxiv.org/content/10.1101/2024.07.12.603288v2.full-text)
61. [https://www.biorxiv.org/content/10.1101/2024.12.08.627402v1.full-text](https://www.biorxiv.org/content/10.1101/2024.12.08.627402v1.full-text)
62. [https://www.nature.com/articles/s41592-023-01840-z](https://www.nature.com/articles/s41592-023-01840-z)
63. [https://www.biorxiv.org/content/10.1101/2023.05.15.540875v3.full-text](https://www.biorxiv.org/content/10.1101/2023.05.15.540875v3.full-text)
64. [https://pmc.ncbi.nlm.nih.gov/articles/PMC9288987/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9288987/)
65. [https://www.sciencedirect.com/science/article/pii/S266616672030112X](https://www.sciencedirect.com/science/article/pii/S266616672030112X)
66. [https://pmc.ncbi.nlm.nih.gov/articles/PMC7416462/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7416462/)
67. [https://www.biorxiv.org/content/10.1101/2021.03.31.437978v1.full.pdf](https://www.biorxiv.org/content/10.1101/2021.03.31.437978v1.full.pdf)
68. [https://onlinelibrary.wiley.com/doi/full/10.1002/advs.202204484](https://onlinelibrary.wiley.com/doi/full/10.1002/advs.202204484)
69. [https://www.nature.com/articles/s41587-022-01551-4](https://www.nature.com/articles/s41587-022-01551-4)
70. [https://genome.cshlp.org/content/early/2022/04/29/gr.275870.121.full.pdf](https://genome.cshlp.org/content/early/2022/04/29/gr.275870.121.full.pdf)
71. [https://www.biorxiv.org/content/10.1101/2024.07.12.603288v1.full-text](https://www.biorxiv.org/content/10.1101/2024.07.12.603288v1.full-text)
72. [https://www.hubrecht.eu/app/uploads/2021/11/VanOudenaarden_2021_Nature_VanInsberghe_compressed.pdf](https://www.hubrecht.eu/app/uploads/2021/11/VanOudenaarden_2021_Nature_VanInsberghe_compressed.pdf)
73. [https://www.biorxiv.org/content/10.1101/2021.03.31.437978.full](https://www.biorxiv.org/content/10.1101/2021.03.31.437978.full)
74. [https://www.rna-seqblog.com/perturb-seq-enables-large-scale-analysis-of-complex-genetic-interactions-using-crispr-based-gene-perturbation-and-single-cell-rna-sequencing/](https://www.rna-seqblog.com/perturb-seq-enables-large-scale-analysis-of-complex-genetic-interactions-using-crispr-based-gene-perturbation-and-single-cell-rna-sequencing/)
75. [https://www.nature.com/articles/s41467-025-59306-z](https://www.nature.com/articles/s41467-025-59306-z)
76. [https://academic.oup.com/bioinformatics/article/39/2/btad062/7008325](https://academic.oup.com/bioinformatics/article/39/2/btad062/7008325)
77. [https://www.biorxiv.org/content/biorxiv/early/2025/03/07/2025.01.22.634371.full.pdf](https://www.biorxiv.org/content/biorxiv/early/2025/03/07/2025.01.22.634371.full.pdf)
78. [https://www.biorxiv.org/content/10.1101/2024.11.23.624931v1.full-text](https://www.biorxiv.org/content/10.1101/2024.11.23.624931v1.full-text)
79. [https://pmc.ncbi.nlm.nih.gov/articles/PMC7116838/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7116838/)
80. [https://www.biorxiv.org/content/10.1101/2024.08.21.609075v3.full](https://www.biorxiv.org/content/10.1101/2024.08.21.609075v3.full)
81. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10680627/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10680627/)
82. [https://www.science.org/doi/10.1126/science.abj3013](https://www.science.org/doi/10.1126/science.abj3013)
83. [https://www.sciencedirect.com/science/article/pii/S2666979X23001179](https://www.sciencedirect.com/science/article/pii/S2666979X23001179)
84. [https://www.sciencedirect.com/science/article/pii/S0006497121009575](https://www.sciencedirect.com/science/article/pii/S0006497121009575)
85. [https://www.nature.com/articles/s41587-024-02213-3](https://www.nature.com/articles/s41587-024-02213-3)
86. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10070275/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10070275/)
87. [https://www.biorxiv.org/content/10.1101/2023.11.09.563812v1.full.pdf](https://www.biorxiv.org/content/10.1101/2023.11.09.563812v1.full.pdf)
88. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10638471/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10638471/)
89. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10568495/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10568495/)
90. [https://www.sciencedirect.com/science/article/pii/S2666979X2500062X](https://www.sciencedirect.com/science/article/pii/S2666979X2500062X)
91. [https://lmu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01LMU_INST%3AHannon&lang=en&search_scope=Main_CDI&adaptor=Primo+Central&query=null%2C%2CDVD%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c375t-ce475158c4406dc4ef7c2859bc79a1dc75d4a84362f500dad5e080b5688535683&offset=0](https://lmu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01LMU_INST%3AHannon&lang=en&search_scope=Main_CDI&adaptor=Primo+Central&query=null%2C%2CDVD%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c375t-ce475158c4406dc4ef7c2859bc79a1dc75d4a84362f500dad5e080b5688535683&offset=0)
92. [https://www.embopress.org/doi/10.15252/msb.20209873](https://www.embopress.org/doi/10.15252/msb.20209873)
93. [https://www.sciencedirect.com/science/article/pii/S2001037024001417](https://www.sciencedirect.com/science/article/pii/S2001037024001417)
94. [https://experiments.springernature.com/techniques/perturb-seq](https://experiments.springernature.com/techniques/perturb-seq)
95. [https://www.10xgenomics.com/analysis-guides/quality-assessment-using-the-cell-ranger-web-summary](https://www.10xgenomics.com/analysis-guides/quality-assessment-using-the-cell-ranger-web-summary)
96. [https://www.bioconductor.org/packages/devel/bioc/manuals/TAPseq/man/TAPseq.pdf](https://www.bioconductor.org/packages/devel/bioc/manuals/TAPseq/man/TAPseq.pdf)
97. [https://github.com/Katsevich-Lab/import-schraivogel-2020](https://github.com/Katsevich-Lab/import-schraivogel-2020)
98. [https://www.bioconductor.org/packages/release/bioc/html/TAPseq.html](https://www.bioconductor.org/packages/release/bioc/html/TAPseq.html)

---

Answer from Perplexity: [pplx.ai/share](https://www.perplexity.ai/search/pplx.ai/share)