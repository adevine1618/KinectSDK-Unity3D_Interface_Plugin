*********************************README*********************************

                      KinectSDK / Unity3D Interface
		                  v.3.0

                             Andrew DeVine
                 University of Central Florida ISUE Lab
                    http://www.eecs.ucf.edu/isuelab

************************************************************************

Thanks for downloading!

The Microsoft Kinect SDK is required for this dll,
As well as all supporting Microsoft Speech software:

http://www.microsoft.com/en-us/kinectforwindows/download

If you don't have these already installed on your system, you may have
to uninstall this program, install the prerequisites, and then
re-install this dll.

Do not change the directory of the supporting dlls.

New Features:
    1. The Kinect Audio Array is now accessible from Unity! The built-in
	speech recognizer can be used with a few simple functions.

    2. The NUI is now two-player (the max amount the SDK allows).

    3. You can now display joint data in an on-screen GUI easily.

    4. Now with more comments! And how!


************************************************************************
                                 SETUP
************************************************************************

1) Copy KUInterfaceCPP.dll into the Unity game's working directory
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


AUDIO:

- Call GetLastRecoResult() to get the last string recognized by the
Kinect Audio Speech Recognizer.

- Call GetGrammar() to get a string array of the current grammar loaded
into the Kinect Audio Speech Recognizer. The grammar initially loaded
is {"hello", "goodbye"}.

- Call ClearGrammar() to reset the Speech Recognizer's grammar to { }.

- Call AddToGrammar(string word) to add a string to the Speech Recognizer's
grammar. For ease of recognition, spell everything out (for example, if you
want the recognizer to fire when the number '42' is spoken, call
AddToGrammar("fortytwo").


CAMERA:

- Call GetCameraAngle() to get the Kinect Camera's current angle from the
horizontal as a float.

- Call SetCameraAngle(int angle) to set the Kinect Camera's angle from the
horizontal. Do not change the camera angle more than once every 30 seconds,
as this may damage the motor (A provision to prevent this already exists,
do not remove this code). The camera is capable of -27 deg. to 27 deg.


************************************************************************
December 2011

Questions? email: adevine@knights.ucf.edu
************************************************************************