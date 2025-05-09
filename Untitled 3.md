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