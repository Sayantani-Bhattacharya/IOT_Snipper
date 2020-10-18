 #                                                                          Creators


# Problem Statement

Crime and terrorism, which are increasing at a huge rate,  require serious monitoring and controlling. During encounters, terror attacks, or tracking down the criminals and terrorists, soldiers and police force suffer a lot of deadly injuries and undergo fatal situations. Risking their lives. Carrying on criminal hunt  in difficult topography  is not an easy task, life threats and risks are involved. While shooting, snipers  have  risks of being identified, which might lead to their death. Target acquisition requires great  accuracy and exactness, target estimation methods also needs to precisely locate the location of the enemy, even a small  error causes huge 
risks of lives.

# Installation:

Use the package manager pip to install the app

```
pip install cv2
pip install numpy
pip install pyserial
```

# Solution:

The idea is to develop automatic target shooter that will detect a particular person (here, it refers to criminals or terrorists) and will aim and shoot at them. It can also be substituted for a sniper. 24 hours surveillance is being provided, through the cameras. When the images of the specified person will be captured by the cameras, in their field view, the gun will adjust its position, aiming at the target and will be pointed by a laser beam. 

## Video Link 
https://youtu.be/_svrFGHh7yc

# Plan of Execution:

The automatic target shooter can detect a particular person (here, it refers to criminals or terrorists) and will aim and shoot at them.

Two cameras are installed for viewing a stereoscopic pair of separate images, depicting as a single three-dimensional image, using Computer Vision. When the images of the specified person will be captured by the cameras, in their field view, the gun will adjust its position, aiming at the target. A classifier is built and trained to classify the specified person, then, whenever that person appears in the field of view of the cameras, that specific person will be pointed by a laser beam.

Arduino IDE(Arduino Uno board) and PySerial were used to drive the motors (a servo and a dc motor) which were used for positioning the gun.  

The python file(facedetection.py) is detecting the frontal face of the human using haarcascade classifier and then using lbph face recognition the face is being recognised for the particular person with whom images it has been trained with. 

Communication is established between python file(facedetection.py) and file containing arduino code(targetshooter.ino or finaltarget.ino) using pyserial. The .ino file contains the arduino code for driving the motors which will automatise the movement of the gun.

When the motors reach the tolerance limit of the coordinate Set Point values, obtained from the detection algorithm,  that specific person will be pointed by a laser beam. The power supply circuit of the gun-trigger mechanism will be completed using Arduino Code, and bullet will be fired.

First, we perform tunning to get the optimal values of Gain parameters of the controller. Operationally, we will then estimate angular positon from position sensor readings. These are used as imput for the PID controller which will reduce the error between target and measured value, increasing the accuracy of shooting.

# facedetection.py

```
depth = (focalLength * baseline) / (disparity*0.264)
cX=(int)(cX/480) #Scaling the centroid co-ordinates 
cY=(int)(cY/480) 
 #(sending the x, y, z coordinates through serial to arduino file) 
ser.write(cX)
ser.write(cY) ser.write(-depth[cX,cY])
```

# Hardware:
2 Web Camera, Arduino UNO, Servo Motor, DC Motor, Electric Gun, PID controllers, Raspberry Pi, Battery power supply, Position sensor 

# Software:
Open CV, PySerial 

