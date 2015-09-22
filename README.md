# gesture-recognition
Final Project for CS378 FRI Autonomous Intelligent Robotics 

In this project, I implemented basic gesture recognition. I was trying to get the robot to recognize the fact that I had raised one of my arms over my head. Didn't matter which one, as long as one was raised it would return true and print to the console that the there was an arm over a head on the skeleton.

I used openni_tracker node from ros and listened for the transforms from the different joints/frames, using the information I got in the transforms, I stored the position data into a StampedTransform object for each joint frame. 


To run this project: 
roscore in terminal
rosrun openni_tracker openni_tracker
roslaunch openni_launch openni.launch 

To run this node: 
rosrun gesture_recognition gesture_recognition

Googledoc: 
https://docs.google.com/document/d/1BLY7RBUDHI90GwJdErgqO3rfFTzVEaCWvWU4ApkWcn4/edit?usp=sharing

