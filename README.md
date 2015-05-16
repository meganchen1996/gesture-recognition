# gesture-recognition
Final Project for CS378 FRI Autonomous Intelligent Robotics 

In this project, I basically implemented basic gesture recognition. I was trying to get the robot to recognize the fact that I had raised one of my arms over my head. Didn't matter which one, as long as one was raised it would return true and print to the console that the there was an arm over a head on the skeleton.

I used openni_tracker node from ros and listened for the transforms from the different joints/frames, using the information I got in the transforms, I stored the position data into a StampedTransform object for each joint frame. 


I want to implement even more gestures later on, but at last minute without my group since they dropped the class 3 days before the project due date, I tried my best to at least get the basic of recognizing any gesture for what it was. 



To run this project: 
roscore in terminal
rosrun openni_tracker openni_tracker
roslaunch openni_launch openni.launch 
