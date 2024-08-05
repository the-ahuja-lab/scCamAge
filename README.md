<div align="center"> <h1>scCamAge </h1> </div>
 <br>
<div align="center">
<img src="Data/Images/scCamAge.png"></div>

<div align="center"><b>scCamAge: A Context-Aware Prediction Engine for Aging-Associated Bioactivities and Morphometrics</b></div><br><br>
An advanced transfer learning framework utilizing spatiotemporal information from phase-contrast images to predict yeast cell age at single-cell resolution. In addition, scCamAge integrates predictive models for various aging-related biological processes, such as genomic instability, reactive oxygen species, mitochondrial content, and potential, among others, and also calculates cellular morphometric parameters.


<div align="center"> <h1>scCamAge Docker Container </h1> </div>
<br>
<br>
<div align="center">
<img src="/Data/Images/Docker_CamAge1.png"></div>
<br>

This is the repo of the official [Docker image](https://hub.docker.com/r/ahujalab/camage) for **scCamAge**.


You can find instructions for installing and running Docker on any PC using the following [links](https://docs.docker.com/engine/install/) 
1. [Windows](https://docs.docker.com/desktop/install/windows-install/)
2. [MacOS](https://docs.docker.com/desktop/install/mac-install/)
3. [Linux](https://docs.docker.com/desktop/install/linux-install/)


---

<h3>Pulling the scCamAge Image</h3>

Pull the **scCamAge image** from Docker Hub by running the following command in your terminal:

```
$ docker pull ahujalab/camage
```
<h3>Verifying the Image</h3><br>

Verify the new image has been created using the **docker images** command.
```
$ docker images
```
<h3>Accessing the Docker Image Terminal</h3><br>

To access the terminal of a **Docker container**, use the docker run command with the **-it** option.
```
$ docker run -it <image-name> bash
```

<h3>Managing Containers</h3><br>

Replace **<image-name\>** with the name or ID of the Docker image of **scCamAge**.

Find the ID of the currently running container for **input** and **output**.
```
$ docker ps -a
```
To start the container again, access its terminal. 
```
$ docker start <container-ID>
$ docker exec -it <container-ID> bash
```
---


## Input/Output

### Input 
Find the ID of the running container using the **docker ps -a** command.
```
$ docker ps -a
```
To write a file to the container, use the **docker cp** command to copy it from the host to the container.
```
$ docker cp file container_id:WDir/
```
This command will copy the **folder** from the host's current directory to the **scCamAge** container with ID **container_id** at the WDir/ directory inside the container.

### Output
Find the ID of the running container using the **docker ps -a** command.
```
$ docker ps -a
```
To write a file from the container, use the **docker cp** command to copy it to the host.
```
$ docker cp container_id:WDir/file-name .
```
This command will copy the **folder** from the **scCamAge** container with ID **container_id** under the WDir/ directory inside the container to the host's current directory.

---



## Running scCamAge
There are two scCamAge Docker images available: one optimized for GPU usage and the other for CPU. Users can select the appropriate image based on their specific requirements.

## 1. Segmenter
This command segments yeast cell images.
```
$ segmenter -id raw_input_folder -od segmenter_output_folder
```
<b>Additional arguments:</b>

| Arguments | Description |
| -------- | -------- |
| id | Input the folder path containing the raw images of yeast cells. |
| od | Output folder path for the segmented images |

<b>Returns:</b>

~ masks: segmented file for the raw images <br>
~ preprocessed_images: preprocessed images of raw yeast cells <br>
~ compressed_masks.csv: compressed masked .csv for raw yeast cells <br>



## 2. Predictor
This command processes raw yeast images, converts them into single-cell yeast images, and provides scCamAge predictions.

<b>Basic Usage</b>
```
$ predictor -id raw_input_folder -od prediction_output -segmented segmenter_output_folder -SCImages sc_output_folder
```
<b> Advanced Usage</b>
```
$ predictor -id raw_input_folder -od prediction_output -segmented segmenter_output_folder -SCImages sc_output_folder explainability -image_features -num_features 3 -bio_prediction
```
<b>Additional arguments:</b>

| Arguments | Description |
| -------- | -------- |
| id | Input the folder path containing the raw images of yeast cells|
| od | Output folder path for the scCamAge predictions|
| segmented | Output folder path for the segmented images|
| SCImages | Output folder path for single-cell yeast images|
| explainability | Generate explainability plots for the predictions|
| num_features | Number of top features to include for explainability|
| image_features | Include image features for bioactivity predictions|
| bio_prediction | Generate bioactivity predictions|

<b>Returns:</b><br>
~ Single-cell yeast images<br>
~ Morphometric features<br>
~ A .csv file containing scCamAge predictions and bioactivity predictions<br>
~ Explainability plots for predictions of each image<br>

<div align="center"> <h1>Additional Details </h1> </div>
<br>

## 1. Scripts
Detailed instructions on using the scCamAge scripts are available at <b>Data/CamAge_Scripts</b>

## 2. Datasets
The datasets used for developing scCamAge can be downloaded from [Zenodo](https://zenodo.org/records/11209124)


