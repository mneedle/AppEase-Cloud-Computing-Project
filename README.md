# AppEase

Cloud Computing Project Part 2: AppEase

1. 'simulate_data_and_labels.py'
This script creates simulated AppEase data in 2 JSON files ('simulated_health_data.json' for simulated user health data and 'random_labels.json' for simulated anxiety attack labels). This script should be run by calling "python3 create_data_and_labels.py [rows] [users]" where [rows] are the desired instances of collected data and [users] are the desired number of simulated users the data are collected from. The 'Sample Data' Folder contains an example of simulated data and labels for 100 instances of data for 5 distinct users. 
NOTE: At least 63 rows of data are required for Azure Machine Learning analytics (assuming a 0.8/0.2 train/test split).

2. (RETIRED) 'AppEaseIoT.py'
This script uploads a file as an Azure Storage Blob to a Container through an IoT Hub Device. This script requires an Azure IoT Hub that has been associated with a publicly-accessible Azure Storage Account Container and contains at least one IoT Device. This script should be run by calling "python3 AppEaseIoT.py [device_conn_str] [file]" where [device_conn_str] is the connection string of the IoT device created in the Azure IoT Hub and [file] is the name of the file in the local directory to be uploaded (i.e., 'simulated_health_data.json').

3. 'AppEaseML.ipynb'
This notebook uses automated machine learning in Azure Machine Learning to create a classification model for predicting the above-created simulated labels (i.e., 'random_labels.json') from given data (i.e., 'simulated_health_data.json') and then outputs the best model ('best_model.pkl') and the data and labels used to train the best model (i.e., 'train_data.csv' and 'train_labels.csv'). The 'ML Analysis for Best Model' Folder contains examples of these output files. This notebook requires an Azure subscription. 
NOTE: It is recommended to run this script on an Azure Data Science Virtual Machine with a Python 3 kernel to ensure the necessary packages are installed.

4. 'P2P' Folder
This folder contains the necessary files to create a Peer-to-Peer networking application for uploading and analyzing AppEase data against the previously-found best model. An IoT node uploads the data as a publicly-accessible Azure Storage Blob and then send the URL for the Blob to an ML client node, which loads the data and sends back a list of users which it predicts to be having an anxiety attack. A server node is first created by running "python3 server.py" before connecting an ML client node (creating by running "python3 client_ml.py") and an IoT client node (created by running "python3 client_iot.py [device_conn_str] [file]" where [device_conn_str] is the connection string of the IoT device created in the Azure IoT Hub and [file] is the name of the file in the local directory to be uploaded). These Python scripts should also be run in a directory that contains the files outputed by the 'AppEaseML.ipynb' notebook (i.e., 'best_model.pkl', 'train_data.csv', and 'train_labels.csv'). 
