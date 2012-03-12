*********************************README*********************************

                      KinectSDK / Unity3D Interface
		                  v.4.0

                             Andrew DeVine
                 University of Central Florida ISUE Lab
                    http://www.eecs.ucf.edu/isuelab

************************************************************************

Thanks for downloading!

The Microsoft Kinect SDK v.1.0 is required for this dll:

http://www.microsoft.com/en-us/kinectforwindows/download


************************************************************************
                                 SETUP
************************************************************************

1) Copy KUInterface.dll into the Unity game's working directory
(Main Folder; It shares the game's name, and is the parent folder of
'Assets').

2) Add KUInterface.cs to your Unity project (Assets/Scripts) and attach
it to a GameObject.
See: http://unity3d.com/support/documentation/Manual/Scripting.html


************************************************************************
                                  USE
************************************************************************

NUI:

- Call GetJointPos(KinectWrapper.Joints joint) to retrieve the given
joint's current position as a Vector3 object.

- Call the override GetJointPos(int player, KinectWrapper.Joints joint)
for player = 1,2 to use two-player mode. The Microsoft Kinect SDK supports
a maximum of two players with fully recognized skeletons. To use this,
field 'twoPlayer' must be set to 'True'.

- To display the joint information on the screen, set
'displayJointInformation' to 'True'.


CAMERA:

- Call GetCameraAngle() to get the Kinect Camera's current angle from the
horizontal as a float.

- Call SetCameraAngle(int angle) to set the Kinect Camera's angle from the
horizontal. Do not change the camera angle more than once every 30 seconds,
as this may damage the motor (A provision to prevent this already exists,
do not remove this code). The camera is capable of -27 deg. to 27 deg.


************************************************************************
March 2012

Questions? email: adevine@knights.ucf.edu
************************************************************************