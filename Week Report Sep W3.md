
**Comparative Analysis: Deep Footprinting vs. MEME-suite**

• Conducted a comparative enrichment analysis between Deep Footprinting and MEME-suite (including tools such as FIMO, CentriMO, and STREME).

• Found that Deep Footprinting enrichment analysis yields more accurate results than MEME-suite. While MEME-suite can capture the transcription factor (TF) motif of interest, it underperforms in correctly identifying enriched motifs.

• Observed a noticeable decrease in the number of correctly identified TF motifs in MEME-suite when narrowing the selection from top-10 to top-1 motifs.

• Included quantitative analysis on the number of output motifs per ChIP-seq peak for both methods, noting an order of magnitude difference (Deep Footprinting outputs significantly more accurate).

• Provided a heatmap and an example output for the GATA2 motif identified by MEME-suite for visual comparison.

![[Pasted image 20250919134554.png]]

**Background Selection in Enrichment Analysis**

• Initiated a comparative analysis on the impact of different background selections for enrichment analyses: DHS all-genome, DHS cell-line, and flanking regions.

• Early observations suggest substantial differences depending on background choice, especially:

• For cell-line specific TFs (e.g., HNF4A in HepG2), results vary significantly.

• For more ubiquitous TFs (e.g., CTCF in HepG2), the output is less sensitive to background selection.

• Analysis on this aspect is ongoing and will continue next week.




**Next Steps**

- Finalize results for the background selection analysis.
- Start analysis on Enhancers. 