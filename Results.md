
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

**Key Insight:** The analysis reveals a highly interconnected network of TFs within enhancers, with certain TFs (ARID5B, PAXIP1, ARID3A, SOX6, HNF4A, FOXA2, MAX) acting as central hubs that frequently co-occur with many other TFs


## Results Summary: TF Pair Overlap and Distance Analysis

Based on the visualization, here are the key findings:

**Relationship Classification:**

- **All_Overlap**: 7,445,376 TF pairs (18.2%) - All their peaks overlap
- **Mixed**: 1,674,055 TF pairs (3.7%) - Some peaks overlap, some don't
- **No_Overlap**: 31,833,586 TF pairs (80.5%) - No peaks overlap at all

**Overlap Statistics (for overlapping pairs):**

- **Mean overlap percentage**: ~19.0%
- **Mean overlap size**: 8.5bp
- **Median overlap size**: 9.0bp
- Most overlaps are 8-16bp (the size of the centered peaks)

**Distance Statistics (for non-overlapping peaks):**

- **Mean distance**: 78.0bp
- **Median distance**: 67.0bp
- Most non-overlapping peaks are within 50-100bp of each other
- Distribution shows many pairs very close together but not overlapping

**Top 30 TF Pairs by Co-occurrence:**  
Ranked by number of enhancers where they appear together, color-coded by relationship type:

- Red = All peaks overlap
- Orange = Mixed (some overlap, some don't)
- Blue = No overlap

Top pairs include ARID5B-PAXIP1, ARID3A-ARID5B, ARID3A-PAXIP1, etc., mostly showing "No_Overlap" relationships.

**Co-occurrence vs Overlap:**

- Scatter plot shows most TF pairs have low overlap percentages even when frequently co-occurring
- High co-occurrence doesn't necessarily mean high overlap

**Overlap vs Distance (Mixed pairs):**

- For pairs with mixed relationships, shows the relationship between overlap size and distance
- Colored by number of enhancers where the pair occurs

**Top 20 Most Overlapping Pairs:**

- Lists pairs with highest percentage of overlapping peaks
- Shows which TF combinations tend to bind at the same exact locations

**Top 20 Most Separated Pairs:**

- Shows pairs with largest average distances between non-overlapping peaks
- Indicates TFs that co-occur but maintain spatial separation

**Average Overlap Percentage Matrix (Top 15 TFs):**

- Heatmap showing pairwise overlap percentages for the most common TFs
- Most show 20-40% overlap, indicating partial co-localization patterns

**Key Insight:** The vast majority (80%) of TF pairs within the same enhancer do NOT overlap, suggesting they bind at distinct but nearby locations within the 400bp enhancer regions. This supports a model of combinatorial TF binding with spatial organization rather than complete co-localization

## Results Summary: Non-Overlapping TF Pairs Analysis

**Overall Statistics:**

- **Total non-overlapping TF pair instances**: 36,643,656
- **Unique TF pairs**: 88,597
- **Enhancers with non-overlapping pairs**: 19,455 (93% of all enhancers)

**Distance Statistics:**

- **Mean distance**: 60.5bp between non-overlapping TF peaks
- **Median distance**: 43.0bp
- **Range**: 0-398bp (spans the full 400bp enhancer length)
- **Std deviation**: 58.7bp

**Top 20 Most Frequent Non-Overlapping TF Pairs:**

1. **ARID3A-PAXIP1** - 7,094 enhancers, avg distance 35.0bp, median 24bp
2. **ARID3A-ARID5B** - 6,973 enhancers, avg distance 34.0bp, median 22bp
3. **ARID3A-SOX6** - 6,931 enhancers, avg distance 37.4bp, median 26bp
4. **PAXIP1-SOX6** - 6,927 enhancers, avg distance 35.0bp, median 23bp
5. **MAX-PAXIP1** - 6,748 enhancers, avg distance 43.3bp, median 30bp

Most top pairs maintain 20-35bp spacing between their binding sites.

**TF Connectivity (Non-overlapping Partners):**

- Many TFs have **421 unique non-overlapping partners** (the maximum)
- Top connected TFs: ZNF512B, THAP7, DLX6, GATA2, TOPORS, MAX, etc.
- MAX appears in 11,089 enhancers with non-overlapping relationships

**Key Visualizations Show:**

1. **Top 20 pairs** - Most frequent non-overlapping combinations
2. **Distance distribution** - Right-skewed with peak at 20-50bp
3. **TF partner counts** - Most TFs have extensive non-overlapping networks
4. **Pair frequency vs distance** - No strong correlation; pairs at all distances are common
5. **Distance percentiles** - 50% of pairs within ~50bp, 90% within ~180bp
6. **Pairs per enhancer** - Mean ~1,883 non-overlapping pairs per enhancer
7. **Frequency heatmap** - Shows which TFs most frequently appear together without overlapping
8. **Distance by frequency** - Average distance relatively stable (~80bp) across frequency bins
9. **Cumulative distribution** - 50% of pairs within 43bp separation

**Key Insight:** Non-overlapping TF pairs are extremely common (36.6M instances vs 7.4M overlapping), with most maintaining relatively close spacing (20-60bp). This indicates that TFs frequently bind in spatial proximity within enhancers but at distinct sites, suggesting a model of combinatorial regulation through neighboring rather than co-localized binding. The top TF families (ARID, PAXIP1, SOX6, MAX, HNF4A, FOXA2, SALL1) show particularly strong patterns of non-overlapping co-occurrence.