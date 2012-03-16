*********************************README*********************************

                      KinectSDK / Unity3D Interface
		                  v.4.1

                             Andrew DeVine
                 University of Central Florida ISUE Lab
                    http://www.eecs.ucf.edu/isuelab

************************************************************************

Thanks for downloading!

The Microsoft Kinect SDK v.1.0 is required for this dll:

http://www.microsoft.com/en-us/kinectforwindows/download

Changes:
	A bug was fixed, occuring on restarting gameplay in Unity, which
	caused the editor to freeze. Due to limitations with the Kinect SDK,
	prohibiting uninitialization and re-initialization of the sensor
	within a running application, the sensor remains on after the first
	NuiInit call.
		In the interest of condensing this download, I did not
	include an editor script to turn off the sensor when you close Unity
	(as this is not a problem for a Unity .exe build of the project,
	only when using the editor). You will see the red IR projector still
	active on your Kinect after you close the editor. So, BE SURE TO
	DISCONNECT YOUR SENSOR AFTER YOU CLOSE UNITY.


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