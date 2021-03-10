# Project_C3a_peri-infarct
Project repository C3a peri-infarct study
<img align="left" src="https://github.com/aswendtlab/Project_C3a_peri-infarct/blob/main/C3a_peri-infarct_v2%20copy.png">

## Step-by-Step guide to replicate the analysis

1. Install [AIDAmri](https://github.com/aswendtlab/AIDAmri) and [AIDAconnect](https://github.com/aswendtlab/AIDAconnect)

2. Download MRI raw data (and proc data for comparison) from [G-Node](https://doi.org/10.12751/g-node.699mgv)

3. Run AIDAmri pre- and postprocessing steps for T2 and DTI data, see [manual](https://github.com/aswendtlab/AIDAmri/blob/master/manual.pdf)

5. Extract the graph theoretical measure global density using AIDAconnect and Matlab
  * ```mergeDTIdata_input.m and plotGlobalParameter(inputDTI, graphCell, 'Density')```
  
6. Run peri-infarct specific Python scripts (4.1_ROI_analysis in AIDAmri)
  * Adapt ```proc_tools.py``` to your folder structure
  * Run ```python proc_tools.py; python 01_dilate_mask_process.py; python 02_apply_xfm_process.py; python 03_create_seed_rois_process_npflip.py; python 04_examine_rois```sequentially
  * The output of ```04_examine_rois```is ROIs_count_voxels.txt with the number of voxels inside the peri-infarct mask per brain region (Allen Mouse Brain Atlas label number). This is used to determine which regions to include in the analysis, here: ACA, SSp-ll/m/ul, SSs, MOp, MOs, and GU: ![image](https://user-images.githubusercontent.com/79273576/110662916-3f461f80-81c6-11eb-890d-9f45d7b22390.png)

7. Use the [iterativeRun_MA_peri-infarct_ROIs.py](https://github.com/aswendtlab/Project_C3a_peri-infarct/blob/main/iterativeRun_MA_peri-infarct_ROIs.py) script to extract diffusion measures (FA, AD, RD, MD) for each atlas region

8. Retrieve the atlas region-specific diffusion measures from the stored .txt files
> e.g. C3a_PT_8wks_T2w_DTI/MRI_proc_data/P56/Treatment_C3a/GV_T3_12_1_1_8_20191008_102322/DTI/DSI_studio/GV_T3_12_1_1_8_20191008_102322_T2w_Anno_DTI_mod_peri_scaled_fa0.txt 

(first column: atlas number, second column: atlas label, third: value)

![image](https://user-images.githubusercontent.com/32373094/109677970-78eda980-7b7a-11eb-92da-2d5c9d140114.png)


