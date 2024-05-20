
# User Guide for Running Analysis Scripts

## Section 1: Setting Up Environments

Two environments have been used in the CamAge modules; users need to use .yml files to set these environments. This guide is intended for users who will be utilizing scripts to perform analysis.


| Environment Name | Details |
| --- | --- |
| environment_yeastsegmentation.yml | For segmentation of yeast images |
| environment_CamAge.yml | For CamAge modules |


```bash
conda env create -f environment.yml
```

## Section 2: Segmentation

This section provides detailed steps for using the segmentation module.

---


1. Use conda environment yeastsegmentation

```bash
conda activate yeastsegmentation
```

2. Download the folder yeast_segmentation-master

```bash
  wget("https://zenodo.org/records/11184213/files/yeast_segmentation-master.zip?download=1")
```

3. In folder yeast_segmentation-master/opts.py change the input directory and output directory paths
4. Go to yeast_segmentation-master folder and run command 

```bash
python segmentation.py
```

---


## Section 3: CamAge Predictor module

This section provides detailed steps for using the CamAge Predictor module.

1. Use conda environment CamAge

```bash
conda activate CamAge
```

2. Download pre-trained models

```bash
  wget("https://zenodo.org/records/11184213/files/Models.zip?download=1")
```

3. Use CamAge_predictor_module.ipynb for the prediction modules.

---


## NOTE: Use the following notebook to retrain models using CamAge weight

Notebook_to_retrain_dataset.ipynb 

For example purposes, we have used the CPT dataset (https://doi.org/10.5281/zenodo.11184213).
