This readme file is for how to train PAR/NAR model from Chip-seq peaks and use trained model to scan enhancer sequences for PAR/NAR
### Step 0: Train the TREDNet Model with Enhancer Coordinates

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

## Step 1:train PAR/NAR model: /data/Dcode/common/CenTRED_for_Mehari_94biosamples/PARNNAR_model
/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/PARNNAR_model
	1.1. FIMO predicted motif positions as "true TF binding sites" in the directory: 
	/data/Dcode/common/CenTRED_for_Mehari_94biosamples/PARNNAR_model/FIMO_identified_Chipseq_TFBS
	file total_final_chip2fimo_HepG2.pvaluee_04.merged is from FIMO scanned motif location in 
	all HepG2 TF Chip-seq peaks and combined together, 
	eg, HNF4A motif position located in HNF4A Chip-seq peaks. 
	These motif locations will be the positive sets for PAR/NAR model training
 