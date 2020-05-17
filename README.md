## ReadMe: LSTM Neural Networks and HAR Models for Realized Volatility - An Application to Financial Volatility Forecasting

The following document aims to provide an overview of the whole code base used throughout the thesis. Generally speaking, this repository contains code for all the data loading, preprocessing, estimation, training, and prediction. For reporting the results an individual repository was set up containing a dashboard with all the relevant information. The dashboard repository can be found here: https://github.com/nickzumbuehl/dashboard_deployment and the dashboard runs under the url: http://nick-vola.herokuapp.com.

This document outlines the following points:
1. Setting up the Code Base
   - Environment
   - Configuration
2. Pipeline Overview
3. Pipeline Walk-Through
   - Feature Engineering
   - AutoRegression_Model.py & run_AutoRegression_Model.py
   - HAR_Model.py & run_HAR_model.py
   - LSTM.py, run_LSTM.py
     - GeneticAlgorithm.py
     - run_GeneticAlgorithm.py
   - dashboard_data_prep.py
   

## 1. Setting up the Code Base

#### Environment
The ```requirements.txt``` contains information on all the relevant packages and versions used in the code base. In order to set up the environment, the please follow the subsequent process:
1. cd to the directory where your ```requirements.txt```is located
2. activate your virtual environment
3. run: ``` pip install -r requirements.txt``` in your shell. Alternatively, when working with conda, run: ```conda install --file requirements.txt```.

#### Configuration
The ```config.py``` file sets up the folder structure. When cloning the repository from GitHub, all the relevant folders are already in place. Nevertheless, the ```config.py``` defines the path architecture and makes sure it runs on each individual local machine.

## 2. Pipeline Overview
The pipeline of the overall project is illustrated in the following figure. It can be splited into input-, process- and output files. The blue-colored boxes describe the proces or the content which is relevant for the corresponding step in the pipeline. The grey-colored boxes are indicating the name of the corresponding file in the repository.
Naturally, the input files are the files that are later processed by the python process files. The input files consist of ```.csv``` and ```.h5``` files, where the input data is stored in .csv-format and the models are stored in .h5-files. 
The output files are often times the input files for another python file in the pipeline. Hence, an output file can be an input file later in the process.

![](pipeline_advance.png)

## 3. Pipeline Walk-Through
#### Feature-Engineering
The file ```feature_engineering.py``` processes high-frequency data to compute the relevant features (realized volatility, positive- & negative realized semi-variance). As a input it takes high-frequency data in a ```.csv```-format retrieved from the WRDS data base. High-frequency data tend to be extremely large in storage (for the period considered in the application at hand, we face approximately 50GB of high-frequency data). Therefore, each year of high-frequency data was processed separately and later concatenated to obtain the complete time series of volatility measures. The ```zip```-files for the raw high-frequency data pulled from WRDS can be found here: https://drive.google.com/drive/folders/1VVNbAx8bbY2Km-NGu5cBaK8lHFdmjRD1?usp=sharing
The output generated by ```feature_engineering.py``` is a ```.csv```-file containing the time series of the volatility measures.
In the data-folder in the repository, there are two ```csv```-file. The first one is the concatenated file ```RealizedMeasures03_10.csv``` with the realized volatility time series that contain the data used for training and valiadtion and ranges from 2003 to 2010. The second one (```DataFeatures.csv```)contains the realized volatility time series for the testing set.



https://help.github.com/en/github/writing-on-github/basic-writing-and-formatting-syntax
