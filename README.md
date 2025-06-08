# Human-Activity-Classification-using-Wavelet-Analysis-and-Deep-Learning
This project classifies human activities (sitting, walking, running) from mobile accelerometer data by transforming signals into scalograms using Wavelet Analysis and classifying them with fine-tuned GoogLeNet and custom CNN architectures, achieving high accuracy.




## Project Overview

This project focuses on developing a robust system for classifying human activities (Sitting, Walking, Running) using accelerometer data acquired from mobile phones. The methodology involves transforming time-series sensor signals into visual representations (scalograms) using Wavelet Analysis, followed by classification using a Convolutional Neural Network (CNN). The system demonstrates high accuracy in distinguishing between different activities.

## Key Features & Functionality

* **Accelerometer Data Acquisition & Preprocessing:** Utilizes raw accelerometer data (X, Y, Z axes) from mobile phones, loading it into MATLAB timetables for efficient handling. Includes optional steps for absolute acceleration calculation and Z-score normalization to enhance data quality.
* **Wavelet Analysis (Scalogram Generation):** Employs Continuous Wavelet Transform (CWT) with the 'amor' (Morlet) wavelet to convert time-series accelerometer signals into scalograms. These scalograms serve as rich time-frequency representations, capturing discriminative features for different activities.
* **Data Augmentation & Segmentation:** Implements a strategy to break down raw signals into overlapping segments (e.g., 1000 samples with 500 stride) to increase the dataset size and variability for robust CNN training.
* **Image Database Creation:** Converts generated scalograms into RGB image files (e.g., 227x227 pixels) and organizes them into a folder structure, enabling their use with MATLAB's `imageDatastore` for CNN input.
* **Deep Learning Classification (GoogLeNet & Custom CNN):**
    * **GoogLeNet Fine-tuning:** Leverages a pre-trained `googlenet` architecture, adapting its final layers (dropout, fully connected, classification) for 3-class human activity classification.
    * **Custom CNN Architecture:** Designed and implemented a custom CNN from scratch, including convolutional layers, batch normalization, ReLU activations, max-pooling, and a residual block for enhanced feature learning and performance.
* **Performance Evaluation:** Assesses the model's accuracy on unseen test data and visualizes performance using a confusion matrix. Includes a mechanism to test the trained CNN on new, individual signal samples.

## Technical Details & Methodology

* **Programming Environment:** MATLAB
* **Core Libraries/Toolboxes:**
    * **Wavelet Toolbox:** For Continuous Wavelet Transform (CWT) and scalogram generation.
    * **Deep Learning Toolbox:** For building, training, and fine-tuning Convolutional Neural Networks (CNNs), including `googlenet` and custom architectures.
    * `ImageDatastore` for efficient image data management.
* **Data Flow:**
    1.  Load `Sitting`, `Walking`, `Running` accelerometer data from `.mat` files.
    2.  Combine datasets and visualize raw signals.
    3.  Generate CWT scalograms for segments of the X, Y, Z accelerometer data.
    4.  Save scalograms as RGB images to categorized subfolders (`CWTdata/sitting`, `CWTdata/walking`, `CWTdata/running`).
    5.  Load image data into `imageDatastore` and split into training and testing sets.
    6.  **CNN Training (Two Approaches):**
        * **GoogLeNet:** Load `googlenet`, modify output layers, and train using `trainingOptions` (e.g., 'sgdm' optimizer, 'minibatchsize', 'MaxEpochs', 'InitialLearnRate').
        * **Custom CNN:** Define a layered architecture with residual connections, set `trainingOptions` (e.g., 'sgdm', 'MiniBatchSize', 'MaxEpochs', 'InitialLearnRate', 'LearnRateSchedule', 'L2Regularization'), and train the network.
    7.  Evaluate classification accuracy and plot confusion matrices.
    8.  Test the trained model with new, unseen single data points.

## Key Results

* [cite_start]**High Classification Accuracy:** Achieved a classification accuracy of **100%** on the validation set using the fine-tuned GoogLeNet model.  The custom CNN also achieved high validation accuracy of **97.14%**.
* [cite_start]**Effective Feature Extraction:** Wavelet Analysis successfully extracted discriminative features from raw sensor signals, enabling robust classification. 
* **Real-time Performance:** Demonstrated the ability to classify new signals, such as a "sitting" test dataset, with high probability (e.g., 99.95%).

## Getting Started (for review/reproduction)

* **Software Requirements:** MATLAB with Wavelet Toolbox and Deep Learning Toolbox.
* **Data:** Raw accelerometer data files (`Sitting data.mat`, `Walking data.mat`, `Running data.mat`, `sitting testset.mat`) as timetables.
* **Execution:** The project is structured as a MATLAB Live Script, with sequential execution of code sections for data loading, preprocessing, scalogram generation, CNN design, training, and evaluation.

## Author

Puneet Singh Arora
[LinkedIn Profile](https://www.linkedin.com/in/puneet-singh11
