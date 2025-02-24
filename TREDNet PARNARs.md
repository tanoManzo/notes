This readme file is for how to train PAR/NAR model from Chip-seq peaks and use trained model to scan enhancer sequences for PAR/NAR

## Step 0: Train TREDNet model using enhancers' coordinates
go to path: "/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/TREDNet", and submit "submit_local_jobs.sh" to train a model on H1 enhancers, with input file located in input file localtion: "/data/Dcode/gaetano/CenTRED/CenTRED_for_PARNARs/input_training_trednet"
	 /data/Dcode/common/CenTRED_for_Mehari_94biosamples/input_training_trednet, 
	 the complete input file is located in 
	 /data/Dcode/common/CenTRED/hg38/green_celllines/CenTRED_training_files, 
	 for simplicity, here for HepG2, you can just read dataset in h5 format: 
	 /data/Dcode/common/CenTRED/hg38/green_celllines/CenTRED_models/BioS11/phase_two_dataset.hdf5
	
	0.2. the output model will be stored in 
	/data/Dcode/common/CenTRED_for_Mehari_94biosamples/CenTRED_models/part1