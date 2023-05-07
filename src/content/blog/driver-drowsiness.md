---
author: Helios
pubDatetime: 2023-05-07T15:57:52.737Z
title: Transistor Transistor Logic
postSlug: ttl-logic
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - CASE-STUDY
description: nothing and everything 
---

## Introduction

You’ve probably driven while tired at some point in your life. It’s not something we like to recognize, but it’s a real issue with major implications that must be handled. Drowsy driving causes one in every four car accidents, and one in every 25 adult drivers admits to falling asleep behind the wheel in the last 30 days. The frightening aspect is that drowsy driving is more than simply falling asleep while driving. Drowsy driving may be as simple as a short moment of sleepiness when the motorist is not paying full attention to the road. Drowsy driving causes around 71,000 injuries, 1,500 fatalities, and $12.5 billion in monetary damages each year. Because of the importance of this issue, we believe it is critical to develop a solution for drowsiness detection, particularly in the early stages, to prevent accidents.

Moreover, we feel that tiredness might have a detrimental influence on individuals in the workplace and in the classroom. Despite the fact that sleep deprivation and college go hand in hand, drowsiness in the workplace, particularly when using heavy machinery, can lead to serious injuries similar to those that result from drowsy driving.

Our approach to this issue is to create a detection system that recognizes key characteristics of sleepiness and sends a warning when someone becomes sleepy before it’s too late.

## Data Source and Preprocessing

For our training and testing data, we used the Real-Life Drowsiness Dataset that a research team at the University of Texas at Arlington created specifically for detecting multi-stage drowsiness. The ultimate goal is for our system to detect not only extreme and visible cases of drowsiness, but also softer signals of drowsiness. The collection contains around 30 hours of footage from 60 different people. We were able to extract face landmarks from 44 films of 22 persons using the dataset. This enabled us to collect enough data for the alert and sleepy states.

We used OpenCV to extract 1 frame per second till the finish of each film.

To detect drowsiness, the baseline architecture is described first, and then two compressed models are introduced. The suggested models comprise three kinds, including the baseline 4-stream sleepiness detection model, the 2-stream drowsiness detection model, and its compressed variant that applies the teacher-student approach with the least accuracy decrease.

Our suggested system architecture for sleepiness detection comprises two primary phases. The sleepiness detection model comes next, after joint face identification and alignment. Multi-Task Cascaded Convolutional Networks (MTCNN) are used for face identification and alignment because of their speed and precision in face detection. MTCNN’s cascaded architecture enables rapid joint face identification and alignment. The output of the first phase consists of facial boundary coordinates and five landmark points, including the left and right eye, nose, left lip-end, and right lip-end. In the second stage, the Driver Drowsiness Detection Network (DDDN) is employed to identify driver sleepiness. The result of the first step is the input for DDDN.

## System Architecture

![image](https://user-images.githubusercontent.com/103866475/236674588-c0baa86b-8cdc-4c5c-aeda-882e4c32265a.png)


### 1. Baseline model

The suggested network architecture includes a baseline model called baseline-4, which is shown as a 4-stream deep neural network in Figure 2. This model takes as inputs the detection network’s left eye, right eye, mouth, and face. When images are entered, they are resized to 224x224 pixels. The baseline-4 model has five convolutional layers for each input stream. The network structure of each stream is similar to Alex Net, with filter sizes of 11x11, 5x5, 7x7, and 3x3. Figure 1 shows the number of kernels for each layer. Models with Alex Net-like architectures are preferable for embedded board implementation because to their improved execution performance over Google Net and ResNet. Since the recovered attributes from the eyes are assumed to be equivalent, the convolution layers of the eyes share the same weight, as informed by the gaze-tracking architecture. The size of each fully connected (FC) layer that follows each stream of convolutional layers is specified further. Every FC layer is connected to the last two FC levels. The proposed model predicts three output classes: normal, yawning, and sleepy. A normal driving state is one in which the driver is alert, attentive, and not weary. The driver’s yawning signals that he or she will likely get weary while driving shortly. Drowsiness indicates that the driver is very tired and should immediately cease driving to avoid potentially harmful situations.

### 2. ResNET

ResNet (Residual Network) is a deep learning architecture that has shown to be very effective in various computer vision tasks, including object detection and recognition. To use ResNet for drowsiness detection, we can adapt the architecture to fit the specific requirements of the task. One way to do this is to use the ResNet architecture as a feature extractor, where the pre-trained ResNet model is used to extract high-level features from input images. The extracted features are then fed into a classifier to classify the level of drowsiness. The classifier can be a simple fully connected neural network, or a more advanced classifier such as a support vector machine (SVM) or random forest. Another way to use ResNet for drowsiness detection is to fine-tune the pre-trained model on a large dataset of drowsy and non-drowsy images. This involves retraining the last few layers of the ResNet model to adapt to the specific task of drowsiness detection. The fine-tuned model can then be used as a classifier to predict the level of drowsiness. Overall, ResNet can be a powerful tool for drowsiness detection as it is able to extract high-level features from input images and learn complex patterns that are important for the task. However, the effectiveness of the model will depend on the size and quality of the training dataset, as well as the specific implementation of the architecture.

### 3. Model architecture

The architecture described corresponds to a convolutional neural network (CNN) that is typically used for image classification tasks.

There are two main parts to CNN architecture.

- A convolution tool that separates and identifies the various features of the image for analysis in a process called Feature Extraction.
- The network of feature extraction consists of many pairs of convolutional or pooling layers.
- A fully connected layer that utilizes the output from the convolution process and predicts the class of the image based on the features extracted in previous stages.
- This CNN model of feature extraction aims to reduce the number of features present in a dataset. It creates new features which summarises the existing features contained in an original set of features. There are many CNN layers as shown in the CNN architecture diagram.

## Architecture of a CNN model

![image](https://user-images.githubusercontent.com/103866475/236674623-309d102c-767d-4d47-b492-8428c135b6f6.png)


### 1. Convolutional Layer

This layer is the first layer that is used to extract the various features from the input images. In this layer, the mathematical operation of convolution is performed between the input image and a filter of a particular size MxM. By sliding the filter over the input image, the dot product is taken between the filter and the parts of the input image with respect to the size of the filter (MxM).

The output is termed as the Feature map which gives us information about the image such as the corners and edges. Later, this feature map is fed to other layers to learn several other features of the input image.

The convolution layer in CNN passes the result to the next layer once applying the convolution operation in the input. Convolutional layers in CNN benefit a lot as they ensure the spatial relationship between the pixels is intact.

### 2. Pooling Layer

In most cases, a Convolutional Layer is followed by a Pooling Layer. The primary aim of this layer is to decrease the size of the convolved feature map to reduce computational costs. This is performed by decreasing the connections between layers and independently operates on each feature map. Depending upon the method used, there are several types of Pooling operations. It basically summarises the features generated by a convolution layer.

In Max Pooling, the largest element is taken from feature map. Average Pooling calculates the average of the elements in a predefined sized Image section. The total sum of the elements in the predefined section is computed in Sum Pooling. The Pooling Layer usually serves as a bridge between the Convolutional Layer and the FC Layer.

This CNN model generalises the features extracted by the convolution layer, and helps the networks to recognise the features independently. With the help of this, the computations are also reduced in a network.

### 3. Fully Connected Layer

The Fully Connected (FC) layer consists of the weights and biases along with the neurons and is used to connect the neurons between two different layers. These layers are usually placed before the output layer and form the last few layers of a CNN Architecture.

In this, the input image from the previous layers are flattened and fed to the FC layer. The flattened vector then undergoes few more FC layers where the mathematical functions operations usually take place. In this stage, the classification process begins to take place. The reason two layers are connected is that two fully connected layers will perform better than a single connected layer. These layers in CNN reduce the human supervision

### 4. Dropout

Usually, when all the features are connected to the FC layer, it can cause overfitting in the training dataset. Overfitting occurs when a particular model works so well on the training data causing a negative impact in the model’s performance when used on new data.

To overcome this problem, a dropout layer is utilised wherein a few neurons are dropped from the neural network during training process resulting in reduced size of the model. On passing a dropout of 0.3, 30% of the nodes are dropped out randomly from the neural network.

Dropout results in improving the performance of a machine learning model as it prevents overfitting by making the network simpler. It drops neurons from the neural networks during training.

### 5. Activation Functions

Finally, one of the most important parameters of the CNN model is the activation function. They are used to learn and approximate any kind of continuous and complex relationship between variables of the network. In simple words, it decides which information of the model should fire in the forward direction and which ones should not at the end of the network.

It adds non-linearity to the network. There are several commonly used activation functions such as the ReLU, Softmax, tanH, and Sigmoid functions. Each of these functions has a specific usage. For a binary classification CNN model, sigmoid and softmax functions are preferred, and for multi-class classification, generally, softmax is used. In simple terms, activation functions in a CNN model determine whether a neuron should be activated or not. It decides whether the input to the work is important or not using mathematical operations.

## Model evaluation

Precision is a key performance metric for assessing the success of a model’s predictions. It is calculated by dividing the total number of true positive predictions by the sum of true positive and false positive predictions. The precision, recall, F1-score, and support metrics can be used to evaluate the model’s performance on different classes such as yawn, no_yawn, closed, and open eyes.

The true positive rate, also referred to as recall, measures the proportion of data samples belonging to the positive class that the model correctly identifies. An evaluation metric in machine learning called the F1 score, can be used to measure the accuracy of the model’s predictions. Furthermore, the number of samples with the correct response in each class can be utilized to define support in this context.

In the context of machine learning, epochs refer to the number of times a model goes through the entire training dataset during the training process. Loss, on the other hand, is a measure of how well a model is performing on a given task, such as classification or regression. Specifically, the loss is a numerical value that represents the difference between the predicted output of the model and the true output label of the training data. During training, as the model learns, it aims to minimize the loss function by adjusting the values of its parameters. The loss function can be used to evaluate the performance of a model across different epochs. Generally, as the number of epochs increases, the loss should decrease. This is because the model becomes better at making predictions as it sees more examples from the training data. However, if the model is overfitting to the training data, then the loss may start to increase after a certain number of epochs. This is because the model has started to memorize the training data and is not generalizing well to new examples. Therefore, the optimal number of epochs can vary depending on the complexity of the model and the amount of training data available. Finding the right balance between the number of epochs and the loss is an important aspect of training a machine learning model.

## Using IOT devices:

Driver drowsiness detection system used various hardware components such as:-

1. **FTDI** : The chips produced by Future Technology Devices International are known as FTDI chips. To connect to RS232 and parallel FIFO hardware interfaces, USB adapters employ FTDI chips. The USB-2-COM interface is used the most frequently. cables for cell phones. The chip transforms RS232 into USB because mobile phones only have USB output whereas PCs may only have RS232 or UART output. Moreover, the virtual device is created by the PC driver.
2. **ESP32-Cam**: A compact, inexpensive development board built on the ESP32 platform is called ESP32- CAM. It is the best option for Internet of Things applications, building prototypes, and do-it-yourself projects. The board includes two powerful 32-bit LX6 Processors, WIFI, classic Bluetooth, and low power BLE. The main frequency adjustment runs from 80MHz to 240MHz, and it uses a 7-stage pipeline architecture, an on-chip sensor, a Hall sensor, a temperature sensor, and other sensors.
3. **GPS MODULE**: Using a method known as trilateration, one of the GPS devices pinpoints a specific place on Earth using satellite data. A GPS receiver trilaterates radio waves to determine satellite distances in the interim. This illustration of triangulation, which measures angles, is also analogous to trilateration (Tim Gun- ther, 2020). GPS modules have small computers and antennas that are used to directly receive data from satellites through certain RF frequencies. From there, it will get information from a variety of sources, including timestamps from all visible satellites. If the module’s antenna can identify at least four satellites, it can precisely calculate its location and time.

## Results

To minimize damage and prevent accidents, but this is a difficult and time-consuming task. With the advancement of computer science technology, it is now possible to detect driver fatigue. Several techniques have been developed in the past to detect driver drowsiness. In this paper, we proposed a novel method for detecting real-time driver fatigue by monitoring behavioural measures on facial expressions, human physiological signals, and vehicle parameters.The research focuses on feature extraction methodologies such as preprocessing, filtering, and normalising. Facial expressions such as yawning and eye features have been captured and analysed using computer vision techniques based on deep learning algorithms. The signals were extracted using built-in sensors of modern wearable devices such as smartwatches in this study.
Sequential’s CNN Model architecture

![image](https://user-images.githubusercontent.com/103866475/236674715-ca0bb899-496d-4514-bea8-c269c6372224.png)


The figure above shows the architecture of the deep learning model. The architecture described corresponds to a convolutional neural network (CNN) that is typically used for image classification tasks. Here are some conclusions that can be drawn from the information you provided:

1. The model is relatively complex: With almost 500,000 parameters, the model is quite large and can potentially capture complex relationships between the input data and the output labels.
2. The model includes common CNN layers: The four convolutional layers and three pooling layers are common building blocks of CNNs that help extract features from the input image and reduce its spatial dimensions.
3. The flattening layer is used to convert the output of the convolutional layers to a 1D vector that can be fed into a fully connected layer. This is a common technique in CNNs used for image classification.
4. The dropout layer is a regularization technique that randomly drops out a fraction of the neurons during training to prevent overfitting. The use of dropout suggests that the model was likely trained on a relatively small dataset.

## Model performance

Precision is a key performance metric for assessing the success of a model’s predictions. It is calculated by dividing the total number of true positive predictions by the sum of true positive and false positive predictions. The precision, recall, F1-score, and support metrics can be used to evaluate the model’s performance on different classes such as yawn, no_yawn, closed, and open eyes.

The true positive rate, also referred to as recall, measures the proportion of data samples belonging to the positive class that the model correctly identifies. An evaluation metric in machine learning, called the F1 score, can be used to measure the accuracy of the model’s predictions. Furthermore, the number of samples with the correct response in each class can be utilized to define support in this context.

In the context of machine learning, epochs refer to the number of times a model goes through the entire training dataset during the training process. Loss, on the other hand, is a measure of how well a model is performing on a given task, such as classification or regression. Specifically, loss is a numerical value that represents the difference between the predicted output of the model and the true output label of the training data. During training, as the model learns, it aims to minimize the loss function by adjusting the values of its parameters. The loss function can be used to evaluate the performance of a model across different epochs. Generally, as the number of epochs increases, the loss should decrease. This is because the model becomes better at making predictions as it sees more examples from the training data. However, if the model is overfitting to the training data, then the loss may start to increase after a certain number of epochs. This is because the model has started to memorize the training data and is not generalizing well to new examples.

Therefore, the optimal number of epochs can vary depending on the complexity of the model and the amount of training data available. Finding the right balance between the number of epochs and the loss is an important aspect of training a machine learning model.

The below figure shows the epochs vs loss graph for our model. The graph is a falling curve. A graph of epochs vs loss that is falling indicates that the model is improving as it trains. Specifically, as the number of epochs increases, the loss should decrease. This indicates that the model is becoming better at making predictions on the training data, and is capturing the underlying patterns in the data. However, it is important to keep in mind that the loss function is only a

measure of how well the model is doing on the training data. It does not necessarily mean that the model is generalizing well to new, unseen data. To evaluate the model’s performance on unseen data, it is important to use a separate validation set or test set.

Additionally, it is important to monitor the loss over time and ensure that it continues to decrease or level off, rather than increasing again. If the loss starts to increase after a certain number of epochs, this may indicate that the model is overfitting to the training data and is not generalizing well. Therefore, it is important to strike a balance between the number of epochs and the complexity of the model to avoid overfitting.

![image](https://user-images.githubusercontent.com/103866475/236674757-3e6c63e5-8f75-43ff-9b08-3316f4c495f0.png)

A graph of epochs vs accuracy shows how the accuracy of the model changes over time as it goes through the training process. Specifically, as the number of epochs increases, the accuracy should increase as the model improves. A rising accuracy graph indicates that the model is learning and improving as it trains, and is becoming better at making predictions on the training data. However, as with the loss function, it is important to keep in mind that the accuracy on the training data is not necessarily indicative of how well the model will perform on new, unseen data.

To get a better understanding of how well the model is generalizing, it is important to evaluate its performance on a separate validation or test set. Additionally, it is important to monitor the accuracy over time to ensure that it continues to increase or level off, rather than decreasing again. If the accuracy starts to decrease after a certain number of epochs, this may indicate that the model is overfitting to the training data and is not generalizing well.

![image](https://user-images.githubusercontent.com/103866475/236674773-a990479a-3b9f-48bc-a801-c08801002510.png)


Above figure Epochs vs accuracy graph for our model. It is a rising graph. Overall, a rising accuracy graph is a positive sign that the model is learning and improving, but it should be used in conjunction with other evaluation metrics to ensure that the model is performing well on both the training and test data.

## Conclusion

Throughout this endeavor, we picked up a lot of new skills. First, less complicated models can be just as effective as more sophisticated ones in completing tasks. The accuracy of the K-Nearest Neighbor model in our situation was comparable to that of the LSTM model. Yet ultimately, it is better to employ the more sophisticated model with a lower false-negative rate than a simpler model that could be easier to implement because we do not want to mistakenly label those who are sleepy as alert. Second, normalization was essential for our success. We realized that everyone had a unique baseline for their eye and mouth aspect ratios, so it was necessary to normalize for each participant. The majority of our effort was spent on data pre-processing and feature extraction/normalization outside of the runtime for our models. Updating our research and investigating ways to reduce the false-negative rate for kNN and other simpler models will be fascinating. Nowadays, the use of vehicles is increasing at an increasing rate. As a result, there are more car accidents on the road. Driver weariness, or drowsiness is a common contributing factor in auto accidents. This is a very severe issue that contributes to hundreds of thousands of traffic accidents annually. Thus, it is essential to have a warning system so that the siren will activate and warn other drivers anytime the driver begins to feel sleepy. Driver Drowsiness is a significant reason for thousands of road accidents all over the world. Driver drowsiness detection is a car safety technology that helps prevent accidents caused by the driver getting drowsy. The project aims at providing a solution for Driver Drowsiness Detection using CNN and image processing. The project aimed at optimizing the model to limit the number of parameters under 250k for easy deployment on edge devices. This deployment is possible through the Canvas Platform by making use of their compiler called deepC. Thus effectively bringing AI out on edge — in actual and physical real-world use cases.

## Future Scope

There are a few things we can do going forward to enhance our findings and hone the models. In order to account for any movement by the person in the video, we must first integrate the distance between the facial landmarks. We think quick movements by the participant may indicate tiredness or waking up from microsleep because, in reality, the participants won’t be static on the screen. Second, to get better outcomes, we wish to update parameters with our more sophisticated models (NNs, ensembles, etc.). Lastly, and most importantly, we want to gather our own training data from a bigger sample of people (more data!) while integrating new distinguishing sleepiness signs such as sudden head movement, hand movement, or even tracking eye movements.
