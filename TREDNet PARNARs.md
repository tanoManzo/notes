This readme file is for how to train PAR/NAR model from Chip-seq peaks and use trained model to scan enhancer sequences for PAR/NAR
## Step 0: Train the TREDNet Model with Enhancer Coordinates
**To Do:**
1. **Navigate to the Training Directory:**
   Go to the path:  
   `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/TREDNet`

2. **Submit the Training Job:**
   Run the script to start the training:  
   `sh submit_local_jobs.sh H1`  
   This will train the model using data from H1 enhancers. You can replace H1 with any bio samples in the input files directory.

**Input Files:**
   The input data is located at:  
   `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/input_training_trednet`  
   The complete input file is located in: 
   `/data/Dcode/common/CenTRED/hg38/green_celllines/CenTRED_training_files`
   For simplicity, the pre-processed dataset for HepG2 is available in HDF5 format at:  
   `/data/Dcode/common/CenTRED/hg38/green_celllines/CenTRED_models/BioS11/phase_two_dataset.hdf5`

**Output:**
   The trained model will be saved in the following directory:  
   `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/CenTRED_models/part1`

Here’s a clearer, well-structured version of your description:  

---

## Step 1: Training the PAR/NAR Model

This section outlines the steps to train the PAR/NAR model using motif positions predicted by FIMO as true TF binding sites, generating input datasets, and training the model.  

### **1.1. Define Positive TF Binding Sites**  
FIMO-predicted motif positions serve as **true TF binding sites** and are stored in:  
📂 `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/PARNNAR_model/FIMO_identified_Chipseq_TFBS`  

- The file **`total_final_chip2fimo_HepG2.pvaluee_04.merged`** contains motif locations scanned by FIMO across **all HepG2 TF ChIP-seq peaks**.  
- For example, **HNF4A motif positions** are identified within **HNF4A ChIP-seq peaks**.  
- These motif locations will be used as **positive training sets** for the PAR/NAR model.  

---

### **1.2. Generate Input Positive and Control Sets**  
📂 **Directory:** `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/PARNNAR_model/step1_input_PARNNAR`  

#### **Step 1: Create Positive and Control Sets**  
Run `submit_step0_inputfile.sh` to:  
✅ Overlap **HepG2 enhancers** with **motif locations** from Step 1.1 to create the **positive sets**.  
✅ Generate **control sets** from **HepG2 enhancer regions** that **exclude** motif locations.  

🔹 **Output Files:**  
- `list_control_in_enhancer.bed` (control sets)  
- `list_motif_in_enhancer.bed` (positive sets)  

#### **Step 2: Extract Features for Each Nucleotide**  
Run `submit_step1_genebasepair_bychrom.sh` to generate **220 features** per nucleotide in the **positive and control sets** (separately for peak/dip regions).  

📝 **Requires:** Precomputed **normalized delta scores** per nucleotide.  
📂 **Delta Score Input:** `/data/Dcode/common/CenTRED_for_Mehari_94biosamples/gene_mutagenesis/output_deltascore/BioS11_1kb/output.txt.total.BioS11.fpr5.normscore.newformat`  

🔹 **Feature Output Files (for chromosome 1 as an example):**  
- `list_control_in_enhancer.bed.withenh.feature.chr1`  
- `list_motif_in_enhancer.bed.withenh.dip.feature.chr1`  
- `list_motif_in_enhancer.bed.withenh.peak.feature.chr1`  

#### **Step 3: Split Data into Training and Testing Sets**  
Run `submit_step2_split.sh` to:  
✅ **Merge feature files** containing 220 features.  
✅ **Split data** into training and testing sets:  
   - **Training set:** Excludes chromosomes **8 and 9**  
   - **Testing set:** Includes chromosomes **8 and 9**  

🔹 **Output Files:**  
- `input_peak.train`, `input_peak.test`  
- `input_dip.train`, `input_dip.test`  



### **1.3. Train the PAR/NAR Model**  
📂 **Directory:** `/data/Dcode/common/CenTRED_for_Mehari_94biosamples/PARNNAR_model/step2_train_PARNNAR`  

Using the training and testing sets from Step 1.2, train the **PAR/NAR model**.  

🔹 **Output File:**  
- `BioS11_HepG2hg38_peak`  

---