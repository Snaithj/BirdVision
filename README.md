## Welcome to BirdVision

We are an indterdisciplinary team working to gather data on window related bird deaths and how to prevent them.

### What is BirdVision?

BirdVision is a system for recognizing birds and bird window strikes using machine vision. It is composed of several different data gathering, data management, and data processing modules which we connected into a mostly automated pipeline.

### How does it work?

There are several modules to the BirdVision system:

```
**Module 1 - Data Collection**
Data collection in BirdVision currently comes in two forms, video frames and sensor data. In order to train the neural network, we needed to build a data set. To do that, we created sensors which could be installed on windows and detect the vibrations from a bird strike.
Once the strike is detected, the vibration data is collected and a camera is activated to save image frames at the time of the strike. The data is saved to a local file on the systems running the sensors.
```

```
**Module 2 - Data Transfer**
Once the data has been saved to a local folder, a script running every five minutes syncs the new files with an S3 bucket on the Amazon Sagemaker platform. This bucket acts as a repository which can then be accessed by other Sagemaker tools.
```

```
**Module 3 - Image Annotation**
From the S3 Bucket, the images get collated into labelling jobs. 
```
