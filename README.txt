*********************************README*********************************

                      KinectSDK / Unity3D Interface
		                  

                             Andrew DeVine

************************************************************************

Thanks for downloading!

The Microsoft Kinect SDK v.1.7 is required for this dll:

http://www.microsoft.com/en-us/kinectforwindows/develop/developer-downloads.aspx

Changes (08/16/13):
- DLL LOCATION HAS CHANGED TO ASSETS/PLUGINS
- Initialization routine now starts first connected sensor found.
- Depth Stream is now correct. The depth stream is actually of type 'short'.
  However, Color32 object requires bytes. Therefore, the displayed depth
  image is 'looped' over intensities, in order to not lose resolution.
- There still seems to be a problem with editing scripts, then returning
  to the Unity window and having it crash on play. I'm investigating this.

Since there still seems to be a demand for this, I've revisited it.
If you're still getting a 'DLL not found' error after following the setup
instructions, make sure the Environment Variable 'KINECTSDK10_DIR' is set
to...you guessed it...the Kinect SDK dir.

This hasn't been rigorously tested, so the source is also on Github.
You'll probably have to change the build directory.


************************************************************************
                                 SETUP
************************************************************************

copy KUInterface.dll to Assets/Plugins

import the C# file into your game, and attach it to a game object.

use the C# functions as you would any other script in Unity.


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

- Call GetDepthData() to return the pixel depths as a short[][] array. The
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
Aug 2013

Questions? email: andrew@ardevine.com
************************************************************************