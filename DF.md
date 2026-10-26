
## 1. New biological findings

- **Attribution identifies which motif matches are bound.** Within active enhancers, attribution separates ChIP-occupied from unoccupied motif matches far better than motif strength (median AUROC 0.74 vs 0.58, 110 TFs). This holds on held-out chromosomes and replicates in K562 (40 TFs) (Fig. 3F; Supp. Tables 5, 5b).

- **Layered liver enhancer grammar.** Summit-resolved occupancy of 423 TFs across 20,833 HepG2 enhancers shows HNF4A and FOXA1/2 at the core. Nuclear-receptor, insulin-responsive and developmental regulators are added in the most complex enhancers.

- **Co-bound factors converge on a nucleosome-sized core.** All 380 pairs of frequently bound TFs show this, including cofactors that do not bind DNA (median 1.8-fold closer than a cross-enhancer null) (Fig. 4A/4D; Supp. Table 8).

- **AP-1–forkhead adjacency** is a partner-specific arrangement at attribution-supported sites (Supp. Table 8c).

- **Footprints sit where TF binding occurs.** The strongest 11 bp footprint lies within 100 bp of the peak centre in 52% of 223,703 peaks (10% expected), without the summit position being given to the model (Fig. 2A/2D).

  

## 2. Stronger validation

- **Allele-specific binding (ADASTRA).** Variants are enriched 2.6-fold at high-attribution bases against a local null. The model identifies the preferred allele better than the TF's motif (AUROC 0.71 vs 0.58) (Fig. 2E; Supp. Table 2).

- **SNP-SELEX.** The test now uses measured preferential-binding SNPs (21 TFs, 3,074 SNPs) (Fig. 2G; Supp. Table 6).

- **Saturation mutagenesis.** All HepG2 libraries are included: SORT1 (3 libraries), LDLR and F9. DeepFootprinting reaches r = 0.24–0.43 versus 0.09–0.18 for JASPAR (Fig. 5F; Supp. Tables 3, 7).

- **rs12740374.** The causal C/EBP-creating allele at the SORT1 LDL-cholesterol locus ranks among the top 0.1% of activating substitutions.

- **Leakage controls.** Ablating Phase I features (the target TF's own prediction, all HepG2 features, or all TF-binding features) leaves accuracy unchanged. The chromosome 8/9 holdout was verified.

  

## 3. Comparison with leading models on identical variants (Fig. 5D; Supp. Tables 4, 4b)

| Benchmark | DeepFootprinting | AlphaGenome | Enformer (HepG2 DNase) | Sei | Borzoi | Best fine-tuned DNA LM |

|---|---|---|---|---|---|---|

| 14,088 HepG2 raQTLs (r) | **0.31** | 0.30 | 0.27 | 0.28 | 0.12 | 0.16 (NT-2.5B) |

| SORT1 mutagenesis MPRA (r) | 0.37 | **0.73** | 0.65 | 0.35 | 0.00 | — |

  

DeepFootprinting matches AlphaGenome and HepG2-restricted Enformer on population variants. It clearly outperforms Sei, Borzoi and four DNA language models fine-tuned on the same enhancer task (Nucleotide Transformer, GENA-LM, HyenaDNA, DNABERT-2). AlphaGenome and Enformer remain stronger on dense single-element scans.

  

## 4. Corrected claims (accuracy and reviewer-proofing)

- **Performance:** "mean AUPRC 0.91" → median AUPRC 0.94 on held-out chromosomes.

- **Motif-family recovery:** 79% → 61%, verified with TOMTOM (150 of 247 TFs).

- **MEME:** "significantly outperforming MEME Suite" → on par with MEME-ChIP for top-ranked motifs, while reporting about 6-fold fewer patterns.

- **HNF4A–FOXA2 spacing:** the fixed-spacing claim, based on 298 JASPAR matches, was an artifact of motif scanning and is replaced by the core-convergence result. The original Fig. 2A/2D and 4A/4D were rebuilt.

- **Comparator fairness:** archived Enformer, Borzoi and Sei scores did not use HepG2 tracks. The Methods are corrected and Enformer was rescored on HepG2 DNase tracks.

- **Other corrections:**

- The training software and compute were corrected (TF 1.4/Keras 2.0.8 on V100, about 330 GPU-hours; not TF 2.15/H200).

- The Fig. 5A coordinates and cCRE label were fixed.

- An underpowered GTEx eQTL claim is now stated as a limitation.

  

## 5. Presentation and reproducibility

- Abstract, Introduction, Results and Discussion are rewritten around biological questions, with limitations stated explicitly.

- Figures 1–5 are revised (new or rebuilt panels 1D, 1G, 2A, 2D, 2E, 2G, 3E, 3F, 4A, 4D, 5D and 5F).

- There are 11 new or regenerated supplementary tables.

- The 67 numbered references were checked against Crossref and arXiv.

- Every new number is produced by a script in `paper/revision_analyses/`.