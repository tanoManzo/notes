This readme file is for how to train PAR/NAR model from Chip-seq peaks and use trained model to scan enhancer sequences for PAR/NAR
### Step 0: Train the TREDNet Model with Enhancer Coordinates

1. **Navigate to the Training Directory:**
   Go to the path:  
   `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/TREDNet`

2. **Submit the Training Job:**
   Run the script to start the training:  
   `submit_local_jobs.sh`  
   This will train the model using data from H1 enhancers.

3. **Input Files:**
   The input data is located at:  
   `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/input_training_trednet`  
   For simplicity, the pre-processed dataset for HepG2 is available in HDF5 format at:  
   `/data/Dcode/common/CenTRED/hg38/green_celllines/CenTRED_models/BioS11/phase_two_dataset.hdf5`

4. **Output:**
   The trained model will be saved in the following directory:  
   `/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/CenTRED_models/part1`
