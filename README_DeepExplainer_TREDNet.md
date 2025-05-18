# Guide to Run DeepExplainer_TREDNet on Biowulf

This guide explains how to run SHAP DeepExplainer with TREDNet models on Biowulf using the preconfigured scripts.

**Author:** Gaetano Manzo  
**Date:** Apr 25, 2025

---

## Table of Contents

1. [Step 1: Copy the Folder](#step-1-copy-the-folder)
2. [Step 2: Customize the submit2biowulf Script](#step-2-customize-the-submit2biowulf-script)
3. [Step 3: Submit the Job](#step-3-submit-the-job)
4. [Alternative: Interactive Jupyter Notebook](#alternative-interactive-jupyter-notebook)
5. [Output](#output)

---

## Step 1: Copy the Folder

First, copy the working directory to your personal space on Biowulf:

```bash
cp -r /data/Dcode/gaetano/DeepExplainer_TREDNet /data/Dcode/YOUR_USERNAME/
```

Replace `YOUR_USERNAME` with your actual Dcode user folder.

---

## Step 2: Customize the submit2biowulf Script

Go into your copy of the folder:

```bash
cd /data/Dcode/YOUR_USERNAME/DeepExplainer_TREDNet
```

Open `submit2biowulf` and customize the following fields under **USER CONFIGURATION**:

- `EID="YourExperimentID"`
- `TREDNET_MODEL_I_PATH="/path/to/TREDNet_I"`
- `TREDNET_MODEL_II_PATH="/path/to/TREDNet_II"`
- `INPUT_SEQS_POS="/path/to/positive_sequences.bed"`
- `INPUT_SEQS_CTRL="/path/to/control_sequences.bed"`
- `NUM_GPUS=4`
- `TYP_GPU="v100x"`  *(or "a100")*

Make sure **no trailing slashes (/) are added** to paths.

---

## Step 3: Submit the Job

Simply run the following command:

```bash
sh submit2biowulf
```

This will:

- Create a timestamped output directory (e.g., `output/HNF4A_sample_2025-04-25_13-42-01`).
- Copy and configure the required scripts into the new directory.
- Launch a job on Biowulf using `sbatch` with the selected number/type of GPUs.

---

## Output

After completion, you’ll find the following:

- All results inside the `output/YOUR_EID_TIMESTAMP/` folder.
- Logs in `*.log.out` and `*.log.err`.
- A SHAP summary plot and `.npy` files containing the SHAP values.

---

## Alternative: Interactive Jupyter Notebook

If you prefer running the analysis interactively (e.g., for prototyping or debugging), you can launch the Jupyter notebook version:

### Steps:

1. Navigate to the folder:

    ```bash
    cd notebook
    ```

2. Create an environment:

    **Using Conda**:

    ```bash
    conda env create -f environment.yaml
    conda activate DeepExplainer_TREDNet
    ```

    **Using Pip**:

    ```bash
    python -m venv deepexplainer_env
    source deepexplainer_env/bin/activate
    pip install -r requirements.txt
    ```

3. Run your analysis:

    Open `DeepExplainer_TREDNet.ipynb` and edit only the **INPUTS** section (the first cell), where you provide your model paths, BED files, and BIOS ID. That’s all the configuration needed.

---

## Contact

**Author:** Gaetano Manzo  
**Date:** Apr 25, 2025

---

## License

This code is provided under the MIT license.