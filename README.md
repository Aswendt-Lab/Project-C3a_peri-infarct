# Project_C3a_peri-infarct
Project repository C3a peri-infarct study
<img align="left" src="https://github.com/aswendtlab/Project_C3a_peri-infarct/blob/main/C3a_peri-infarct_v2%20copy.png">

## Step-by-Step guide to replicate the analysis

1. Install AIDAmri
2. Download MRI raw data (and proc data for comparison) from [G-Node](https://doi.org/10.12751/g-node.699mgv)
3. Run AIDAmri pre- and postprocessing steps for T2 and DTI data
4. Run peri-infarct specific Python scripts (XX in AIDAmri)
  * Adapt proc_tools.py to your folder structure
  * Run ```python 01_dilate_mask_process.py; python 02_apply_xfm_process.py; python 03_create_seed_rois_process_npflip.py```sequentially
5. Use the iteratur... script to extract 
6. Retrieve the atlas region-specific diffusion measures from the stored .txt files, e.g. C3a_PT_8wks_T2w_DTI/MRI_proc_data/P56/Treatment_C3a/GV_T3_12_1_1_8_20191008_102322/DTI/DSI_studio/GV_T3_12_1_1_8_20191008_102322_T2w_Anno_DTI_mod_peri_scaled_fa0.txt (first column: atlas number, second column: atlas label, third: value)

![image](https://user-images.githubusercontent.com/32373094/109677970-78eda980-7b7a-11eb-92da-2d5c9d140114.png)


