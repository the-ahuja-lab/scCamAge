# ReadMe For scripts

Status: Not started

# User Guide for Running Analysis Scripts

## Section 1: Setting Up Environments

Their are two environments that have been used in the CamAge modules, user need to use .yml files for the setting of these environments. This guide is intended for users who will be utilizing scripts to perform analysis.

There are two environments required for the CamAge modules. Users need to configure these environments using the provided .yml files.

| Environment Name | Details |
| --- | --- |
| environment_yeastsegemntation.yml | For segmentation of yeast images |
| environment_CamAge.yml | For CamAge modules |

```bash
conda env create -f environment.yml
```

## Section 2: Segmentation

This section provides detailed steps for using the segmentation module.

---

---

1. Use conda environment yeastsegmentation

```bash
conda activate yeastsegmentation
```

1. Download the folder yeast_segmentation-master

```bash
  wget("https://zenodo.org/records/11184213/files/yeast_segmentation-master.zip?download=1")
```

1. In folder yeast_segmentation-master/opts.py change the input directory and output directory paths
2. Go to yeast_segmentation-master folder and run command 

```bash
python segmentation.py
```

---

---

## Section 3: CamAge Predictor module

This section provides detailed steps for using the CamAge Predictor module.

1. Use conda environment CamAge

```bash
conda activate CamAge
```

1. Download pre-trained models

```bash
  wget("https://zenodo.org/records/11184213/files/Models.zip?download=1")
```

1. Use well commented CamAge_predictor_module.ipynb for the prediction modules.

---

---

## NOTE : Retrain models using CamAge weights

Notebook_to_retrain_dataset.ipynb 

For example purposes we have used CPT dataset ( [https://doi.org/10.5281/zenodo.11184213](https://doi.org/10.5281/zenodo.11184213)).