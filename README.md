# Multi-Machine Disruption Prediction Challenge for Fusion Energy
Submission by Isaac Oluwafemi Ogunniyi (zindi username: isaacOluwafemiOg)

This solution consist of four sets of files (all part of the official competition data):

- Owing to the size of the files, the data is to be read from the google drive linked below: 
    - https://drive.google.com/drive/folders/1m6o2mKnRBaky11jZ7HKtbh1zh6RCBVOk?usp=drive_link

- The sets of files are in folders named: 
    - 'J-TEXT processed_data_1k_5k_final' which contains shot files for the J-TEXT tokamak type.
    - 'JDDB_repo_2A_5k' which contains HL-2A tokamak shot files
    - 'CMod_train' which contain CMod tokamak shot files that will be used to validate the performance of the model
	locally.
    - 'CMod_evaluate_20_10_2023' contains CMod-type tokamak shot files on which model performance will be finally tested
   
- A Jupyter notebook named 'fusion_finale.ipynb' containing the code for
handling data, training model and predicting disruption in a tokamak.

## The environment
The Jupyter notebook runs in a python environment. For a Google Colab CPU runtime type,
it lasts under 6 minutes.
No paid subscriptions or resources were used.

## The Jupyter Notebook
* This notebook takes input of all data files from the folders mentioned previously and outputs
'Submission.csv'.

* To run the notebook the 'data_path' variable must contain the path to the directory
containing all the folders mentioned previously above.

* The notebook contains python code and the whole code runs on Google colab lasting
under 6 minutes.

* The General Overview of the Notebook is as follows:
 1. Importing Relevant libraries
pandas (1.5.3), numpy (1.23.5), scikit-learn (1.2.2), scipy(1.11.3), lightgbm(4.1.0), h5py(3.9.0), google(2.0.3)

 2. Reading Data

 3. Engineering Features
The features fed into the model are 21 and fall into 3 categories:
    - Features extracted as statistical measures of the entries of the line integral density(center chord) signal.
	Measures such as maximum, mean, standard deviation, interquartile range, range, among others
	
    - Features extracted as statistical measures of the change in value between successive entries of the line integral density(center chord) signal
    	Measures such as variance, median, minimum, among others

    - Other features such as an encoding of the type of tokamak and validity flag of the line integral density(center chord) signal for the shot file
 
 4. Developing Pipelines and training models
     - Pipeline involved scaling (standardScaler) and then fitting an LGBMClassifier model.
     - The model's hyperparameters were tuned using the RandomizedsearchCV
 
 5. Predicting and preparing submission
    - Predictions are made on the dataframe created from the shot files in 'CMod_evaluate_20_10_2023'
    
    - The final predictions are exported to 'Submission.csv' in the same directory as
the jupyter notebook.
