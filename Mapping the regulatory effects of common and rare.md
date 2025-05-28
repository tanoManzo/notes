
Recent advances have enabled comprehensive mapping of the regulatory effects of both common and rare non-coding genetic variants across cellular and developmental contexts in the brain and heart. Here is a synthesis of the latest findings and methodologies:

## Large-Scale Variant Effect Prediction

Researchers have leveraged deep learning models, such as ChromBPNet and FLARE, trained on single-cell ATAC-seq data from 132 cellular contexts in adult and fetal brain and heart, to predict the regulatory effects of over 15 million common and rare variants—yielding nearly two billion context-specific predictions[^1][^3][^9][^8]. These predictions provide unprecedented resolution for understanding how non-coding variants influence gene regulation during human development and disease.

## Key Findings

- **Cell-Type and Developmental Specificity**:
    - *Common variants* tend to exert regulatory effects that are highly specific to particular cell types, especially in the adult brain and heart.
    - *Rare variants*, including ultra-rare and de novo mutations, more often have regulatory effects that are shared across multiple cell types, particularly during fetal development. This broad impact is especially notable in fetal brain neurons, where evolutionary constraint is strongest[^1][^3][^9].
- **Disease Relevance**:
    - The integration of deep learning predictions with GWAS and QTL data has revealed context-specific regulatory mechanisms underlying traits and diseases, such as neurodevelopmental disorders and congenital heart defects (CHD)[^1][^3][^4][^9].
    - FLARE, a context-aware model of regulatory constraint, outperforms previous methods in prioritizing de novo mutations with extreme regulatory effects, particularly in autism-affected families, highlighting rare regulatory variants near key neurodevelopmental genes like *CNTNAP2*[^1][^3][^9].
- **Evolutionary Constraint**:
    - Selective pressures are especially pronounced against variants that disrupt regulatory elements in fetal brain neurons, indicating the critical importance of these contexts for human development[^1][^3][^9].
- **Molecular Convergence in Heart Development**:
    - In the heart, both rare coding variants associated with CHD and common non-coding variants associated with structural traits converge on specific cell types, such as valvular interstitial cells (VICs) and cardiac fibroblasts, suggesting shared molecular pathways underlying diverse cardiac phenotypes[^2][^4][^5].
    - Single-cell multiomic maps from hundreds of thousands of fetal heart cells have enabled the identification of enhancers and regulatory elements active in rare cardiac cell populations, providing a framework for interpreting the polygenic risk of heart disease[^2][^4][^5].


## Methodological Advances

- **Deep Learning Models**:
    - ChromBPNet and FLARE enable high-throughput, context-specific prediction of regulatory variant effects, even in the absence of large population datasets[^3][^9][^8].
    - These models can be integrated with population genetics data to prioritize variants likely to disrupt regulatory function, addressing limitations of traditional QTL mapping.
- **Single-Cell Multiomics**:
    - High-resolution single-cell gene regulation maps now cover dozens of cell types and developmental stages in both brain and heart, allowing precise mapping of variant effects to specific cellular contexts[^2][^4][^5].


## Implications

- **Neurodevelopmental Disorders**:
    - The genetic contribution to rare neurodevelopmental disorders is predominantly driven by rare non-coding variants with broad regulatory effects, especially during early brain development[^1][^3][^9].
- **Cardiac Disease**:
    - Both common and rare non-coding variants play key roles in heart development and disease, with convergent effects on specific cell types and pathways[^2][^4][^5][^7].


## Summary Table

| Variant Type | Regulatory Effect Pattern | Disease Relevance | Key Cell Types/Contexts |
| :-- | :-- | :-- | :-- |
| Common | Cell-type-specific (adult) | GWAS loci for traits/diseases | Microglia (brain), VICs (heart), etc. |
| Rare | Cell-type-shared (fetal, broad) | Autism, CHD, neurodevelopmental | Fetal neurons, cardiac fibroblasts, VICs |

## Conclusion

Integrating deep learning-based variant effect prediction with single-cell regulatory maps and population genetics is transforming our understanding of non-coding genetic variation in the brain and heart. These efforts are illuminating the developmental and cell-type specificity of regulatory variants, clarifying their roles in disease, and providing foundational resources for future research and therapeutic development[^1][^3][^4][^9].

<div style="text-align: center">⁂</div>

[^1]: https://pubmed.ncbi.nlm.nih.gov/40027628/

[^2]: https://www.medrxiv.org/content/10.1101/2024.11.20.24317557v2.full-text

[^3]: https://www.biorxiv.org/content/10.1101/2025.02.18.638922v1.full-text

[^4]: https://pubmed.ncbi.nlm.nih.gov/39606363/

[^5]: https://www.medrxiv.org/content/10.1101/2024.11.20.24317557v2.full.pdf

[^6]: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4845174

[^7]: https://onlinelibrary.wiley.com/doi/10.1111/jcmm.17762

[^8]: https://www.biorxiv.org/content/10.1101/2025.02.18.638922v2.full.pdf

[^9]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11870466/

[^10]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11023684/

[^11]: https://www.nature.com/articles/s41467-024-52463-7

[^12]: https://github.com/kundajelab/neuro-variants

[^13]: https://x.com/biorxiv_genomic/status/1892190889641955397

[^14]: https://www.sciencedirect.com/science/article/pii/S167385272400002X

[^15]: https://www.sciencedirect.com/science/article/pii/S0168952521002535

[^16]: https://reporter.nih.gov/project-details/10869990

[^17]: https://www.protocols.io/view/tissue-dissociation-and-10x-multiome-for-fetal-hea-dkta4wie

[^18]: https://www.biorxiv.org/content/10.1101/2025.02.18.638922v2.full-text

[^19]: https://www.medrxiv.org/content/10.1101/2022.02.02.22270312v1.full-text

