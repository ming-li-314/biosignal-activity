# Biosignal-Activity
Human activity recognition from various biosignals using machine learning models.

This is the final course project for the data science boot camp (Spring 2024 cohort) from Erdos Institute (https://www.erdosinstitute.org/).
The goal is to use machine learning models to recognize human activities from a collection of various time series biosignals (like ECG, EDA, ACC, etc).


## The Data
The raw data comes from (https://physionet.org/content/scientisst-move-biosignals/1.0.1/) : 

Areias Saraiva, J., Abreu, M., Carmo, A. S., Plácido da Silva, H., & Fred, A. (2024). ScientISST MOVE: Annotated Wearable Multimodal Biosignals recorded during Everyday Life Activities in Naturalistic Environments (version 1.0.1). PhysioNet. https://doi.org/10.13026/hyxq-r919.

There are 17 participants. Each participant performs up to 8 activities. While each participant performs the activities, up to 14 biosignals are recorded. 

The 8 activities are:
* Baseline, Lift, Greetings, Gesticulate, Jumps, Walk_before, Run, Walk_after.

The 14 biosignals are:
* ECG:dry, ECG:gel, EDA:dry, EDA:gel, EMG:Left Bicep, TEMP:temp, PPG:Left index finger, PPG:Left Wrist, ACC_e4:z, ACC_e4:x, ACC_e4:y, ACC_chest:x, ACC_chest:y, ACC_chest:z

The problem can be viewed as time series classification problem, which has been extensively studied in the literature (see https://www.aeon-toolkit.org/en/stable/index.html). There are many different methods to do time series classification. For our problem of human activity recognition from biosignal time series, we focus on the

* Feature Based approach,
* Convolutional Neural Network Based approach. 

The full time series is divided into segments of predefined length (10 seconds for example). In the feature based approach, various features are extracted for each segment of the time series. These features could be describing the statistical distribution of the time series, the time domain features or features from the Fourier space. We have used the Neurokit2 package (https://github.com/neuropsychology/NeuroKit) and the Biobss package (https://github.com/obss/BIOBSS) to analyze the data and extract features. In the convolutional neural network based approach, all the time series segments are fed into the convolutional neural network. The CNN automatically learns from the segments of the time series. This is a one-dimensional analog to the two-dimensional image recognition problem. 

![activity_counts](https://github.com/ming-li-314/biosignal-activity/assets/132095576/32de3b83-af43-4f08-a450-0d2fc4833657)

The data is high imbalanced among the 8 classes. For the "jump" activity, there are only 12 data points while for the "run" activity, there are approximately 2200 data points.
This falls into the imbalanced multi-class classification problem, which is one of the major challenges of this project. 

## Machine Learning Models
We have used three machine learning algorithms to model this multi-class classification problem:
* RandomForestClassifier
* XGBoostClassifier
* RocketClassifier

The confusion matrix on the test set are:
For the RandomForestClassifier,

<img width="639" alt="Screenshot 2024-04-25 at 10 10 55 PM" src="https://github.com/ming-li-314/biosignal-activity/assets/132095576/22b2149e-8ad1-4308-b752-17f2af4e75d7">





For the XGBoostClassifier, 

<img width="648" alt="Screenshot 2024-04-25 at 10 05 33 PM" src="https://github.com/ming-li-314/biosignal-activity/assets/132095576/7b353c99-e78a-493a-a70d-9bb51716c0da">


The most important features come from the ACC biosignal.

<img width="775" alt="Screenshot 2024-04-25 at 10 17 18 PM" src="https://github.com/ming-li-314/biosignal-activity/assets/132095576/e6c00f66-55e7-47e7-9715-9818ac3b7417">



For the RocketClassifier, a convolutional neural network based algorithm from the "aeon" library,

<img width="657" alt="Screenshot 2024-04-25 at 4 17 13 PM" src="https://github.com/ming-li-314/biosignal-activity/assets/132095576/003ead06-a6e8-4426-8596-0562307aa680">



