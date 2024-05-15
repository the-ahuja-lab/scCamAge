<div align="center"> <h1>CamAge </h1> </div>
 <br>
<div align="center">
<img src="Data/Images/CamAge.png"></div>

<div align="center"><b>An Image-based Intelligent Lens for single-cell Age Prediction and its Aging-associated Bioactivities</b></div><br><br>
An advanced transfer learning framework utilizing spatiotemporal information from phase-contrast images to predict yeast cell age at single-cell resolution. In addition, CamAge integrates predictive models for various aging-related biological processes, such as genomic instability, reactive oxygen species, mitochondrial content, and potential, among others, and also calculates cellular morphometric parameters.

<div align="center"><h3> How to use the CamAge package<h3></div>

#### Installation of CamAge package
This is a one-time task that must be completed to use the CamAge module
1. Creation of Conda Environment
```bash
conda create --name CamAge
conda activate CamAge
```
2. Installation of CamAge
```Python
pip install torch==2.2.2 torchvision==0.17.2 --index-url https://download.pytorch.org/whl/cu121

```
```Python
pip install -i https://test.pypi.org/simple/ CamAge==0.0.4
```
#### Segmentation of yeast images
```Python
from CamAge.module1.main import perform_segmentation
input_folder = path/to/input_folder
output_folder = path/to/output_folder
perform_segmentation(input_folder,output_folder)
```

#### Extracting micrographs and morphological features
```Python
from CamAge.module2.cont import perform_contour_analysis
perform_contour_analysis(dir_raw, dir_mask, dir_contour, out_dir)
```


