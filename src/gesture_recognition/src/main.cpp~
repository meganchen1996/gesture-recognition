#include <ros/ros.h>
#include <tf/transform_listener.h>
#include "geometry_msgs/Twist.h"
#include <XnOpenNI.h>
#include <math.h>
#include <std_msgs/String.h>
#include <std_msgs/Bool.h>
#include <iostream>
#include <time.h>
#include <tf/tf.h>

//two methods that will determine whether or not left arm or right arm were raised
bool raiseLeftArm(tf::StampedTransform leftHandTransform, tf::StampedTransform headTransform) {
      if(leftHandTransform.getOrigin().z() - headTransform.getOrigin().z() > .1) {
	std::cout<<"The left arm is raised!"<<std::endl;
	return true; 
      } else {
	return false;
      }
}

bool raiseRightArm(tf::StampedTransform rightHandTransform, tf::StampedTransform headTransform) {
      if(rightHandTransform.getOrigin().z() - headTransform.getOrigin().z() > .1) {
	std::cout<<"The right arm is raised!"<<std::endl;
	return true;
      } else {
	return false;
      }
}


int main(int argc, char** argv) {
  	
  	
  // Initialize ROS
  ros::init (argc, argv, "gesture_recognition_fun");
  ros::NodeHandle nh;

  
  //Transform Listeners for every joint/frame, will get transform between camera and joint
  
  tf::TransformListener headLsnr;
  tf::TransformListener neckLsnr;
  tf::TransformListener torsoLsnr;
  tf::TransformListener leftShoulderLsnr;
  tf::TransformListener leftElbowLsnr;
  tf::TransformListener leftHandLsnr; 
  tf::TransformListener rightShoulderLsnr; 
  tf::TransformListener rightElbowLsnr; 
  tf::TransformListener rightHandLsnr;
  tf::TransformListener leftHipLsnr; 
  tf::TransformListener leftKneeLsnr; 
  tf::TransformListener leftFootLsnr; 
  tf::TransformListener rightHipLsnr; 
  tf::TransformListener rightKneeLsnr; 
  tf::TransformListener rightFootLsnr; 
  
  //Stamped Transforms for each joint/frame, will store tf between camera and joint
  
  tf::StampedTransform headTransform;
  tf::StampedTransform neckTransform;
  tf::StampedTransform torsoTransform;
  tf::StampedTransform leftShoulderTransform;
  tf::StampedTransform leftElbowTransform;
  tf::StampedTransform leftHandTransform; 
  tf::StampedTransform rightShoulderTransform; 
  tf::StampedTransform rightElbowTransform; 
  tf::StampedTransform rightHandTransform;
  tf::StampedTransform leftHipTransform; 
  tf::StampedTransform leftKneeTransform; 
  tf::StampedTransform leftFootTransform; 
  tf::StampedTransform rightHipTransform; 
  tf::StampedTransform rightKneeTransform; 
  tf::StampedTransform rightFootTransform; 
  
  ros::Rate(10); 
  
  
  
  while(ros::ok()) {
    ros::spinOnce();
    //look for all transforms 
    try {
      headLsnr.waitForTransform("/openni_depth_frame", "/head", ros::Time(0), ros::Duration(1.0)); 
      headLsnr.lookupTransform("/openni_depth_frame", "/head", ros::Time(0), headTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      neckLsnr.waitForTransform("/openni_depth_frame", "/neck", ros::Time(0), ros::Duration(1.0)); 
      neckLsnr.lookupTransform("/openni_depth_frame", "/neck", ros::Time(0), neckTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      torsoLsnr.waitForTransform("/openni_depth_frame", "/torso", ros::Time(0), ros::Duration(1.0)); 
      torsoLsnr.lookupTransform("/openni_depth_frame", "/torso", ros::Time(0), torsoTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      leftShoulderLsnr.waitForTransform("/openni_depth_frame", "/left_shoulder", ros::Time(0), ros::Duration(1.0));
      leftShoulderLsnr.lookupTransform("/openni_depth_frame", "/left_shoulder", ros::Time(0), leftShoulderTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      leftElbowLsnr.waitForTransform("/openni_depth_frame", "/left_elbow", ros::Time(0), ros::Duration(1.0));
      leftElbowLsnr.lookupTransform("/openni_depth_frame", "/left_elbow", ros::Time(0), leftElbowTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      rightShoulderLsnr.waitForTransform("/openni_depth_frame", "/right_shoulder", ros::Time(0), ros::Duration(1.0));
      rightShoulderLsnr.lookupTransform("/openni_depth_frame", "/right_shoulder", ros::Time(0), rightShoulderTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      rightElbowLsnr.waitForTransform("/openni_depth_frame", "/right_elbow", ros::Time(0), ros::Duration(1.0));
      rightElbowLsnr.lookupTransform("/openni_depth_frame", "/right_elbow", ros::Time(0), rightElbowTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      rightHandLsnr.waitForTransform("/openni_depth_frame", "/right_hand", ros::Time(0), ros::Duration(1.0));
      rightHandLsnr.lookupTransform("/openni_depth_frame", "/right_hand", ros::Time(0), rightHandTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      leftHandLsnr.waitForTransform("/openni_depth_frame", "/left_hand", ros::Time(0), ros::Duration(1.0));
      leftHandLsnr.lookupTransform("/openni_depth_frame", "/left_hand", ros::Time(0), leftHandTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      leftHipLsnr.waitForTransform("/openni_depth_frame", "/left_hip", ros::Time(0), ros::Duration(1.0));
      leftHipLsnr.lookupTransform("/openni_depth_frame", "/left_hip", ros::Time(0), leftHipTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      rightHipLsnr.waitForTransform("/openni_depth_frame", "/right_hip", ros::Time(0), ros::Duration(1.0));
      rightHipLsnr.lookupTransform("/openni_depth_frame", "/right_hip", ros::Time(0), rightHipTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      leftKneeLsnr.waitForTransform("/openni_depth_frame", "/left_knee", ros::Time(0), ros::Duration(1.0));
      leftKneeLsnr.lookupTransform("/openni_depth_frame", "/left_knee", ros::Time(0), leftKneeTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      leftFootLsnr.waitForTransform("/openni_depth_frame", "/left_foot", ros::Time(0), ros::Duration(1.0));
      leftFootLsnr.lookupTransform("/openni_depth_frame", "/left_foot", ros::Time(0), leftFootTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
			}
    try {
      rightFootLsnr.waitForTransform("/openni_depth_frame", "/right_foot", ros::Time(0), ros::Duration(1.0));
      rightFootLsnr.lookupTransform("/openni_depth_frame", "/right_foot", ros::Time(0), rightFootTransform); 
      
    }
    catch (tf::TransformException ex) {
			  ROS_ERROR("%s", ex.what());
			  ros::Duration(1.0).sleep();
    }
    
    if(raiseLeftArm(leftHandTransform, headTransform) || raiseRightArm(rightHandTransform, headTransform)) {
	ROS_INFO("You succesfully detected the raising of an arm!"); 
    }
    return 0;
  }
  
}


  