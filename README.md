## Welcome to BirdVision

Have you ever witnessed a bird collide on your windows? How often did you notice that happen? Did you do anything about it? Every year during the migratory season, that is, Spring and Fall, millions of birds lose their lives from hitting glass windows. Glass being a transparent object, falls out of the birds’ visual spectrum, thus making them unaware of its presence and causing fatalities. We are an interdisciplinary team with a vision, working on gathering data on window related bird deaths and how we may prevent them and save bird lives. 

### What is BirdVision?

BirdVision is a system for recognizing the presence of birds along with identifying bird window strikes using machine vision. It is composed of several different data gathering, data management, and data processing modules which we connected into a mostly automated pipeline.

### How does it work?

There are several modules to the BirdVision system:

![BirdVision Flowchart](/images/BirdVisionFlowchart.png)

**Module 1 - Data Collection**

![Sensor Setup](/images/SensorSetup.jpg)

```
Data collection in BirdVision currently comes in two forms, video frames and sensor data. 
In order to train the neural network, we needed to build a data set. To do that, we created 
sensors which could be installed on windows and detect the vibrations from a bird strike.
Once the strike is detected, the vibration data is collected and a camera is activated to 
save image frames at the time of the strike. The data is saved to a local file on the systems 
running the sensors.
```


**Module 2 - Data Transfer**
```
Once the data has been saved to a local folder, a script running every five minutes syncs the 
new files with an S3 bucket on the Amazon Sagemaker platform. This bucket acts as a repository 
which can then be accessed by other Sagemaker tools.
```

**Module 3 - Image Annotation**

![Bird Labelling Job](/images/BirdLabellingJob.png)

```
From the S3 Bucket, the images get collated into labelling jobs. From there, volunteers can apply labels to the images using a simple and intuitive interface. If there is a bird in the image, they click the appropriate button. This user input will allow us to create a large enough database to finish training our neural network.
```
**Module 4 - Neural Network**
```
This module is currently in the works. As we grow our dataset, we are training a neural network to complete the jobs in Module 3. The more data that passes through the system, the better the neural network gets at classifying what is and isn’t a bird/window collision. The system is already well trained at detecting birds, we are now pivoting to detecting window collisions.
```

### What still needs to be done?
BirdVision is still a work in progress. Our vision is to have live or recorded footage from multiple sources constantly being run through the neural network in order to provide the most robust coverage possible. To accomplish this, we need to transition from physical sensors to pure video. We also need to set up a way for labelling jobs to be created automatically.

### How can you help?
If you would like to help us label data, or are interested in using our framework for your own image/footage recognition, please contact us at [email address]. 
