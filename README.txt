*********************************README*********************************

                      KinectSDK / Unity3D Interface
		                  v.5.0

                             Andrew DeVine
                 University of Central Florida ISUE Lab
                    http://www.eecs.ucf.edu/isuelab

************************************************************************

Thanks for downloading!

The Microsoft Kinect SDK v.1.0 is required for this dll:

http://www.microsoft.com/en-us/kinectforwindows/download


New Features with this Release:

    1) The Depth and RGB streams are now available for your enjoyment!
    
    2) Intellisense summaries have been added for public members

    3) Now distributed as a Unity package for easy setup

WARNING: Using both the RGB and Depth feeds will cause a significant
drop in performance. Please be sure your system meets the requirements
found in the website above to maximize your experience with the SDK.


************************************************************************
                                 SETUP
************************************************************************

In Unity:
    Assets -> Import Package -> Custom Package

Select the package from the directory you downloaded it to!

Simple.


************************************************************************
                                  USE
************************************************************************

PUBLIC SETTINGS:

scaleFactor: scales all joint positions by this number. Do not set to zero.

twoPlayer: set to true to track the maximum of two skeletons. Do not change
           value while in play.

useRGB: update RGB feed every frame. Set to false if not being used to
        optimize performance. Do not change value while in play.

useDepth: update depth feed every frame. Set to false if not being used to
          optimize performance. Do not change value while in play.

displayJointInformation: for visualization of data.

diplayTextureImage: renders RGB feed on-screen.

displayDepthImage: renders depth feed on-screen as reverse-intensity image.


NUI:

- Call GetJointPos(KinectWrapper.Joints joint) to retrieve the given
joint's current position as a Vector3 object.

- Call the override GetJointPos(int player, KinectWrapper.Joints joint)
for player = 1,2 to use two-player mode. The Microsoft Kinect SDK supports
a maximum of two players with fully recognized skeletons. To use this,
field 'twoPlayer' must be set to 'True'.


IMAGE STREAMS:

- Call GetTextureImage() to get the RGB camera's current output as a
Texture2D object.

- Call GetDepthData() to return the pixel depths as a byte[][] array. The
coordinate depth[x=0][y=0] corresponds to the top-left corner of the depth
camera's viewport.


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