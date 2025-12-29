```
import pickle

# save the keys in a list

list_eid = list(dict_eid.keys())

  

with open('eid_list.pkl', 'wb') as f:

pickle.dump(list_eid, f)
```
```
import matplotlib.pyplot as plt

import numpy as np

  

# Extract data

eids = list(dict_eid.keys())

clean_eids = []

  

for eid in eids:

clean_eid = (

eid.replace("human", "")

.replace("cell_line", "")

.replace("_", "")

.strip("")

)

clean_eids.append(clean_eid)

  

n_tfs = [len(data['list_tf']) for data in dict_eid.values()]

  

# Compute mean

mean_tfs = np.mean(n_tfs)

  

# Plot

plt.figure(figsize=(14, 5))

plt.bar(clean_eids, n_tfs, color="skyblue", edgecolor="black")

  

# Add mean line

plt.axhline(mean_tfs, color="red", linestyle="--", linewidth=1.5, label=f"Mean = {mean_tfs:.2f}")

  

plt.xticks(rotation=45)

plt.xlabel("EID")

plt.ylabel("Number of TFs")

  

# Clean style

ax = plt.gca()

  

ax.spines["top"].set_visible(False)

ax.spines["right"].set_visible(False)

  

plt.legend()

plt.tight_layout()

plt.show()



## Read all .merged.bed files from HepG2 directory

import os

import pandas as pd

from pathlib import Path

  

# Define the directory path

bed_dir = Path("/data/Dcode/gaetano/FootPrinting/data/ENCODE_TF_CHIPSEP/TFs_chipseq_by_biotype/cell line/HepG2")

  

# Find all .merged.bed files

bed_files = list(bed_dir.glob("*.merged.bed"))

  

print(f"Found {len(bed_files)} .merged.bed files")

print("\nFirst 10 files:")

for i, file in enumerate(bed_files[:10]):

print(f"{i+1}. {file.name}")

  

# Read all bed files into a dictionary

# Key: filename, Value: DataFrame

bed_data = {}

  

for bed_file in bed_files:

# BED files typically have columns: chr, start, end, (name, score, strand, ...)

# Adjust column names based on your BED file format

df = pd.read_csv(

bed_file,

sep='\t',

header=None,

names=['chr', 'start', 'end', 'name', 'score', 'strand'] # Standard BED6 format

)

bed_data[bed_file.name] = df

print(f"\nLoaded {len(bed_data)} BED files into dictionary")

  

# Example: Show first file's data

if bed_data:

first_file = list(bed_data.keys())[0]

print(f"\nPreview of {first_file}:")

print(bed_data[first_file].head())

print(f"Shape: {bed_data[first_file].shape}")
```

```
import pandas as pd

import pyranges as pr

from pathlib import Path

  

# Directory with BED files

bed_dir = Path("/data/Dcode/gaetano/FootPrinting/data/ENCODE_TF_CHIPSEP/TFs_chipseq_by_biotype/cell line/HepG2")

  

# Load HNF4A merged bed file - only read first 3 columns (chr, start, end)/

hnf4a_bed = bed_dir / "HNF4A-human.merged.bed"

hnf4a_df = pd.read_csv(hnf4a_bed, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

  

print(f"HNF4A binding sites: {len(hnf4a_df)}")

print(f"Preview:")

print(hnf4a_df.head())

print(f"\nUnique chromosomes in HNF4A: {sorted(hnf4a_df['chr'].unique())[:10]}")

  

# Check a few other TFs to see chromosome naming

print("\nChecking chromosome naming in other TFs:")

for tf_file in list(bed_dir.glob("*.merged.bed"))[:3]:

tf_df = pd.read_csv(tf_file, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

print(f"{tf_file.stem}: {sorted(tf_df['chr'].unique())[:5]}")

  

# Create PyRanges object for HNF4A

hnf4a_pr = pr.PyRanges(hnf4a_df.rename(columns={'chr': 'Chromosome', 'start': 'Start', 'end': 'End'}))

  

print(f"\nHNF4A PyRanges object:")

print(hnf4a_pr)


# Find intersections with all other TFs

all_bed_files = list(bed_dir.glob("*.merged.bed"))

  

# Store intersection results

intersection_results = []

  

# Debug: try one TF first to see what's happening

print("Testing with FOXA1 first...")

test_file = bed_dir / "FOXA1-human.merged.bed"

test_df = pd.read_csv(test_file, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

print(f"FOXA1 sites: {len(test_df)}")

print(f"FOXA1 chromosomes: {sorted(test_df['chr'].unique())[:5]}")

  

test_pr = pr.PyRanges(test_df.rename(columns={'chr': 'Chromosome', 'start': 'Start', 'end': 'End'}))

print(f"\nFOXA1 PyRanges:")

print(test_pr)

  

# Try intersection

test_intersect = hnf4a_pr.join(test_pr)

print(f"\nHNF4A ∩ FOXA1 intersections: {len(test_intersect)}")

if len(test_intersect) > 0:

print("Sample intersections:")

print(test_intersect.df.head())

  

print("\n" + "="*80)

print("Now checking all TFs...")

print("="*80)

  

for bed_file in all_bed_files:

tf_name = bed_file.stem.replace("-human.merged", "").replace("-human", "")

# Skip HNF4A itself

if tf_name == "HNF4A":

continue

# Load other TF - only first 3 columns

other_df = pd.read_csv(bed_file, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

other_pr = pr.PyRanges(other_df.rename(columns={'chr': 'Chromosome', 'start': 'Start', 'end': 'End'}))

# Find intersections

intersect_pr = hnf4a_pr.join(other_pr)

n_intersections = len(intersect_pr) if len(intersect_pr) > 0 else 0

# Store results

intersection_results.append({

'TF': tf_name,

'HNF4A_sites': len(hnf4a_df),

'Other_TF_sites': len(other_df),

'Overlapping_regions': n_intersections,

'Overlap_percentage': (n_intersections / len(hnf4a_df) * 100) if len(hnf4a_df) > 0 else 0

})

  

# Convert to DataFrame and sort by number of overlaps

results_df = pd.DataFrame(intersection_results)

results_df = results_df.sort_values('Overlapping_regions', ascending=False)

  

print(f"\nTop 20 TFs with most overlaps with HNF4A:")

print("=" * 80)

print(results_df.head(20).to_string(index=False))

  

print(f"\n\nSummary:")

print(f"Total TFs checked: {len(results_df)}")

print(f"TFs with overlaps: {(results_df['Overlapping_regions'] > 0).sum()}")

if (results_df['Overlapping_regions'] > 0).sum() > 0:

print(f"Mean overlap percentage (excluding zeros): {results_df[results_df['Overlapping_regions'] > 0]['Overlap_percentage'].mean():.2f}%")

else:

print("WARNING: No overlaps found! Check chromosome naming consistency.")
```


```
# Visualize the top co-binding TFs

import matplotlib.pyplot as plt

import seaborn as sns

  

sns.set_style("whitegrid")

  

# Plot top 30 TFs by overlap

top_n = 50

  

# Calculate percentage of OTHER TF sites that overlap with HNF4A

results_df['Other_TF_overlap_percentage'] = (results_df['Overlapping_regions'] / results_df['Other_TF_sites'] * 100)

  

# Sort by the percentage of the OTHER TF's peaks that overlap with HNF4A

top_tfs = results_df.sort_values('Other_TF_overlap_percentage', ascending=False).head(top_n)

  

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(18, 8))

  

# Plot 1: Number of overlapping regions

ax1.barh(range(len(top_tfs)), top_tfs['Overlapping_regions'], color='steelblue', edgecolor='black')

ax1.set_yticks(range(len(top_tfs)))

ax1.set_yticklabels(top_tfs['TF'], fontsize=9)

ax1.set_xlabel('Number of Overlapping Regions', fontsize=12, fontweight='bold')

ax1.set_title(f'Top {top_n} TFs Co-binding with HNF4A\n(Sorted by % of TF peaks overlapping HNF4A)', fontsize=14, fontweight='bold')

ax1.invert_yaxis()

ax1.spines['top'].set_visible(False)

ax1.spines['right'].set_visible(False)

  

# Plot 2: Overlap percentage of OTHER TF

ax2.barh(range(len(top_tfs)), top_tfs['Other_TF_overlap_percentage'], color='coral', edgecolor='black')

ax2.set_yticks(range(len(top_tfs)))

ax2.set_yticklabels(top_tfs['TF'], fontsize=9)

ax2.set_xlabel('% of TF Sites Overlapping with HNF4A', fontsize=12, fontweight='bold')

ax2.set_title(f'TF Overlap Percentage\n(What % of this TF overlaps HNF4A)', fontsize=14, fontweight='bold')

ax2.invert_yaxis()

ax2.spines['top'].set_visible(False)

ax2.spines['right'].set_visible(False)

  

plt.tight_layout()

plt.show()
```

```
# Visualize top co-binding TFs - using only center 30bp of each peak and classify overlaps

import matplotlib.pyplot as plt

import seaborn as sns

import numpy as np

  

sns.set_style("whitegrid")

  

# Plot top TFs by overlap

top_n = 50

center_window = 13 # Use only 30bp in the center of each peak

  

# Create centered peaks for HNF4A (±15bp from center)

hnf4a_df_centered = hnf4a_df.copy()

hnf4a_df_centered['center'] = (hnf4a_df_centered['start'] + hnf4a_df_centered['end']) // 2

hnf4a_df_centered['start_centered'] = hnf4a_df_centered['center'] - center_window // 2

hnf4a_df_centered['end_centered'] = hnf4a_df_centered['center'] + center_window // 2

  

# Create PyRanges for centered HNF4A peaks

hnf4a_centered_pr = pr.PyRanges(hnf4a_df_centered.rename(columns={

'chr': 'Chromosome',

'start_centered': 'Start',

'end_centered': 'End'

}))

  

print(f"Analyzing overlaps using center {center_window}bp of each peak...")

print(f"Original HNF4A peaks: {len(hnf4a_df)}")

print(f"HNF4A centered regions: {len(hnf4a_centered_pr)}\n")

  

# Find intersections with all other TFs (using centered regions for both)

intersection_results_centered = []

overlap_quality_rows = []

  

for bed_file in all_bed_files:

tf_name = bed_file.stem.replace("-human.merged", "").replace("-human", "")

# Skip HNF4A itself

if tf_name == "HNF4A":

continue

# Load other TF

other_df = pd.read_csv(bed_file, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

# Center the other TF peaks too

other_df_centered = other_df.copy()

other_df_centered['center'] = (other_df_centered['start'] + other_df_centered['end']) // 2

other_df_centered['start_centered'] = other_df_centered['center'] - center_window // 2

other_df_centered['end_centered'] = other_df_centered['center'] + center_window // 2

other_centered_pr = pr.PyRanges(other_df_centered.rename(columns={

'chr': 'Chromosome',

'start_centered': 'Start',

'end_centered': 'End'

}))

# Find intersections between centered peaks

intersect_pr = hnf4a_centered_pr.join(other_centered_pr, suffix="_other")

n_intersections = len(intersect_pr) if len(intersect_pr) > 0 else 0

# Quantify overlap quality

complete_count = 0

partial_count = 0

overlap_other_pairs = set()

if len(intersect_pr) > 0:

join_df = intersect_pr.df

overlap_len = np.minimum(join_df['End'], join_df['End_other']) - np.maximum(join_df['Start'], join_df['Start_other'])

complete_mask = overlap_len >= center_window # 30bp fully overlaps

partial_mask = (overlap_len > 0) & (overlap_len < center_window)

complete_count = int(complete_mask.sum())

partial_count = int(partial_mask.sum())

overlap_other_pairs = set(zip(join_df['Start_other'], join_df['End_other']))

total_other = len(other_df_centered)

no_overlap_count = total_other - len(overlap_other_pairs)

# Distances for non-overlapping other peaks (0 distance means overlapping)

nearest_df = other_centered_pr.nearest(hnf4a_centered_pr).df

if 'Distance' in nearest_df.columns:

distances = nearest_df['Distance']

else:

# Fallback manual distance

distances = np.where(

nearest_df['Start'] > nearest_df['End_b'],

nearest_df['Start'] - nearest_df['End_b'],

nearest_df['Start_b'] - nearest_df['End']

)

nonzero_dist = distances[distances > 0]

mean_distance = float(nonzero_dist.mean()) if len(nonzero_dist) > 0 else 0.0

min_distance = float(nonzero_dist.min()) if len(nonzero_dist) > 0 else 0.0

overlap_quality_rows.append({

'TF': tf_name,

'Total_TF_sites': total_other,

'Complete_overlap_count': complete_count,

'Partial_overlap_count': partial_count,

'No_overlap_count': no_overlap_count,

'Pct_complete_overlap': (complete_count / total_other * 100) if total_other > 0 else 0,

'Pct_partial_overlap': (partial_count / total_other * 100) if total_other > 0 else 0,

'Mean_distance_if_no_overlap_bp': mean_distance,

'Min_distance_if_no_overlap_bp': min_distance

})

# Store summary for previous chart

intersection_results_centered.append({

'TF': tf_name,

'HNF4A_centered_sites': len(hnf4a_df_centered),

'Other_TF_centered_sites': len(other_df_centered),

'Overlapping_centered_regions': n_intersections,

'Other_TF_overlap_percentage': (n_intersections / len(other_df_centered) * 100) if len(other_df_centered) > 0 else 0

})

  

# Convert to DataFrames

results_centered_df = pd.DataFrame(intersection_results_centered).sort_values('Other_TF_overlap_percentage', ascending=False)

overlap_quality_df = pd.DataFrame(overlap_quality_rows)

  

print(f"Top 20 TFs by overlap percentage (using center {center_window}bp):")

print("=" * 80)

print(results_centered_df.head(20).to_string(index=False))

  

print(f"\nTop 20 TFs by complete overlap percentage (center {center_window}bp):")

print("=" * 80)

print(

overlap_quality_df

.sort_values(['Pct_complete_overlap', 'Pct_partial_overlap'], ascending=False)

.head(20)

.to_string(index=False)

)

  

# Visualize

sns.set_style("whitegrid")

top_tfs_centered = results_centered_df.head(top_n)

  

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(18, 8))

  

# Plot 1: Number of overlapping regions

ax1.barh(range(len(top_tfs_centered)), top_tfs_centered['Overlapping_centered_regions'], color='steelblue', edgecolor='black')

ax1.set_yticks(range(len(top_tfs_centered)))

ax1.set_yticklabels(top_tfs_centered['TF'], fontsize=9)

ax1.set_xlabel('Number of Overlapping Regions', fontsize=12, fontweight='bold')

ax1.set_title(f'Top {top_n} TFs Co-binding with HNF4A\n(Center {center_window}bp only, sorted by % of TF overlapping)', fontsize=14, fontweight='bold')

ax1.invert_yaxis()

ax1.spines['top'].set_visible(False)

ax1.spines['right'].set_visible(False)

  

# Plot 2: Overlap percentage of OTHER TF

ax2.barh(range(len(top_tfs_centered)), top_tfs_centered['Other_TF_overlap_percentage'], color='coral', edgecolor='black')

ax2.set_yticks(range(len(top_tfs_centered)))

ax2.set_yticklabels(top_tfs_centered['TF'], fontsize=9)

ax2.set_xlabel(f'% of TF Sites Overlapping HNF4A (center {center_window}bp)', fontsize=12, fontweight='bold')

ax2.set_title(f'TF Overlap Percentage\n(What % of this TF overlaps HNF4A center)', fontsize=14, fontweight='bold')

ax2.invert_yaxis()

ax2.spines['top'].set_visible(False)

ax2.spines['right'].set_visible(False)

  

plt.tight_layout()

plt.show()

  

# Optional: show distance summary for TFs with no/partial overlaps

print("\nDistance summary for non-overlapping peaks (mean/min, bp):")

print(

overlap_quality_df[['TF', 'Mean_distance_if_no_overlap_bp', 'Min_distance_if_no_overlap_bp']]\

.sort_values('Mean_distance_if_no_overlap_bp')

.head(20)

.to_string(index=False)

)
```

```
# Comprehensive overlap quality analysis - Flexible for any Reference TF

import pandas as pd

import numpy as np

import pyranges as pr

  

# ============================================================================

# CONFIGURATION: Set your reference TF here

# ============================================================================

REFERENCE_TF = "HNF4A" # Change this to analyze a different TF (e.g., "FOXA1", "CEBPA", etc.)

# ============================================================================

  
  

center_window = 13

# Check if required variables exist

try:

all_bed_files

bed_dir

center_window # Get the center_window size from previous cell

except NameError:

print("="*80)

print("ERROR: Required variables not found in kernel")

print("="*80)

print("\nPlease run the cells that load BED files and set center_window first.")

print("\nRequired variables:")

print(" - all_bed_files (list of BED files)")

print(" - bed_dir (directory path)")

print(" - center_window (window size for analysis)")

else:

print("="*80)

print(f"DETAILED OVERLAP ANALYSIS - {REFERENCE_TF} vs Other TFs")

print(f"Using {center_window}bp centered windows")

print("="*80)

# Load reference TF data

ref_bed = bed_dir / f"{REFERENCE_TF}-human.merged.bed"

if not ref_bed.exists():

print(f"\nERROR: {REFERENCE_TF} BED file not found: {ref_bed}")

print(f"\nAvailable TFs:")

for f in sorted(all_bed_files)[:20]:

print(f" - {f.stem.replace('-human.merged', '').replace('-human', '')}")

else:

# Load and center reference TF peaks

ref_df = pd.read_csv(ref_bed, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

ref_df_centered = ref_df.copy()

ref_df_centered['center'] = (ref_df_centered['start'] + ref_df_centered['end']) // 2

ref_df_centered['start_centered'] = ref_df_centered['center'] - center_window // 2

ref_df_centered['end_centered'] = ref_df_centered['center'] + center_window // 2

ref_centered_pr = pr.PyRanges(ref_df_centered.rename(columns={

'chr': 'Chromosome',

'start_centered': 'Start',

'end_centered': 'End'

}))

print(f"\n{REFERENCE_TF} binding sites: {len(ref_df):,}")

print(f"Centered regions ({center_window}bp): {len(ref_centered_pr):,}")

print(f"\nAnalyzing overlaps with all other TFs...")

# Calculate overlaps for all TFs

overlap_results = []

detailed_stats = []

for bed_file in all_bed_files:

tf_name = bed_file.stem.replace("-human.merged", "").replace("-human", "")

# Skip reference TF itself

if tf_name == REFERENCE_TF:

continue

# Load other TF

other_df = pd.read_csv(bed_file, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

# Center the other TF peaks

other_df_centered = other_df.copy()

other_df_centered['center'] = (other_df_centered['start'] + other_df_centered['end']) // 2

other_df_centered['start_centered'] = other_df_centered['center'] - center_window // 2

other_df_centered['end_centered'] = other_df_centered['center'] + center_window // 2

other_centered_pr = pr.PyRanges(other_df_centered.rename(columns={

'chr': 'Chromosome',

'start_centered': 'Start',

'end_centered': 'End'

}))

# Find intersections

intersect_pr = ref_centered_pr.join(other_centered_pr, suffix="_other")

n_intersections = len(intersect_pr) if len(intersect_pr) > 0 else 0

# Calculate overlap lengths and classify

complete_count = 0

partial_count = 0

mean_all_overlaps = 0.0

median_all_overlaps = 0.0

mean_complete = 0.0

mean_partial = 0.0

overlap_other_pairs = set()

if len(intersect_pr) > 0:

join_df = intersect_pr.df

overlap_lengths = np.minimum(join_df['End'], join_df['End_other']) - np.maximum(join_df['Start'], join_df['Start_other'])

complete_mask = overlap_lengths >= center_window

partial_mask = (overlap_lengths > 0) & (overlap_lengths < center_window)

complete_count = int(complete_mask.sum())

partial_count = int(partial_mask.sum())

overlap_other_pairs = set(zip(join_df['Start_other'], join_df['End_other']))

# Calculate mean overlap lengths

complete_overlaps = overlap_lengths[complete_mask]

partial_overlaps = overlap_lengths[partial_mask]

mean_complete = float(complete_overlaps.mean()) if len(complete_overlaps) > 0 else 0.0

mean_partial = float(partial_overlaps.mean()) if len(partial_overlaps) > 0 else 0.0

mean_all_overlaps = float(overlap_lengths.mean())

median_all_overlaps = float(overlap_lengths.median())

total_other = len(other_df_centered)

no_overlap_count = total_other - len(overlap_other_pairs)

# Calculate distances for non-overlapping peaks

nearest_df = other_centered_pr.nearest(ref_centered_pr).df

if 'Distance' in nearest_df.columns:

distances = nearest_df['Distance']

else:

distances = np.where(

nearest_df['Start'] > nearest_df['End_b'],

nearest_df['Start'] - nearest_df['End_b'],

nearest_df['Start_b'] - nearest_df['End']

)

nonzero_dist = distances[distances > 0]

mean_distance = float(nonzero_dist.mean()) if len(nonzero_dist) > 0 else 0.0

min_distance = float(nonzero_dist.min()) if len(nonzero_dist) > 0 else 0.0

max_distance = float(nonzero_dist.max()) if len(nonzero_dist) > 0 else 0.0

# Store results

overlap_results.append({

'TF': tf_name,

'Total_sites': total_other,

'Overlapping_sites': n_intersections,

'Overlap_percentage': (n_intersections / total_other * 100) if total_other > 0 else 0

})

detailed_stats.append({

'TF': tf_name,

'Total_sites': total_other,

'Complete_overlaps': complete_count,

'Partial_overlaps': partial_count,

'No_overlaps': no_overlap_count,

'Pct_complete': (complete_count / total_other * 100) if total_other > 0 else 0,

'Pct_partial': (partial_count / total_other * 100) if total_other > 0 else 0,

'Mean_overlap_bp_all': mean_all_overlaps,

'Median_overlap_bp_all': median_all_overlaps,

'Mean_overlap_bp_complete': mean_complete,

'Mean_overlap_bp_partial': mean_partial,

'Mean_distance_no_overlap': mean_distance,

'Min_distance_no_overlap': min_distance,

'Max_distance_no_overlap': max_distance

})

# Convert to DataFrames

overlap_df = pd.DataFrame(overlap_results).sort_values('Overlap_percentage', ascending=False)

detailed_df = pd.DataFrame(detailed_stats)

print(f"\nAnalyzed {len(overlap_df)} TFs")

# ====================================================================

# DISPLAY RESULTS

# ====================================================================

print("\n" + "="*80)

print(f"1. TOP 20 TFs OVERLAPPING WITH {REFERENCE_TF}")

print("="*80)

print("\nBy Overlap Percentage:")

print("-"*80)

display_cols = ['TF', 'Total_sites', 'Complete_overlaps', 'Partial_overlaps',

'Mean_overlap_bp_all', 'Median_overlap_bp_all']

top_20_detailed = detailed_df.sort_values('Pct_complete', ascending=False).head(20)

print(top_20_detailed[display_cols].to_string(index=False))

print("\n\nDetailed Overlap Breakdown:")

print("-"*80)

overlap_detail_cols = ['TF', 'Pct_complete', 'Pct_partial', 'Mean_overlap_bp_complete', 'Mean_overlap_bp_partial']

print(top_20_detailed[overlap_detail_cols].to_string(index=False))

print(f"\nNote: Complete overlaps are ≥{center_window}bp, Partial overlaps are 1-{center_window-1}bp")

print("\n" + "="*80)

print("2. DISTANCE ANALYSIS (For non-overlapping peaks)")

print("="*80)

distance_cols = ['TF', 'No_overlaps', 'Mean_distance_no_overlap',

'Min_distance_no_overlap', 'Max_distance_no_overlap']

top_20_distance = detailed_df[detailed_df['No_overlaps'] > 0].nsmallest(20, 'Mean_distance_no_overlap')

print(top_20_distance[distance_cols].to_string(index=False))

print("\n" + "="*80)

print("3. SUMMARY INTERPRETATION")

print("="*80)

print("\nOVERLAP CATEGORIES:")

print(f" • COMPLETE OVERLAP ({center_window}bp): Both {center_window}bp centered regions fully overlap")

print(f" • PARTIAL OVERLAP (1-{center_window-1}bp): Regions partially overlap with some bases shared")

print(" • NO OVERLAP (0bp): Regions don't touch - distance shows gap between them")

print(f"\n\nTFs WITH HIGHEST AVERAGE OVERLAP LENGTH WITH {REFERENCE_TF}:")

top_overlap = detailed_df.nlargest(10, 'Mean_overlap_bp_all')[['TF', 'Mean_overlap_bp_all', 'Median_overlap_bp_all']]

print(top_overlap.to_string(index=False))

print(f"\n\nTFs WITH CLOSEST NON-OVERLAPPING PEAKS TO {REFERENCE_TF}:")

closest_tfs = detailed_df[detailed_df['No_overlaps'] > 0].nsmallest(10, 'Mean_distance_no_overlap')[

['TF', 'No_overlaps', 'Mean_distance_no_overlap', 'Min_distance_no_overlap']

]

if len(closest_tfs) > 0:

print(closest_tfs.to_string(index=False))

else:

print("All peaks overlap - no distance data available")

# ====================================================================

# VISUALIZATIONS

# ====================================================================

import matplotlib.pyplot as plt

import seaborn as sns

sns.set_style("whitegrid")

fig = plt.figure(figsize=(20, 16))

gs = fig.add_gridspec(4, 2, hspace=0.35, wspace=0.25)

# Plot 1: Mean overlap length

ax1 = fig.add_subplot(gs[0, :])

top_15 = detailed_df.nlargest(15, 'Mean_overlap_bp_all')

bars1 = ax1.barh(range(len(top_15)), top_15['Mean_overlap_bp_all'], color='steelblue', edgecolor='black', alpha=0.8)

ax1.set_yticks(range(len(top_15)))

ax1.set_yticklabels(top_15['TF'], fontsize=11, fontweight='bold')

ax1.set_xlabel('Mean Overlap Length (bp)', fontsize=13, fontweight='bold')

ax1.set_title(f'Top 15 TFs by Average Overlap with {REFERENCE_TF}\n({center_window}bp window)', fontsize=15, fontweight='bold')

ax1.invert_yaxis()

ax1.axvline(center_window, color='red', linestyle='--', linewidth=2, alpha=0.7, label=f'Complete overlap ({center_window}bp)')

ax1.legend(fontsize=10)

ax1.spines['top'].set_visible(False)

ax1.spines['right'].set_visible(False)

for i, (bar, val) in enumerate(zip(bars1, top_15['Mean_overlap_bp_all'])):

ax1.text(val + 0.3, i, f'{val:.1f}bp', va='center', fontsize=9, fontweight='bold')

# Plot 2: Complete vs Partial overlap counts

ax2 = fig.add_subplot(gs[1, 0])

top_15_overlap = detailed_df.nlargest(15, 'Complete_overlaps')

x = np.arange(len(top_15_overlap))

width = 0.35

bars2a = ax2.bar(x - width/2, top_15_overlap['Complete_overlaps'], width,

label=f'Complete (≥{center_window}bp)', color='darkgreen', edgecolor='black', alpha=0.8)

bars2b = ax2.bar(x + width/2, top_15_overlap['Partial_overlaps'], width,

label=f'Partial (1-{center_window-1}bp)', color='orange', edgecolor='black', alpha=0.8)

ax2.set_xlabel('Transcription Factor', fontsize=12, fontweight='bold')

ax2.set_ylabel('Number of Overlaps', fontsize=12, fontweight='bold')

ax2.set_title(f'Complete vs Partial Overlaps with {REFERENCE_TF}', fontsize=14, fontweight='bold')

ax2.set_xticks(x)

ax2.set_xticklabels(top_15_overlap['TF'], rotation=45, ha='right', fontsize=9)

ax2.legend(fontsize=10)

ax2.spines['top'].set_visible(False)

ax2.spines['right'].set_visible(False)

ax2.grid(True, alpha=0.3, axis='y')

# Plot 3: Mean overlap length by type

ax3 = fig.add_subplot(gs[1, 1])

top_15_mean = detailed_df.nlargest(15, 'Mean_overlap_bp_all')

x3 = np.arange(len(top_15_mean))

bars3a = ax3.bar(x3 - width/2, top_15_mean['Mean_overlap_bp_complete'], width,

label='Complete overlaps', color='darkgreen', edgecolor='black', alpha=0.8)

bars3b = ax3.bar(x3 + width/2, top_15_mean['Mean_overlap_bp_partial'], width,

label='Partial overlaps', color='orange', edgecolor='black', alpha=0.8)

ax3.set_xlabel('Transcription Factor', fontsize=12, fontweight='bold')

ax3.set_ylabel('Mean Overlap Length (bp)', fontsize=12, fontweight='bold')

ax3.set_title('Mean Overlap Length by Type', fontsize=14, fontweight='bold')

ax3.set_xticks(x3)

ax3.set_xticklabels(top_15_mean['TF'], rotation=45, ha='right', fontsize=9)

ax3.legend(fontsize=10)

ax3.axhline(center_window, color='red', linestyle='--', linewidth=1, alpha=0.5)

ax3.spines['top'].set_visible(False)

ax3.spines['right'].set_visible(False)

ax3.grid(True, alpha=0.3, axis='y')

# Plot 4: Distance analysis

ax4 = fig.add_subplot(gs[2, :])

distance_data = detailed_df[detailed_df['No_overlaps'] > 0].nsmallest(15, 'Mean_distance_no_overlap')

if len(distance_data) > 0:

bars4 = ax4.barh(range(len(distance_data)), distance_data['Mean_distance_no_overlap'],

color='coral', edgecolor='black', alpha=0.8)

ax4.set_yticks(range(len(distance_data)))

ax4.set_yticklabels(distance_data['TF'], fontsize=11, fontweight='bold')

ax4.set_xlabel(f'Mean Distance to Nearest {REFERENCE_TF} Peak (bp)', fontsize=13, fontweight='bold')

ax4.set_title(f'TFs with Closest Non-Overlapping Peaks to {REFERENCE_TF}', fontsize=15, fontweight='bold')

ax4.invert_yaxis()

ax4.spines['top'].set_visible(False)

ax4.spines['right'].set_visible(False)

for i, (bar, val) in enumerate(zip(bars4, distance_data['Mean_distance_no_overlap'])):

ax4.text(val + 5, i, f'{val:.0f}bp', va='center', fontsize=9, fontweight='bold')

else:

ax4.text(0.5, 0.5, 'All peaks overlap - no distance data', ha='center', va='center',

transform=ax4.transAxes, fontsize=12)

ax4.axis('off')

# Plot 5: Scatter - Overlap vs Distance

ax5 = fig.add_subplot(gs[3, 0])

scatter_data = detailed_df[detailed_df['Mean_distance_no_overlap'] > 0]

if len(scatter_data) > 0:

scatter = ax5.scatter(scatter_data['Mean_overlap_bp_all'],

scatter_data['Mean_distance_no_overlap'],

c=scatter_data['Complete_overlaps'],

s=100, cmap='viridis', edgecolor='black', alpha=0.7)

for idx, row in scatter_data.iterrows():

ax5.annotate(row['TF'], (row['Mean_overlap_bp_all'], row['Mean_distance_no_overlap']),

fontsize=8, alpha=0.7)

cbar = plt.colorbar(scatter, ax=ax5)

cbar.set_label('Complete Overlaps', fontsize=10)

ax5.set_xlabel('Mean Overlap Length (bp)', fontsize=12, fontweight='bold')

ax5.set_ylabel('Mean Distance (bp)', fontsize=12, fontweight='bold')

ax5.set_title('Overlap Length vs Distance', fontsize=13, fontweight='bold')

ax5.spines['top'].set_visible(False)

ax5.spines['right'].set_visible(False)

ax5.grid(True, alpha=0.3)

# Plot 6: Proportion stacked bars

ax6 = fig.add_subplot(gs[3, 1])

top_15_prop = detailed_df.nlargest(15, 'Total_sites')

total_sites = top_15_prop['Total_sites']

complete_prop = (top_15_prop['Complete_overlaps'] / total_sites) * 100

partial_prop = (top_15_prop['Partial_overlaps'] / total_sites) * 100

no_overlap_prop = (top_15_prop['No_overlaps'] / total_sites) * 100

x6 = np.arange(len(top_15_prop))

ax6.barh(x6, complete_prop, label=f'Complete (≥{center_window}bp)', color='darkgreen', edgecolor='black')

ax6.barh(x6, partial_prop, left=complete_prop, label=f'Partial (1-{center_window-1}bp)', color='orange', edgecolor='black')

ax6.barh(x6, no_overlap_prop, left=complete_prop + partial_prop, label='No overlap', color='lightcoral', edgecolor='black')

ax6.set_yticks(x6)

ax6.set_yticklabels(top_15_prop['TF'], fontsize=10, fontweight='bold')

ax6.set_xlabel('Percentage of Total Sites (%)', fontsize=12, fontweight='bold')

ax6.set_title(f'Overlap Distribution with {REFERENCE_TF}', fontsize=13, fontweight='bold')

ax6.legend(fontsize=9, loc='lower right')

ax6.invert_yaxis()

ax6.spines['top'].set_visible(False)

ax6.spines['right'].set_visible(False)

ax6.set_xlim(0, 100)

plt.tight_layout()

plt.show()

print("\n" + "="*80)

print("ANALYSIS COMPLETE")

print("="*80)

print(f"\nTo analyze a different TF, change REFERENCE_TF at the top of this cell and re-run.")
```


```
# Multi-TF Overlap Analysis - Analyze top TFs and create comparative visualizations

import pandas as pd

import numpy as np

import pyranges as pr

import matplotlib.pyplot as plt

import seaborn as sns

  

# ============================================================================

# CONFIGURATION

# ============================================================================

N_REFERENCE_TFS = 20 # Number of top TFs to analyze as reference

center_window = 15 # Window size in bp

# ============================================================================

  

# Check if required variables exist

try:

all_bed_files

bed_dir

except NameError:

print("="*80)

print("ERROR: Required variables not found")

print("="*80)

print("\nPlease run the cells that load BED files first.")

else:

print("="*80)

print(f"MULTI-TF COMPARATIVE OVERLAP ANALYSIS")

print(f"Analyzing top {N_REFERENCE_TFS} TFs by binding site count")

print(f"Using {center_window}bp centered windows")

print("="*80)

# Step 1: Get top N TFs by total binding sites

tf_sizes = []

for bed_file in all_bed_files:

tf_name = bed_file.stem.replace("-human.merged", "").replace("-human", "")

df = pd.read_csv(bed_file, sep='\t', header=None, usecols=[0, 1, 2])

tf_sizes.append({'TF': tf_name, 'Total_sites': len(df)})

tf_sizes_df = pd.DataFrame(tf_sizes).sort_values('Total_sites', ascending=False)

top_tfs_list = tf_sizes_df.head(N_REFERENCE_TFS)['TF'].tolist()

print(f"\nSelected top {N_REFERENCE_TFS} TFs:")

print(", ".join(top_tfs_list))

# Step 2: For each reference TF, calculate overlaps with all other TFs

print(f"\nAnalyzing overlaps...")

all_tf_results = {}

for ref_idx, reference_tf in enumerate(top_tfs_list, 1):

print(f"\rProcessing {ref_idx}/{N_REFERENCE_TFS}: {reference_tf}", end="", flush=True)

# Load reference TF

ref_bed = bed_dir / f"{reference_tf}-human.merged.bed"

if not ref_bed.exists():

ref_bed = bed_dir / f"{reference_tf}-human.bed"

if not ref_bed.exists():

continue

ref_df = pd.read_csv(ref_bed, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

ref_df_centered = ref_df.copy()

ref_df_centered['center'] = (ref_df_centered['start'] + ref_df_centered['end']) // 2

ref_df_centered['start_centered'] = ref_df_centered['center'] - center_window // 2

ref_df_centered['end_centered'] = ref_df_centered['center'] + center_window // 2

ref_centered_pr = pr.PyRanges(ref_df_centered.rename(columns={

'chr': 'Chromosome',

'start_centered': 'Start',

'end_centered': 'End'

}))

# Calculate overlaps with all other TFs

tf_overlaps = {}

for bed_file in all_bed_files:

other_tf = bed_file.stem.replace("-human.merged", "").replace("-human", "")

if other_tf == reference_tf:

continue

other_df = pd.read_csv(bed_file, sep='\t', header=None, usecols=[0, 1, 2], names=['chr', 'start', 'end'])

other_df_centered = other_df.copy()

other_df_centered['center'] = (other_df_centered['start'] + other_df_centered['end']) // 2

other_df_centered['start_centered'] = other_df_centered['center'] - center_window // 2

other_df_centered['end_centered'] = other_df_centered['center'] + center_window // 2

other_centered_pr = pr.PyRanges(other_df_centered.rename(columns={

'chr': 'Chromosome',

'start_centered': 'Start',

'end_centered': 'End'

}))

# Calculate intersection

intersect_pr = ref_centered_pr.join(other_centered_pr, suffix="_other")

complete_count = 0

partial_count = 0

mean_overlap = 0.0

if len(intersect_pr) > 0:

join_df = intersect_pr.df

overlap_lengths = np.minimum(join_df['End'], join_df['End_other']) - np.maximum(join_df['Start'], join_df['Start_other'])

complete_mask = overlap_lengths >= center_window

partial_mask = (overlap_lengths > 0) & (overlap_lengths < center_window)

complete_count = int(complete_mask.sum())

partial_count = int(partial_mask.sum())

mean_overlap = float(overlap_lengths.mean())

total_other = len(other_df_centered)

no_overlap_count = total_other - complete_count - partial_count

tf_overlaps[other_tf] = {

'Complete': complete_count,

'Partial': partial_count,

'None': no_overlap_count,

'Total': total_other,

'Mean_overlap_bp': mean_overlap,

'Pct_complete': (complete_count / total_other * 100) if total_other > 0 else 0,

'Pct_partial': (partial_count / total_other * 100) if total_other > 0 else 0

}

all_tf_results[reference_tf] = tf_overlaps

print(f"\n\nAnalysis complete for {len(all_tf_results)} reference TFs")

# Step 3: Create comprehensive visualizations

# ========================================================================

# Prepare data for plotting

cobinding_summary = []

for ref_tf, partners in all_tf_results.items():

for partner_tf, stats in partners.items():

cobinding_summary.append({

'Reference_TF': ref_tf,

'Partner_TF': partner_tf,

'Complete_overlaps': stats['Complete'],

'Partial_overlaps': stats['Partial'],

'No_overlaps': stats['None'],

'Total_sites': stats['Total'],

'Mean_overlap_bp': stats['Mean_overlap_bp'],

'Pct_complete': stats['Pct_complete'],

'Pct_partial': stats['Pct_partial']

})

cobinding_df = pd.DataFrame(cobinding_summary)

print(f"\nGenerated {len(cobinding_df):,} TF pair comparisons")

# ========================================================================

# CREATE VISUALIZATIONS

# ========================================================================

sns.set_style("whitegrid")

fig = plt.figure(figsize=(20, 12))

gs = fig.add_gridspec(2, 3, hspace=0.35, wspace=0.35)

# Plot 1: Top co-binding pairs by partial overlap

ax1 = fig.add_subplot(gs[0, 0])

top_pairs = cobinding_df.nlargest(20, 'Pct_partial')

pair_labels = [f"{row['Reference_TF'][:7]}-{row['Partner_TF'][:7]}" for _, row in top_pairs.iterrows()]

bars1 = ax1.barh(range(len(top_pairs)), top_pairs['Pct_partial'],

color='orange', edgecolor='black', alpha=0.8)

ax1.set_yticks(range(len(top_pairs)))

ax1.set_yticklabels(pair_labels, fontsize=8)

ax1.set_xlabel('% Partial Overlap', fontsize=11, fontweight='bold')

ax1.set_title('Top 20 TF Pairs\nby Partial Overlap', fontsize=12, fontweight='bold')

ax1.invert_yaxis()

ax1.spines['top'].set_visible(False)

ax1.spines['right'].set_visible(False)

for i, val in enumerate(top_pairs['Pct_partial']):

if val > 1:

ax1.text(val + 0.3, i, f'{val:.1f}%', va='center', fontsize=7)

# Plot 2: Distribution of partial overlap percentages

ax2 = fig.add_subplot(gs[0, 1])

ax2.hist(cobinding_df['Pct_partial'], bins=40, color='steelblue', edgecolor='black', alpha=0.7)

ax2.axvline(cobinding_df['Pct_partial'].median(), color='red', linestyle='--',

linewidth=2, label=f'Median: {cobinding_df["Pct_partial"].median():.1f}%')

ax2.axvline(cobinding_df['Pct_partial'].mean(), color='orange', linestyle='--',

linewidth=2, label=f'Mean: {cobinding_df["Pct_partial"].mean():.1f}%')

ax2.set_xlabel('% Partial Overlap', fontsize=11, fontweight='bold')

ax2.set_ylabel('Frequency', fontsize=11, fontweight='bold')

ax2.set_title('Distribution of Partial Overlap %', fontsize=12, fontweight='bold')

ax2.legend(fontsize=9)

ax2.spines['top'].set_visible(False)

ax2.spines['right'].set_visible(False)

ax2.grid(True, alpha=0.3, axis='y')

# Plot 3: Mean overlap length distribution

ax3 = fig.add_subplot(gs[0, 2])

overlap_data = cobinding_df[cobinding_df['Mean_overlap_bp'] > 0]

ax3.hist(overlap_data['Mean_overlap_bp'], bins=40, color='coral', edgecolor='black', alpha=0.7)

ax3.axvline(center_window, color='red', linestyle='--', linewidth=2,

label=f'Window: {center_window}bp')

ax3.axvline(overlap_data['Mean_overlap_bp'].median(), color='blue', linestyle='--',

linewidth=2, label=f'Median: {overlap_data["Mean_overlap_bp"].median():.1f}bp')

ax3.set_xlabel('Mean Overlap Length (bp)', fontsize=11, fontweight='bold')

ax3.set_ylabel('Frequency', fontsize=11, fontweight='bold')

ax3.set_title('Distribution of Mean Overlap Lengths', fontsize=12, fontweight='bold')

ax3.legend(fontsize=9)

ax3.spines['top'].set_visible(False)

ax3.spines['right'].set_visible(False)

ax3.grid(True, alpha=0.3, axis='y')

# Plot 4: Heatmap of top partners

ax4 = fig.add_subplot(gs[1, :2])

# Create heatmap data

heatmap_rows = []

for ref_tf in top_tfs_list:

ref_data = cobinding_df[cobinding_df['Reference_TF'] == ref_tf]

top_partners = ref_data.nlargest(10, 'Pct_partial')

for _, row in top_partners.iterrows():

heatmap_rows.append({

'Reference': ref_tf,

'Partner': row['Partner_TF'],

'Overlap_Pct': row['Pct_partial']

})

if len(heatmap_rows) > 0:

heatmap_df = pd.DataFrame(heatmap_rows)

heatmap_pivot = heatmap_df.pivot_table(

index='Partner',

columns='Reference',

values='Overlap_Pct',

fill_value=0

)

sns.heatmap(heatmap_pivot, annot=True, fmt='.1f', cmap='YlOrRd',

cbar_kws={'label': '% Partial Overlap'}, ax=ax4,

linewidths=0.5, linecolor='white', annot_kws={'fontsize': 7})

ax4.set_title(f'Top 10 Co-binding Partners per Reference TF\n(Partial Overlap %)',

fontsize=13, fontweight='bold', pad=10)

ax4.set_xlabel('Reference TF', fontsize=11, fontweight='bold')

ax4.set_ylabel('Partner TF', fontsize=11, fontweight='bold')

plt.setp(ax4.get_xticklabels(), rotation=45, ha='right', fontsize=9)

plt.setp(ax4.get_yticklabels(), rotation=0, fontsize=8)

# Plot 5: Average co-binding profile

ax5 = fig.add_subplot(gs[1, 2])

ref_tf_summary = []

for ref_tf in top_tfs_list:

ref_data = cobinding_df[cobinding_df['Reference_TF'] == ref_tf]

ref_tf_summary.append({

'Reference_TF': ref_tf,

'Mean_partial_pct': ref_data['Pct_partial'].mean(),

'Mean_complete_pct': ref_data['Pct_complete'].mean(),

'N_partners': len(ref_data)

})

ref_summary_df = pd.DataFrame(ref_tf_summary).sort_values('Mean_partial_pct', ascending=False)

x5 = np.arange(len(ref_summary_df))

width = 0.35

bars5a = ax5.bar(x5 - width/2, ref_summary_df['Mean_complete_pct'], width,

label=f'Complete (≥{center_window}bp)', color='darkgreen',

edgecolor='black', alpha=0.8)

bars5b = ax5.bar(x5 + width/2, ref_summary_df['Mean_partial_pct'], width,

label=f'Partial (1-{center_window-1}bp)', color='orange',

edgecolor='black', alpha=0.8)

ax5.set_xlabel('Reference TF', fontsize=11, fontweight='bold')

ax5.set_ylabel('Avg Overlap %', fontsize=11, fontweight='bold')

ax5.set_title(f'Avg Co-binding Profile\n({N_REFERENCE_TFS} Reference TFs)',

fontsize=12, fontweight='bold')

ax5.set_xticks(x5)

ax5.set_xticklabels(ref_summary_df['Reference_TF'], rotation=45, ha='right', fontsize=9)

ax5.legend(fontsize=9)

ax5.spines['top'].set_visible(False)

ax5.spines['right'].set_visible(False)

ax5.grid(True, alpha=0.3, axis='y')

plt.tight_layout()

plt.show()

# ========================================================================

# SUMMARY STATISTICS

# ========================================================================

print("\n" + "="*80)

print("MULTI-TF OVERLAP ANALYSIS SUMMARY")

print("="*80)

print(f"\n1. OVERALL STATISTICS:")

print(f" - Total TF pairs analyzed: {len(cobinding_df):,}")

print(f" - Reference TFs analyzed: {len(all_tf_results)}")

print(f" - Window size: {center_window}bp")

print(f"\n2. PARTIAL OVERLAP STATISTICS:")

print(f" - Mean % partial overlap: {cobinding_df['Pct_partial'].mean():.2f}%")

print(f" - Median % partial overlap: {cobinding_df['Pct_partial'].median():.2f}%")

print(f" - Max % partial overlap: {cobinding_df['Pct_partial'].max():.2f}%")

print(f" - TF pairs with >10% partial overlap: {(cobinding_df['Pct_partial'] > 10).sum():,}")

print(f"\n3. COMPLETE OVERLAP STATISTICS:")

print(f" - Mean % complete overlap: {cobinding_df['Pct_complete'].mean():.2f}%")

print(f" - Max % complete overlap: {cobinding_df['Pct_complete'].max():.2f}%")

print(f" - TF pairs with >10% complete overlap: {(cobinding_df['Pct_complete'] > 10).sum():,}")

print(f"\n4. OVERLAP LENGTH STATISTICS:")

overlap_nonzero = cobinding_df[cobinding_df['Mean_overlap_bp'] > 0]

print(f" - Mean overlap length: {overlap_nonzero['Mean_overlap_bp'].mean():.2f}bp")

print(f" - Median overlap length: {overlap_nonzero['Mean_overlap_bp'].median():.2f}bp")

print(f"\n5. TOP 5 MOST PROMISCUOUS TFs (by avg partial overlap):")

for idx, row in ref_summary_df.head(5).iterrows():

print(f" {row['Reference_TF']:15s} - {row['Mean_partial_pct']:.2f}% avg partial overlap")

print(f"\n6. TOP 5 STRONGEST TF PAIRS:")

top_5_pairs = cobinding_df.nlargest(5, 'Pct_partial')

for idx, row in top_5_pairs.iterrows():

print(f" {row['Reference_TF']:10s} × {row['Partner_TF']:10s} - {row['Pct_partial']:.1f}% partial")

print("\n" + "="*80)

print("ANALYSIS COMPLETE")

print("="*80)
```