# Road Segmentation /AIcrowd challenge
ml-project-2-the-happy-whales2 created by GitHub Classroom

The goal of the project is to segment roads in  satellite/aerial images acquired from GoogleMaps. 
The training dataset consists in 100 RGB images of size 400x400x3 and their corresponding groundtruth in black and white . 
To detect roads, three classifiers are created in this project and their efficiency compared. 
In this project, patches of size 16x16 are classified: if a road is detected in the patch the classifier ouputs 1 and if not it ouputs 0. 
An example of an aerial image used for training and its mask is shown below:

<p float="left">
<img src="ML_project/training/images/satImage_001.png" alt="classdiagram"  width="200" title="hover text">
<img src="ML_project/training/groundtruth/satImage_001.png"  alt="classdiagram" width="200" >
</p>
The set of training and test images is available on this page: [EPFL ML Road Segmentation challenge](https://www.aicrowd.com/challenges/epfl-ml-road-segmentation). 

## Prerequisites

This project has been realized using:
* python3.9
* numpy
* segmentation_models
* patchify
* matplotlib
* keras
* tensorfow= 2.7.0

## Structure of files

The folder **ML project** has to be download and run on Google Collab to use the GPU. It contains several sub-folders:

ML project

 |-- **data**  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **training**: original training dataset  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **images** (100 satellite images) 
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |--satImage_001.png  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- ...  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **groundtruth** (100 groundtruth images)
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |--satImage_001.png  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- ...  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **augmented_training**: created augmented dataset for the training
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **images** (1000 satellite images)
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |--satImage_001.png  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- ...  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **groundtruth**  (1000 groundtruth images)
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |--satImage_001.png  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- ...  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **test_set**: original testing dataset   
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- **images** (50 satellite images)  
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |--test_1.png    
 |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  |&nbsp;  &nbsp;  &nbsp;  &nbsp;  |-- ...    
 |-- **src**: script files
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- `train.py`: train the different models implemented, first lines have to be modified accoriding to the desired model 
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- `run.py`: create predictions for the testing dataset and create and save the submission file  
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- `DataPreprocessing.py`: realize all the preprocessing on the images before training or testing
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- `DataAugmentation.py`: create the augmented training dataset
 |-- **saved_models**  
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- `unet_aug4rot_Gblur5_Flips.hdf5`: final model for the   
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |--  ...   
 |-- **prediction_unet**: predicted masks of the best model (Multi-Resnet trained on augmented dataset)
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- pred_1_unet.png    
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |--  ...   
 |-- **submissions**: submission files for AIcrowd  
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |-- `submission_unet_augbcp_f32_p128.csv`
 |&nbsp;  &nbsp; &nbsp;  &nbsp;  |--  ...    
  

## Contributors
* Charlotte Sertic
* Estelle Chabanel
* Servane Lunven
