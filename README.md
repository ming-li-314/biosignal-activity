# Biosignal-Activity
Human activity recognition using various biosignals 

This is the final course project for the data science boot camp (Spring 2024 cohort) from Erdos Institute (https://www.erdosinstitute.org/).
The goal is to use machine learning models to recognize human activities from a collection of various time series biosignals (like ECG, EDA, ACC, etc).


### The Data
The raw data comes from (https://physionet.org/content/scientisst-move-biosignals/1.0.1/) : 

Areias Saraiva, J., Abreu, M., Carmo, A. S., Plácido da Silva, H., & Fred, A. (2024). ScientISST MOVE: Annotated Wearable Multimodal Biosignals recorded during Everyday Life Activities in Naturalistic Environments (version 1.0.1). PhysioNet. https://doi.org/10.13026/hyxq-r919.

There are 17 participants. Each participant performs up to 8 activities. While each participant performs the activities, up to 14 biosignals are recorded. 

The 8 activities are:
* Baseline, Lift, Greetings, Gesticulate, Jumps, Walk_before, Run, Walk_after.

The 14 biosignals are:
* ECG:dry, ECG:gel, EDA:dry, EDA:gel, EMG:Left Bicep, TEMP:temp, PPG:Left index finger, PPG:Left Wrist, ACC_e4:z, ACC_e4:x, ACC_e4:y, ACC_chest:x, ACC_chest:y, ACC_chest:z

The problem can be viewed as time series classification problem, which has been extensively studied in the literature (see https://www.aeon-toolkit.org/en/stable/index.html). There are many different methods to do time series classification. For our problem of human activity recognition from biosignal time series, we focus on the

* Feature Based approach,
* Convolution-Neural-Network Based approach. 
