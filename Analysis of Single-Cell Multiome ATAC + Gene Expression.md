## The problem
![[Pasted image 20240612103621.png]]


## How usually you do
![[Pasted image 20240612103907.png]]

## Check for Gene-Expression (RNA-seq) and Chromatin-Accessibility (ATAC-seq)

each column is a different sample, each row is a different gene
![[Pasted image 20240612104441.png]]

### Limitation: Bulk rna-seq analysis (all the cells and all treatment on average)

![[Pasted image 20240612104836.png]]

same for ATAC-seq bulk (assay that allows us to look at regions of open chromatin e.g., where TF can bind or rna polymerase can come in to drive gene expression)
![[Pasted image 20240612105354.png]]

## Why single cell?

![[Pasted image 20240612105441.png]]

![[Pasted image 20240612113117.png]]

### limitation, no direct profiling gene expression and chromatin accessibility from exact the same cell. 

Each dot is a cell and the color is the pattern of gene expression. Circle is the leukemia cells. 
![[Pasted image 20240612113354.png]]
Look at the peaks in the open chromatin and check if there is an enrichment of the motifs above (CEBPB and GATA1)

![[Pasted image 20240612113656.png]]

### Limitation: because we are not using the both data at the same time/cell, we cannot say that a given chromatin access profile matched a given gene expression profile. 

## Multiome solve this issue. 
Using multiple assays to probe different features in a biological space. 
![[Pasted image 20240612114302.png]] 
![[Pasted image 20240612115144.png]]

### Wet Lab protocol
![[Pasted image 20240612115538.png]]

![[Pasted image 20240612115917.png]]
### Quality control 
![[Pasted image 20240612120457.png]]
(1) get only good reads, (2) Enrichment at Transcript Starting Site, promoter needs to be accessible for the related gene to be expressed. High quality of cells have enriched chromatic accessibility reads at TSS. (3) remove low quality cells.

## Clustering

![[Pasted image 20240612141519.png]]

Group of cells with similar gene expression and chromatin accessibility 
![[Pasted image 20240612141715.png]]

![[Pasted image 20240612141837.png]]

get only the genes that have high variability. 

![[Pasted image 20240612142112.png]]


![[Pasted image 20240612142230.png]]