The **MEME-ChIP** web service is a tool designed for **motif discovery and enrichment analysis** in **ChIP-seq** data. It processes **FASTA-formatted sequences** centered on **ChIP-seq tag peaks**, identifies **novel motifs**, and determines their **enrichment** using various algorithms:

- **Preprocessing**: Uploaded sequences are centered and trimmed to **100 bp** for motif discovery, but the full-length sequences are used for visualization.
    
- **Motif Discovery**:
    
    - **DREME**: Discovers short, statistically significant motifs in all trimmed sequences.
        
    - **MEME**: Identifies longer, more complex motifs, but is limited to **600 randomly selected sequences** due to computational constraints.
        
- **Motif Enrichment Analysis**:
    
    - **AME (Analysis of Motif Enrichment)**: Measures the statistical enrichment of known motifs from the **JASPAR CORE database** in the input sequences.
        
    - **AMA (Average Motif Affinity)**: Computes the average binding affinity of MEME-discovered motifs for each sequence.
        
- **Motif Visualization**:
    
    - **MAST**: Maps discovered motifs to the **full-length** input sequences.
        
    - **Comparison to JASPAR CORE**: Identifies **transcription factors (TFs)** that may bind to the discovered motifs.
![[Pasted image 20250331102249.png]]