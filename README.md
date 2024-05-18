<div align="center"> <h1>CamAge </h1> </div>
 <br>
<div align="center">
<img src="Data/Images/CamAge.png"></div>

<div align="center"><b>An Image-based Intelligent Lens for single-cell Age Prediction and its Aging-associated Bioactivities</b></div><br><br>
An advanced transfer learning framework utilizing spatiotemporal information from phase-contrast images to predict yeast cell age at single-cell resolution. In addition, CamAge integrates predictive models for various aging-related biological processes, such as genomic instability, reactive oxygen species, mitochondrial content, and potential, among others, and also calculates cellular morphometric parameters.

<div align="center"><h3> CamAge Docker container<h3></div>

#### CamAge Docker container
This is the repo of the official [Docker image]() for **CamAge**.


Instructions for installing and running docker on any PC can be found [here](https://docs.docker.com/engine/install/) 
1. [Windows](https://docs.docker.com/desktop/install/windows-install/)
2. [MacOS](https://docs.docker.com/desktop/install/mac-install/)
3. [Linux](https://docs.docker.com/desktop/install/linux-install/)

Pull the **CamAge** image from Docker Hub by running the following command in your terminal:
```
$ docker pull 
```
Verify the new image has been created using the **docker images** command.
```
$ docker images
```
To access the terminal of a Docker image, you can use the **docker run** command with the **-it** option.
```
$ docker run -it <image-name> bash
```
Replace **<image-name\>** with the name or ID of the Docker image of **CamAge**.

Find the ID of the currently running container for **input** and **output**.
```
$ docker ps -a
```
To start the container again, access its terminal. 
```
$ docker start <container-ID>
$ docker exec -it <container-ID> bash
```

## Input/Output

### Input 
Find the ID of the currently running container, which was just executed using the **docker ps -a** command.
```
$ docker ps -a
```
To write a file to the container, use the **docker cp** command to copy the file from the host to the container.
```
$ docker cp file container_id:WDir/
```
This command will copy the **folder** from the host's current directory to the **CamAge** container with ID **container_id** at the WDir/ directory inside the container.

### Output
Find the ID of the currently running container, which was just executed using the **docker ps -a** command.
```
$ docker ps -a
```
To write a file from the container, use the **docker cp** command to copy the file from the container to the host.
```
$ docker cp container_id:WDir/file-name .
```
This command will copy the **folder** from the **CamAge** container with ID **container_id** under the WDir/ directory inside the container to the host's current directory.

## Running **CamAge**
There are two CamAge Docker images available: one optimized for GPU usage and the other for CPU. Users can select the appropriate image based on their specific requirements.

## 1. segmenter
This command segments yeast cell images.
```
$ segmenter -id raw_input_folder -od segmenter_output_folder
```
Additional arguments:

| Arguments | Description |
| -------- | -------- |
| id | Input the folder path containing the raw images of yeast cells. |
| od | Output folder path for the segmented images |

returns:<br><br>

~ masks: segmented file for the raw images <br>
~ preprocessed_images: preprocessed images <br>
~ compressed_masks.csv: compressed masked .csv for images <br>



## 2. predictor
This command converts the raw yeast images to single-cell yeast images and provides the CamAge predictions.
```
$ predictor -id raw_input_folder -od prediction_output -segmented segmenter_output_folder -SCImages sc_output_folder
```
```
$ predictor -id raw_input_folder -od prediction_output -segmented segmenter_output_folder -SCImages sc_output_folder explainability -image_features -num_features 3 -bio_prediction
```
Additional arguments:

| Arguments | Description |
| -------- | -------- |
| id | Input the folder path containing the raw images of yeast cells. |
| od | Output folder path for the CamAge predictions|
| segmented | Output folder path for the CamAge predictions|
| SCImages | Output folder path for single yeast images|
| explainability | explainability for the predictions|
| num_features | Top features for explainaibiltiy|
| image_features | For bioactivity predictions|
| bio_prediction | bioactivity predictions|


