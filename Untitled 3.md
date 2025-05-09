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

### Citations:

1. [https://pubmed.ncbi.nlm.nih.gov/32483332/](https://pubmed.ncbi.nlm.nih.gov/32483332/)
2. [https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7610614/)
3. [https://pmc.ncbi.nlm.nih.gov/articles/PMC5315571/](https://pmc.ncbi.nlm.nih.gov/articles/PMC5315571/)
4. [https://lmu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01LMU_INST%3AHannon&lang=en&search_scope=Main_CDI&adaptor=Primo+Central&query=null%2C%2CDVD%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c375t-ce475158c4406dc4ef7c2859bc79a1dc75d4a84362f500dad5e080b5688535683&offset=0](https://lmu.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_pubmedcentral_primary_oai_pubmedcentral_nih_gov_7610614&context=PC&vid=01LMU_INST%3AHannon&lang=en&search_scope=Main_CDI&adaptor=Primo+Central&query=null%2C%2CDVD%2CAND&facet=citing%2Cexact%2Ccdi_FETCH-LOGICAL-c375t-ce475158c4406dc4ef7c2859bc79a1dc75d4a84362f500dad5e080b5688535683&offset=0)
5. [https://search.library.ucla.edu/discovery/openurl?institution=01UCS_LAL&rfr_id=info%3Asid%252Fprimo.exlibrisgroup.com-bX-Bx&rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3A&rft.epage=635&rft.volume=17&rft_id=info%3Adoi%2F&rfr_id=info%3Asid%2Fprimo.exlibrisgroup.com-163980448-Bx&resource_type=article&rft.isbn_list=&rft.jtitle=Nature+methods.&rft.genre=article&rft.issue=6&rft.eisbn_list=&rft.spage=629&rft.atitle=Targeted+Perturb-seq+enables+genome-scale+genetic+screens+in+single+cells&rft.issn=1548-7091&rft.eissn=1548-7105&svc_dat=CTO&vid=01UCS_LAL%3AUCLA&lang=en](https://search.library.ucla.edu/discovery/openurl?institution=01UCS_LAL&rfr_id=info%3Asid%252Fprimo.exlibrisgroup.com-bX-Bx&rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3A&rft.epage=635&rft.volume=17&rft_id=info%3Adoi%2F&rfr_id=info%3Asid%2Fprimo.exlibrisgroup.com-163980448-Bx&resource_type=article&rft.isbn_list=&rft.jtitle=Nature+methods.&rft.genre=article&rft.issue=6&rft.eisbn_list=&rft.spage=629&rft.atitle=Targeted+Perturb-seq+enables+genome-scale+genetic+screens+in+single+cells&rft.issn=1548-7091&rft.eissn=1548-7105&svc_dat=CTO&vid=01UCS_LAL%3AUCLA&lang=en)
6. [https://www.annualreviews.org/content/journals/10.1146/annurev-genet-072920-013842?TRACK=RSS](https://www.annualreviews.org/content/journals/10.1146/annurev-genet-072920-013842?TRACK=RSS)
7. [https://www.sciencedirect.com/science/article/pii/S0092867416316609](https://www.sciencedirect.com/science/article/pii/S0092867416316609)
8. [https://www.nature.com/articles/s41587-023-02003-3](https://www.nature.com/articles/s41587-023-02003-3)
9. [https://github.com/argschwind/TAPseq_manuscript](https://github.com/argschwind/TAPseq_manuscript)
10. [https://www.nature.com/articles/s41698-024-00576-z](https://www.nature.com/articles/s41698-024-00576-z)
11. [https://www.sciencedirect.com/science/article/pii/S266616672030112X](https://www.sciencedirect.com/science/article/pii/S266616672030112X)
12. [https://pmc.ncbi.nlm.nih.gov/articles/PMC11920212/](https://pmc.ncbi.nlm.nih.gov/articles/PMC11920212/)
13. [https://www.nature.com/articles/s41593-024-01794-1](https://www.nature.com/articles/s41593-024-01794-1)
14. [https://academic.oup.com/nar/article/53/D1/D1099/7815638](https://academic.oup.com/nar/article/53/D1/D1099/7815638)
15. [https://pmc.ncbi.nlm.nih.gov/articles/PMC11399228/](https://pmc.ncbi.nlm.nih.gov/articles/PMC11399228/)
16. [https://www.nature.com/articles/s41556-025-01626-9](https://www.nature.com/articles/s41556-025-01626-9)
17. [https://www.sciencedirect.com/science/article/pii/S0092867416316105](https://www.sciencedirect.com/science/article/pii/S0092867416316105)
18. [https://pmc.ncbi.nlm.nih.gov/articles/PMC9732527/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9732527/)
19. [https://www.nature.com/articles/s41467-023-39784-9](https://www.nature.com/articles/s41467-023-39784-9)
20. [https://www.rna-seqblog.com/tap-seq-increasing-the-scale-and-precision-of-functional-genomics-crispr-cas9-screens-with-targeted-single-cell-rna-sequencing/](https://www.rna-seqblog.com/tap-seq-increasing-the-scale-and-precision-of-functional-genomics-crispr-cas9-screens-with-targeted-single-cell-rna-sequencing/)
21. [https://pmc.ncbi.nlm.nih.gov/articles/PMC5526071/](https://pmc.ncbi.nlm.nih.gov/articles/PMC5526071/)
22. [https://www.nature.com/articles/s41587-023-01964-9](https://www.nature.com/articles/s41587-023-01964-9)
23. [https://www.biorxiv.org/content/10.1101/2021.12.16.473013v1.full](https://www.biorxiv.org/content/10.1101/2021.12.16.473013v1.full)
24. [https://www.sciencedirect.com/science/article/pii/S0092867422005979](https://www.sciencedirect.com/science/article/pii/S0092867422005979)
25. [https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5](https://experiments.springernature.com/articles/10.1038/s41592-020-0837-5)
26. [https://pmc.ncbi.nlm.nih.gov/articles/PMC7416462/](https://pmc.ncbi.nlm.nih.gov/articles/PMC7416462/)
27. [https://pmc.ncbi.nlm.nih.gov/articles/PMC10680627/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10680627/)
28. [https://pmc.ncbi.nlm.nih.gov/articles/PMC11601512/](https://pmc.ncbi.nlm.nih.gov/articles/PMC11601512/)
29. [https://www.nature.com/articles/s41597-019-0071-0](https://www.nature.com/articles/s41597-019-0071-0)
30. [https://pubmed.ncbi.nlm.nih.gov/32483332/](https://pubmed.ncbi.nlm.nih.gov/32483332/)
31. [https://pmc.ncbi.nlm.nih.gov/articles/PMC11906366/](https://pmc.ncbi.nlm.nih.gov/articles/PMC11906366/)

---

Answer from Perplexity: [pplx.ai/share](https://www.perplexity.ai/search/pplx.ai/share)