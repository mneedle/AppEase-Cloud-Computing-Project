# AppEase

Cloud Computing Project Part 2: AppEase

1. 'simulate_data_and_labels.py'
This script creates simulated AppEase data in 2 JSON files ('simulated_health_data.json' for simulated user health data and 'random_labels.json' for simulated anxiety labels). This script should be run by calling "python3 create_data_and_labels.py [rows] [users]" where [rows] are the desired instances of collected data and [users] are the desired number of simulated users the data are collected from. The 'Sample Data' Folder contains an example of simulated data and labels for 100 instances of data for 5 distinct users. 
NOTE: At least 63 rows of data are required for Azure Machine Learning analytics (assuming a 0.8/0.2 train/test split).

2. 'AppEaseIoT.py'
This script uploads a file as an Azure Storage Blob to a Container through an IoT Hub Device. This script requires an Azure IoT Hub that has been associated with an Azure Storage Account Container and contains at least one IoT Device. This script should be run by calling "python3 data_simulation_and_upload_to_azure.py [device_conn_str] [file]" where [device_conn_str] is the connection string of an IoT device created on an Azure IoT Hub and [file] is the name of the file in the local directory to be uploaded (i.e., 'simulated_health_data.json').

3. 'P2P' Folder
This folder contains the necessary files to create a simple Peer-to-Peer file sharing application using Berry’s PeerBase P2P system. Two separate nodes were created by running “python filergui.py 9001 10 localhost:9000” in one Terminal window and “python filergui.py 9002 10 localhost:9000” in another. The two nodes were then connected by ‘Rebuilding’ “localhost:9001” in the GUI for the 9002 node. The ‘simulated_health_data.json’ file was then ‘Added’ to the 9001 node and then ‘Fetched’ by the 9002 node.

4. 'AppEaseML.ipynb'
This notebook uses automated machine learning in Azure Machine Learning to create a regression model to predict the above-created simulated labels (i.e., 'random_labels.json') from given data (i.e., 'simulated_health_data.json') and then outputs the root mean squared error, mean absolute percent error, and accuracy of the best performing model. This notebook requires an Azure subscription. 
NOTE: It is recommended to run this script on a Data Science Virtual Machine to ensure the necessary packages are installed.
