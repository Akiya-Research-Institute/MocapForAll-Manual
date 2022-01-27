# FAQ

## The camera does not work
- Select UE4 media player in [Select camera control framework](../how-to-capture/calibrate-cameras/connect-cameras/#select-camera-control-framework)
    - Try selecting different formats in "Image size"
- Select Direct Show in Select camera control framework
    - Select proper image size based on the camera specification

If none of these work, unfortunately MocapForAll will not be able to use the camera.

## Multiple cameras of the same model are not recognized
When connecting multiple cameras of the same model to a PC, there is a problem that some of them are not displayed (not detected) in the pull-down of camera selection in the app. In that case, try setting an arbitrary FriendlyName from the registry editor to the camera device that is not displayed.  
The method of setting / changing the FriendlyName differs depending on your environment, so please google it yourself. Since you are editing the registry, it is recommended to make a backup.  

## Virtual camera is not recognized
The default virtual camera in OBS does not work. Install [OBS-VirtualCam plugin](https://obsproject.com/forum/resources/obs-virtualcam.539/) and select Direct Show in [camera control framework](../how-to-capture/calibrate-cameras/connect-cameras/#select-camera-control-framework).

## Can I use a black-white camera?
No, you can't use a monochrome camera with this app. Please use an RGB camera. 

## AR marker is not recognized
- Make sure the camera image is [not a mirror image.](../how-to-capture/calibrate-cameras/connect-cameras/)
- Make sure the camera image is in focus on the AR marker.
- Make sure the AR marker is large enough in the camera image.
    - Printing a larger size of the AR marker may help
    - For camera calibration of extrinsic parameters, see [If the marker cannot be read properly](../how-to-capture/calibrate-cameras/execute-calibration/#if-the-marker-cannot-be-read-properly) section.

## Camera calibration of extrinsic parameters does not work
See [If the marker cannot be read properly](../how-to-capture/calibrate-cameras/execute-calibration/#if-the-marker-cannot-be-read-properly) section.

## It does not capture even after camera calibration
- At the start of capture, only a person standing upright can be recognized. So, [rotate the image appropriately according to the actual orientation of the camera.](../how-to-capture/calibrate-cameras/connect-cameras/)
- Make sure that two or more cameras that have been calibrated can see your whole body.
- It will not work if the final frame rate is below 4 fps. [Check the frame rate](../how-to-capture/adjust-settings/optimize-performance/#check-the-frame-rate).

## Does it support capturing multi-person?
No, currently only one person can be captured. Therefore, only one person should be shown on the camera.  

## VMT doesn't work
Check errors in VMT Manager. Especially, check if [Room Matrix](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/trouble/#room-matrix-is-not-set) is set.

## The motion of Virtual trackers are wrong
Make sure that the [alignment of coordinates between SteamVR and MocapForAll](../how-to-export/to-steamvr/#align-coordinates-of-steamvr-and-mocapforall) is correct.

## There is no serial number input field
Please install the latest MocapForAll. From version 1.0 and above, you do not need to input the HMD serial number.  

## Difference between MocapForAll and others
- [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/advanced/3d_reconstruction_module.md)： The basic idea is similar, but the licenses are very different. Basically, you can use OpenPose only for "ACADEMIC OR NON-PROFIT ORGANIZATION NONCOMMERCIAL RESEARCH USE ONLY"
