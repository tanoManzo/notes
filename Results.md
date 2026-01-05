
## TF Binding in Enhancer Regions

**Dataset:**

- **20,833 enhancers** analyzed 
- **20,246 enhancers** (97.2%) have at least one TF binding
- **587 enhancers** (2.8%) have no TF binding

**TF Binding Statistics:**

- **Mean: 44.33 TFs per enhancer**
- **Median: 26 TFs per enhancer**

**Top 20 TFs by Enhancer Coverage:**

1. **ARID5B** - 13,027 enhancers (62.5%), 14,110 peaks (24.0% of total)
2. **PAXIP1** - 12,937 enhancers (62.1%), 15,654 peaks (28.9% of total)
3. **ARID3A** - 12,197 enhancers (58.5%), 13,700 peaks (25.3% of total)
4. **SOX6** - 11,983 enhancers (57.5%), 14,110 peaks (25.1% of total)
5. **HNF4A** - 11,919 enhancers (57.2%), 12,325 peaks (23.2% of total)
6. **FOXA2** - 11,241 enhancers (54.0%), 11,745 peaks (25.7% of total)
7. **MAX** - 11,103 enhancers (53.3%), 12,859 peaks (18.2% of total)
8. **SALL1** - 10,264 enhancers (49.3%), 11,110 peaks (18.5% of total)
9. **TFAP4** - 9,569 enhancers (45.9%), 10,097 peaks (19.8% of total)
10. **FOXP4** - 9,476 enhancers (45.5%), 10,166 peaks (28.5% of total)



**Key Insights from Visualizations:**

- Most enhancers have 20-50 TFs binding
- TF peak enrichment in enhancers averages ~13%
- Top TFs show ~1.0-1.2 average peaks per enhancer (binding intensity)
- Strong co-occurrence of top TFs in highly occupied enhancers

## Results Summary: TF Co-occurrence Analysis

Based on the cell execution and visualizations, here are the key findings:
**Overall Statistics:**

- Analyzed all TF pairs that co-occur within the same enhancers
- Shows mean and median co-occurrence counts per TF pair
- Identifies unique TFs involved in co-occurrence relationships

**Top Co-occurring TF Pairs:**  
The cell outputs the **top 50 TF pairs** ranked by co-occurrence frequency, showing:

- TF1 and TF2 names
- Number of enhancers where they co-occur
- Percentage of total enhancers

From the visualization, the most frequent pairs include:

- **ARID5B-PAXIP1** (~10,629 co-occurrences)
- **ARID3A-ARID5B** (~10,510)
- **ARID3A-PAXIP1** (~10,018)
- And many other highly connected pairs

**TF Connectivity Analysis:**  
The cell identifies the **top 30 most connected TFs** by:

- **Unique partners**: How many different TFs each one co-occurs with
- **Total co-occurrences**: Sum of all co-occurrence events
- **Average per partner**: Strength of co-occurrence relationships

Top connected TFs include PAXIP1, ARID5B, ARID3A, SOX6, MAX, HNF4A, FOXA2, etc.

**Visualizations Show:**

1. **Top 40 pairs** with exact co-occurrence counts
2. **Distribution** of co-occurrence frequencies (log scale)
3. **Co-occurrence matrix heatmap** for top 20 most connected TFs showing all pairwise relationships
4. **Total co-occurrences** per TF (connectivity strength)
5. **Number of unique partners** per TF (connectivity breadth)
6. **Average co-occurrence per partner** (relationship strength)

**Key Insight:** The analysis reveals a highly interconnected network of TFs within enhancers, with certain TFs (ARID5B, PAXIP1, ARID3A, SOX6, HNF4A, FOXA2, MAX) acting as central hubs that frequently co-occur with many other TFs.