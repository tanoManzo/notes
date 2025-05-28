<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# give me more details of the paper and of the figures

Certainly! Here’s a more detailed summary of the paper **“Mapping the regulatory effects of common and rare non-coding variants across cellular and developmental contexts in the brain and heart”** (Jagadeesh, Cotter, et al., bioRxiv 2024), followed by in-depth figure-by-figure descriptions based on the preprint and supplementary materials.

---

# Detailed Paper Summary

### **Background and Motivation**

- Most disease-associated variants identified by GWAS are non-coding and likely act through cell type- and context-specific gene regulation.
- Understanding the regulatory impact of both common and rare non-coding variants, especially in the complex tissues of the brain and heart, is crucial for interpreting genetic risk for neurodevelopmental and cardiac diseases.


### **Approach**

- The authors generated and analyzed single-cell ATAC-seq data from over 800,000 cells spanning 132 cell types and developmental stages in human brain and heart.
- They trained deep learning models (ChromBPNet and FLARE) to predict chromatin accessibility and regulatory constraint at base-pair resolution in each context.
- Using these models, they predicted the regulatory effects of over 15 million common and rare variants (including de novo mutations from disease cohorts) in a context-specific manner.


### **Key Results**

- **Common variants**: Tend to have highly cell type- and context-specific regulatory effects, especially in adult cells.
- **Rare and de novo variants**: More likely to have broad effects across multiple cell types, especially in fetal neurons, and are under strong evolutionary constraint.
- **Disease relevance**: The context-specific regulatory predictions help prioritize variants associated with neurodevelopmental disorders (e.g., autism) and congenital heart disease (CHD).
- **FLARE constraint scores**: Outperform previous metrics for prioritizing pathogenic non-coding variants.
- **Molecular convergence**: Both rare and common variants converge on specific cell types and pathways, especially in heart development.

---

# Figure-by-Figure Details

## **Figure 1: Study Overview and Data Generation**

- **Panel A**: Schematic of the experimental workflow—tissue collection, single-cell ATAC-seq, cell type annotation, and model training.
- **Panel B**: UMAP plots showing clustering of single-cell chromatin accessibility profiles, colored by cell type and developmental stage (fetal vs. adult).
- **Panel C**: Overview of the deep learning pipeline (ChromBPNet/FLARE) for predicting chromatin accessibility and variant effects.

**Takeaway:** Establishes the breadth of the dataset and the computational approach.

---

## **Figure 2: Regulatory Effect Predictions Across Cell Types and Contexts**

- **Panel A**: Heatmap displaying the predicted regulatory effect (delta accessibility) of common and rare variants across 132 cell types.
- **Panel B**: Bar plots showing the number of variants with strong predicted effects in each cell type.
- **Panel C**: Scatterplots comparing the cell type-specificity of common vs. rare variant effects.
- **Panel D**: Examples of variants with highly context-specific vs. broad regulatory effects.

**Takeaway:** Common variants act in specific cell types; rare variants often have broader effects, especially in development.

---

## **Figure 3: Evolutionary Constraint and Disease Enrichment**

- **Panel A**: FLARE regulatory constraint scores across cell types; fetal neurons show the strongest constraint.
- **Panel B**: Enrichment of rare and de novo variants with strong regulatory effects near genes implicated in neurodevelopmental disorders and CHD.
- **Panel C**: Comparison of FLARE scores to other evolutionary metrics (e.g., GERP, PhyloP).
- **Panel D**: Distribution of FLARE scores for variants in disease cohorts vs. controls.

**Takeaway:** Regulatory constraint is strongest in fetal neurons; FLARE scores are better at identifying pathogenic variants.

---

## **Figure 4: Prioritization of Disease-Associated Non-coding Variants**

- **Panel A**: ROC and precision-recall curves comparing FLARE, CADD, and other scores for prioritizing de novo variants in autism and CHD.
- **Panel B**: Case study of a de novo variant near *CNTNAP2* with a high FLARE score, predicted to disrupt enhancer activity in fetal brain.
- **Panel C**: Distribution of prioritized variants in disease vs. control trios.

**Takeaway:** FLARE improves prioritization of pathogenic non-coding variants, especially for developmental disorders.

---

## **Figure 5: Integration with GWAS and QTL Data**

- **Panel A**: Overlay of predicted regulatory effects with GWAS loci for brain traits (e.g., schizophrenia, cognitive function) and heart traits (e.g., left ventricular mass).
- **Panel B**: Colocalization analysis showing overlap between predicted regulatory variants and eQTLs in relevant tissues.
- **Panel C**: Examples of cell type-specific regulatory variants at GWAS loci, highlighting causal cell types.

**Takeaway:** Context-specific predictions help link GWAS signals to causal regulatory mechanisms and cell types.

---

## **Figure 6: Molecular Convergence in Heart Development**

- **Panel A**: Single-cell multiomic maps of fetal heart, highlighting rare cell populations (e.g., valvular interstitial cells, fibroblasts).
- **Panel B**: Enrichment of both rare coding and non-coding variants in enhancers active in these cell types.
- **Panel C**: Network diagrams showing convergence of genetic risk on specific molecular pathways in heart development.

**Takeaway:** Genetic risk for CHD converges on specific cell types and pathways in the developing heart.

---

## **Figure 7: Case Studies and Experimental Validation**

- **Panel A**: Locus plots showing prioritized regulatory variants near disease genes (e.g., *CNTNAP2* in autism, cardiac genes in CHD).
- **Panel B**: Reporter assays or CRISPR perturbations validating the predicted effects of selected variants.
- **Panel C**: Schematic summarizing the workflow from variant prediction to functional validation.

**Takeaway:** Computational predictions are supported by experimental validation, demonstrating the utility of the approach.

---

## **Supplementary Figures**

- Additional analyses of model performance, variant effect distributions, cell type annotations, and extended case studies.

---

# Final Remarks

This study provides a foundational resource for understanding the regulatory landscape of non-coding variation in the brain and heart, with implications for disease genetics, variant interpretation, and functional genomics.

**If you need more details about a specific figure or want to see example data/plots, let me know!**

