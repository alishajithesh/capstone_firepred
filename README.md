# capstone_firepred
MAD2502 capstone project

## Project Overview 
This project consists of three main parts:
1. Forest Fire Exploratory Data Analysis (californiafire_analysis notebook)
2. Predicting Fire Radiative Power Given Meteorological Data (predict_fire_radiative_power notebook)
3. Forest Fire Smoke Detection Model (forest_fire_localizer notebook)

Together these three parts are combined into one main interactive program for the user to experiment with the data and simulate the models as they would be used in the real-world (ModelVisualizer.ipynb). By first using the exploratory
data analysis and predicted radiative power, users would know the optimal location to set up the detection model created in the forest_fire_localizer notebook.

## How To Run the Project
California Fire Analysis Notebook (californiafire.ipynb):
1. Before running any of the cells, make sure that you have the following imports and installations: geopandas, folium, numpy, pandas, matplotlib, and shapely.
2. Additionally, make sure that california_data folder is in the same current directory as this notebook. If you unzipped the folder and did not touch any of the files, everything should already be configured for
you.
3. Run each of the cells and obseve the output. It is important to note that if you are trying to run cells 4 or 6, they might not work on your local computer. For example, on some computers, when you try to run
cell 4 it will say that the format "ISO" is the problem. Additionally, cell 6 might prompt you with an error regarding aspect. If these errors occur on your computer, simply move on and run the rest of the cells.
If you want more information about those two cells, you can refer to the presentation and report.
4. When you get to the last cell in the notebook, it will prompt you with a county in California. It is important to note that this is case sensitive and therefore proper capitaliztion should be used. An easy example
that the user should try inputting is Monterey (there is video footage detection of a fire in this county in the Model Visualizer notebook).

Predicting Fire Radiative Power (predict_fire_radiative_power.ipynb):
1. This notebook is not meant to be run and is supposed to be view only. The reason for this is because this notebook trains multiple models and tries to find the best one. However, this notebook utilizes the
original dataset that was too large to be included in the zip folder. As a result, you cannot train the models on the truncated version of the dataset (radiative/wildfiredb_2016.subset).
2. If you do want to see a model predicting radiative power, look at the Model Visualizer notebook. The visualizer utilizes the best model from this notebook, Random Forest model, and applies it with the truncated
dataset to allow users to experiment with the predictions.

Forest Fire Smoke Detection Model (forest_fire_localizer.ipynb):
1. This notebook is also not meant to be run and is supposed to be more of a view only. The reason for this is because this notebook trains two very large models, each with millions of parameters. As a result, the
training process can take multiple hours and be a tedious process. Additionally, by training the model again there is no guarantee that it will be exactly the same as when we trained the model.
2. However, if you do want to at least view the dataset it is using and understand how bounding boxes are displayed on images, you can run all of the cells up until the "Creating the Model" section. If you plan
on doing this, make sure that the day_time_wildfire_v2 dataset is in the same current directory as this notebook.
3. Additionally, before running any cells make sure that you have the following imports and installations: numpy, pandas, tensorflow (upgraded), matplotlib, and PIL.

Model Visualier (ModelVisualizer.ipynb):
1. This is the main interactive program that allows users to experiment with all of the data analysis and models. Before starting, make sure that the california_data folder, day_time_wildfire_v2 folder, inputVideo
folder, Models folder, OutputVideo folder, radiative folder, SmokeDataset csv, and all of the notebooks are in the same current directory. If you did not move around the files after unzipping, then you should
be fine.
2. Additionally, before running any cells make sure that you have the following imports and installations: os, pandas, numpy, open-cv (for cv2), tensorflow (might need to upgrade it if it does not work), matplotlib, PIL, sklearn, and seaborn.
3. Now run all the cells starting from the imports cell. When you eventually get to the interactive menu, you will be prompted with three different options.
4. If you choose option 1, then you will be prompted with a county in California. It is important to note that this is case sensitive and therefore proper capitalization should be followed. A good example to try
is Monterey county (video 1 has footage from a fire near Monterey county). The visualizer will then return information regarding incidents in that location.
5. If you choose option 2, then you will have 2 more options (disregarding the quit option). The first option will give you some information on the radiative power model and what parameters it takes in. If
you choose option 2, then you will be prompted with a value for each input parameter that the model requires. It is important to note that users should be typing in floating point value (not strings). As a result,
the model will predict the radiative power of a fire with that meterological data.
6. If you choose option 3 (smoke detection model), then you will have 5 more options (disregarding the quit option). The first option will give you some information on how the model was created and designed. The
second option prompts the user for one of the image file names. To find a list of these names, the user can go to the day_time_wildfire_v2 folder and then the images folder. But as an example, the user can try
inputting 'ckagz7s5solbc0841r1aklq1g'. The output will be a predicted bounding box on the image (along with the labeled bounding box). The third option will show the user 9 prediction of 9 random images taken from
the entire dataset. This allows the user to see how good the bounding box predictions really are. The fourth option will prompt the user with two values: a starting point and ending point (within the range of the
dataset). It is important that the user inputs values that are integers, in range, and the first value should be smaller than the second. The visualizer will then return the IoU accuracy of the model on those
specific images. Finally, the fifth option will prompt the user for either video 1 or video 2 and then proceed to apply the model to the video footage you chose. It will apply a prediction to each frame and write
it to an output video in the OutputVideo. Users can see both the input videos and output videos in the InputVideo and OutputVideo section respectively. It is important that the user does not have the output video
open while the model is predicting on it or it will cause an error. 
