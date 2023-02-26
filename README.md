# Steering control using CNN
This repository contains code to train a car to steer in a simulated environment using Convolutional Neural Network (CNN). The simulator used to collect the trainind data and test the model is Udacity's self-driving car simulator. This was the term-end project for the ENPM690-Robot Learning course.

This project is the implementation of NVIDIA's paper "[End to End Learning for Self Driving Cars](https://arxiv.org/abs/1604.07316)".

The CNN model learns a mapping from the single-front facing camera on top of the car to the steering command. The architecture learns internal representation to detect road features.

The simulator has two modes: 1. Training Mode and 2. Autonomous Mode. The car was driven over two laps in both the directions to get a better dataset of the lap's images. The car was driven at the speed of 9 MPH. The center, left, and right view were captured by the simulator for each frame and the images were stored along with the generation of a csv file that has information of all the images.

Data was preprocessed by normalizing and center cropping the images. 

Data Augmentation was performed by adding a steering angle of +- 0.4 on the left and and right view images respectively. The images were also randomly horizontally flipped.

## Udacity's self-driving car simulator
<p align="center">
  <img src="https://github.com/AbhijitMahalle/steering_control_using_cnn/blob/master/gif/simulator.png" />
<p align="center">

## NVIDIA's Neural Network Architecture
<p align="center">
  <img src = https://github.com/AbhijitMahalle/steering_control_using_cnn/blob/master/gif/nvidia_architecture.png>  
<p align="center">

## Challenges
Initially, the car was trained to steer using the above architecture. However, the car was drifting even on straight stracks at the time of testing. Lack of sufficient training data and the absence of Maxpool layers in the above architecture might be the possible reasons. 

## Modified Neural Network Architecture
<p align="center">
  <img src = https://github.com/AbhijitMahalle/steering_control_using_cnn/blob/master/gif/simplified_architecture.jpg>  
<p align="center">
We added Maxpooling layers in the original architecture and the performance improved. The simulator uses a simple PI controller to control the steering action. 

## Requirement:
Python 2.0 or above
  
## Dependencies:
1. PyTorch
2. OpenCV

## Instructions to run the code
Download the folder and upload it in Google Colab to run it.

## Output
<p align="center">
  <img src = https://github.com/AbhijitMahalle/steering_control_using_cnn/blob/master/gif/output.gif>
<p align="center">
  
## Video Link
https://www.youtube.com/watch?v=kxRWDSFM-yQ&t=3s

## Hyper-parameters
* Sample size: 24111 
  - Training size: 19288, Validation size: 4823
* Batch size: 32
* Optimizer: Adam
* Loss: Mean Square Entropy
* No. of epochs: 22
* Activation function: ELU
* Parameters: 120000
* Connections: 15 million
* Training time: 22 minutes

## Results
<p align="center">
  <img src = https://github.com/AbhijitMahalle/steering_control_using_cnn/blob/master/gif/result.PNG>
<p align="center">

## Conclusion
* CNN can learn lane and road following without manual decomposition, semantic abstraction, path planning, and control.
* It can learn meaningful features from sparse training data.
* It can learns features without explicit labels during training.

