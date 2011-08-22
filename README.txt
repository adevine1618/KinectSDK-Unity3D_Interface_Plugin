*****************README*******************

      KinectSDK / Unity3D Interface
		  v.1.2

              Andrew DeVine
  University of Central Florida ISUE Lab

******************************************

This is an initial version that supports
only joint position data for one player.



SETUP:

1) Copy the built dll into the
Unity game's working directory (Main Folder).

2) Add KUInterface.cs to your Unity project
and attach it to a gameObject.

3) Call KUInterface.GetJointPos(KinectWrapper.Joints.JOINT)
to retrieve joint position data.



August 2011