# Problem Statement

Crime and terrorism, which are increasing at a huge rate,  require serious monitoring and controlling. During encounters, terror attacks, or tracking down the criminals and terrorists, soldiers and police force suffer a lot of deadly injuries and undergo fatal situations. Risking their lives. Carrying on criminal hunt  in difficult topography  is not an easy task, life threats and risks are involved. While shooting, snipers  have  risks of being identified, which might lead to their death. Target acquisition requires great  accuracy and exactness, target estimation methods also needs to precisely locate the location of the enemy, even a small  error causes huge 
risks of lives.

# Installation:

Use the package manager pip to install the app

```
pip install cv2 
pip install numpy
pip install pyserial
pip install dlib
```

# Solution:

The idea is to develop automatic target shooter that will detect a particular person (here, it refers to criminals or terrorists) and will aim and shoot at them. It can also be substituted for a sniper. 24 hours surveillance is being provided, through the cameras. When the images of the specified person will be captured by the cameras, in their field view, the gun will adjust its position, aiming at the target and will be pointed by a laser beam. 

## Video Link 
https://youtu.be/_svrFGHh7yc

## Model image
![Model image](https://github.com/Sayantani-Bhattacharya/IOT_Snipper/blob/master/image.jpeg?raw=true)

# Plan of Execution:

The automatic target shooter can detect a particular person (here, it refers to criminals or terrorists) and will aim and shoot at them. 

Two cameras are installed for viewing a stereoscopic pair of separate images, depicting as a single three-dimensional image, using Computer Vision. When the images of the specified person will be captured by the cameras, the three cordinates, x, y, and z will be found using scaling. The z coordinate will be found using depth map calculated using stereoscopic pair of images. These coordinates will be transferred to arduino where the coordinates will be converted into angles, for the movement of the motors. Serial communication will be enabled via pyserial between the python file and the arduino. Thus, whenever the enemy(recognised image person) will appear in their field view, the gun will adjust its position, aiming at the target. A classifier is built and trained to classify the specified person, then, whenever that person appears in the field of view of the cameras, that specific person's frontal face will be detected, then it's centroid will be calculated, and pointed by a laser beam.

Due to the effect of gravity the bullet may not point at the accurate position as targeted. So we need to consider the projectile motion of the bullet. The depth of the target and bullet speed is known so we can calculate the angle at which we need to shoot at the target. If the target is moving then first it will track the person for some range of time then after estimating it's speed it's near future position can be calculated. So it will target at its esmitated position. The speed will be calculated both in X and Y direction. So it can track even a person climbing up a stair.

Arduino IDE(Arduino Uno board) and PySerial were used to drive the motors (a servo and a dc motor) which were used for positioning the gun.  

The python file(facedetection.py) is detecting the frontal face of the human using haarcascade classifier and then using lbph face recognition the face is being recognised for the particular person with whom images it has been trained with. 

Communication is established between python file(facedetection.py) and file containing arduino code(targetshooter.ino or finaltarget.ino) using pyserial. The .ino file contains the arduino code for driving the motors which will automatise the movement of the gun.

Further Implementation - 

Raspberry pi can be used to connect with firebase, helping in retrieving data of newly recognised terrorists.
The serial communication via pyserial to arduino is quite slow which results in a lagging motion of the motors, we can improve the communication gap using raspberry pi.
The counter of the bullets shots can also b maintained.


When the motors reach the tolerance limit of the coordinate Set Point values, obtained from the detection algorithm,  that specific person will be pointed by a laser beam. The power supply circuit of the gun-trigger mechanism will be completed using Arduino Code, and bullet will be fired.

First, we perform tunning to get the optimal values of Gain parameters of the controller. Operationally, we will then estimate angular positon from position sensor readings. These are used as imput for the PID controller which will reduce the error between target and measured value, increasing the accuracy of shooting.

# targetdetection.py

code for calculation of depth using stereovision concept to find the z coordinate
```
import cv2 as cv
import serial as ser
import numpy as np

depth = (focalLength * baseline) / (disparity*0.264)
cX=(int)(cX/480) #Scaling the centroid co-ordinates 
cY=(int)(cY/480) #(sending the x, y, z coordinates through serial to arduino file) 
ser.write(cX) 
ser.write(cY) 
ser.write(depth[cX,cY])
```

# Hardware:
2 Web Cameras, Arduino UNO, Servo Motor, Stepper Motor, Electronic Gun, PID controllers, Raspberry Pi, Battery power supply, Position sensor 

# Software:
OpenCV, PySerial, numpy

## Team Name 
Creators

## Team Members
Anupriya Shree
Sayantani Bhattacharya
Anuktiti Rawat

