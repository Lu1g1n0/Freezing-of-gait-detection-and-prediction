# Freezing-of-gait-detection-and-prediction
Explore a comprehensive collection of scripts and datasets dedicated to the detection and prediction of Freezing of Gait (FoG) in Parkinson's Disease. Leveraging wearable sensors and machine learning techniques, this repository provides a robust toolkit for researchers and practitioners in the field.

The script "train_and_evaluate.py" trains and test a multi-head convolutional neural network developed for freezing of gait detection from inertial data.
The model is that reported in the following article:
Luigi Borzì, Luis Sigcha, Daniel Rodríguez-Martín, Gabriella Olmo,
Real-time detection of freezing of gait in Parkinson’s disease using multi-head convolutional neural networks and a single inertial sensor,
Artificial Intelligence in Medicine 135:102459 (2023). https://doi.org/10.1016/j.artmed.2022.102459.  

INPUT: The script takes in input two CSV files, containing train ('train_data.csv') and test ('test_data.csv') data.
These files should contain a table with N samples and 4 columns.
N samples dependent on the amount of data. Data should be sampled at 40 Hz
The 4 columns contains acceleration data (accV,accAP,accML) and the fog label (fogLabel)

OUTPUT: The script outputs the test label and prediction, writing in two CSV files ('test_label.csv' and 'test_prediction.csv')
The test label is extracted from the 'test_data.csv' file.
The prediction is obtained from the trained model, and is in form of probability (from 0 to 1).
Test label and prediction can then be used for computing classification metrics.
When evaluating test performance, remember that test data and label are here segmented with 75% overlap.

IMPORTANT INFORMATION: (1) Make sure your data is sampled or resampled to 40 Hz; (2) Adjust the learning rate, number of epochs, and batch size based on your dataset size. Specifically, as your dataset size increases, reduce learning rate, and increase the number of epochs and batch size. This configuration should work well with 30 minutes to 2 hours of data; (3) While the window size should be fixed at 2 seconds, you can adjust the overlap as you prefer. As the overlap increases, more windows are generated. This produces more training data, which is beneficial. However, too large overlap may lead to over-fitting. Thus, find the best compromise; (4) This model has shown to provide good performance on acceleration data recorded from the waist/lower back. Evaluations on data recorded from other body locations have not been performed yet.
