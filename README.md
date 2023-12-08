# Freezing of Gait Detection and Prediction Toolkit

Explore a comprehensive collection of scripts and datasets dedicated to the detection and prediction of Freezing of Gait (FoG) in Parkinson's Disease. Leveraging wearable sensors and machine learning techniques, this repository provides a robust toolkit for researchers and practitioners in the field.

## Train and Evaluate Script

The script "train_and_evaluate.py" trains and tests a multi-head convolutional neural network developed for freezing of gait detection from inertial data. The model is detailed in the following article:

Luigi Borzì, Luis Sigcha, Daniel Rodríguez-Martín, Gabriella Olmo, Real-time detection of freezing of gait in Parkinson’s disease using multi-head convolutional neural networks and a single inertial sensor, Artificial Intelligence in Medicine 135:102459 (2023). [DOI: 10.1016/j.artmed.2022.102459](https://doi.org/10.1016/j.artmed.2022.102459).

### Input

The script takes two CSV files as input:

- `train_data.csv` for training data
- `test_data.csv` for testing data

These files should contain a table with N samples and 4 columns. The 4 columns contain acceleration data (`accX`, `accY`, `accZ`) and the Freezing of Gait label (`fogLabel`). N samples depend on the amount of data, and data should be sampled at 40 Hz.

#### Example Data Format

Here's an example of the expected format for the CSV files:

'''csv
accX,accY,accZ,fogLabel
-0.123,0.456,0.789,0
-0.987,0.654,0.321,1
0.111,-0.222,0.333,0'''

### Output

The script outputs the test label and prediction, writing to two CSV files:

- `test_label.csv`
- `test_prediction.csv`

The test label is extracted from the `test_data.csv` file. The prediction is obtained from the trained model and is in the form of probability (from 0 to 1). Test label and prediction can then be used for computing classification metrics. When evaluating test performance, remember that test data and label are here segmented with a 75% overlap.

### Important Information

1. Make sure your data is sampled or resampled to 40 Hz.
2. Adjust the learning rate, number of epochs, and batch size based on your dataset size. Specifically, as your dataset size increases, reduce the learning rate and increase the number of epochs and batch size. This configuration should work well with 30 minutes to 2 hours of data.
3. While the window size should be fixed at 2 seconds, you can adjust the overlap as you prefer. As the overlap increases, more windows are generated, producing more training data, which is beneficial. However, too large overlap may lead to overfitting. Thus, find the best compromise.
4. This model has shown good performance on acceleration data recorded from the waist/lower back. Evaluations on data recorded from other body locations have not been performed yet.

## Citation

If you use this toolkit in your research, please cite the following paper.

Luigi Borzì, Luis Sigcha, Daniel Rodríguez-Martín, Gabriella Olmo, Real-time detection of freezing of gait in Parkinson’s disease using multi-head convolutional neural networks and a single inertial sensor, Artificial Intelligence in Medicine 135:102459 (2023). [DOI: 10.1016/j.artmed.2022.102459](https://doi.org/10.1016/j.artmed.2022.102459).

## Contact

For any questions or inquiries, feel free to contact:

- Luigi Borzì: [luigi.borzi@email.com](mailto:luigi.borzi@email.com)
