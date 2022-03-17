# Changelog

## v1.16.0 (13 Mar. 2022)
- Added UE Mannequin characters.
- Added a function to export motion data as a FBX file.

## v1.15.0 (19 Dec. 2021)
- Updated the default map's background and lighting to make it easier to see.
- Added a function to stop rendering of the viewport.
- Added a function to preview the body tracking result in 2D.
- Added a function to stop the motion of lower body of the character.
- Fixed a bug that the app crashes when BVH export started if video is used and "Capture face" is on.

## v1.14.0 (29 Oct. 2021)
- Updated the AI for hand tracking. (MediaPipe Hand latest version)
- Added a function to preview the hand tracking result in 2D.
- Added a function to delay the input of camera in order to match the timing of the cameras. (You need to specify the delay in milliseconds by hand. So, it is not much practical yet.)
- Changed the camera preview UI to keep the aspect ratio of the image.
- Added a function to magnify the camera preview image.

## v1.13.3 (11 Oct. 2021)
- Fixed a bug that camera preview shows a white screen when DirectShow is used.
- Updated the French translation.

## v1.13.1 (6 Oct. 2021)
- Fixed a bug that shared memory settings were not saved correctly.
- Fixed a typo in the shared memory output specification.
- Removed unnecessary files.

## v1.13 (5 Oct. 2021)
- Added French translation.
- Added a function to export bone tranform and facial expression raw data to shared memory.
- Added a function to execute "StartCapture" and "LoadAllCameras" at startup when specified in command line arguments. (Example: MocapForAll.exe StartCapture LoadAllCameras)
- Fixed a bug that the VMT trackers for hands were not sent when "As controllers" is turned off.

## v1.12 (17 Sep. 2021)
- Changed the AI model for human detection at the start of tracking to the same model as v1.10 (MediaPipe Pose → YOLOv4).
- Added a function to capture motion from recorded videos.

## v1.11 (13 Sep. 2021)
- Changed the AI model for human detection at the start of tracking (YOLOv4 → MediaPipe Pose). The CPU/GPU usage is reduced.
- Added a function to send VMTs of hands as controllers.
- Added options to adjust offsets of virtual tracker positions for all body parts.
- Added buttons next to the scroll bars to adjust the values.
- Added a function to display the camera name on the viewport.
- Added a function to automatically set the language when the app started for the first time. (To fix the problem that numbers cannot be handled correctly in some languages.)
- Fixed a bug that "Align coord to VR" button always appears when the app launched.

## v1.10 (4 Sep. 2021)
- Added a function to [automatically align the coordinates of SteamVR and MocapForAll](http://localhost:8000/MocapForAll-Manual/how-to-export/to-steamvr/#align-coordinates-of-steamvr-and-mocapforall).  

## v1.9.1 (23 Aug. 2021)
- Added MetaHuman models of various body types.

## v1.9 (21 Aug. 2021)
- Added Japanese translation.
- Added help displayed by mouse over.
- Added a function to move the viewpoint with the mouse wheel and drag while holding down the middle mouse button.

## v1.8 (17 Aug. 2021)
- Fixed a bug that v1.6 updates were not included in v1.7.
- Fixed a bug that rotation of Root bone sent by VMC protocol was invalid. This fixes the issue that VMC4UE was unable to receive motion.
- Fixed a bug that the feet sticked to the ground when using a short character. (Changed to automatically adjust the ground contact strength of the foot according to the scale of the lower body.)
- Fixed a bug that hip bone name in BVH file is not based on the model.
- Added an option to export BVH file without root motion. Removed the option to export BVH file with root which only moves horizontally.

## v1.7 (7 Aug. 2021)
- Updated the AI used in "Speed" and "Speed+" modes. (From Movenet V1 to V4)
- Added a function to automatically adjust the position and the orientation of the ground.
- Added a function to automatically calibrate the camera extrinsic parameter by using human motion.

## v1.6 (31 Jul. 2021)
- Fixed a bug that the first letters of bone names in VMC protocol were not uppercase.  
	(This change fixes the problem that some apps such as VSeeFace could not receive bone data from MocapForAll.)
- Changed the messages sent by VMC protocol. The following messages are sent additionally:
	- /VMC/Ext/Root/Pos (The value is always 0 (origin))
	- /VMC/Ext/OK       (The value is always 1)
	- /VMC/Ext/T
	- /VMC/Ext/Tra/Pos  (This allows some apps such as VirtualMotionCapture to receive data from MocapForAll as trackers.)
- Devided the bundle (packet) of VMC protocol data so that it does not exceed 1500 bytes.
- Fixed a bug that settings about receiving VMC protocol are not saved.
- Fixed a bug that VMC protocol data could not be received after changing character.
- Added an option to add the root bone to the bone hierarchy in BVH file.

## v1.5 (22 Jul. 2021)
- Added a function to export motion data via VMC protocol as a "Performer".
- Added a function to receeve facial morph data from "Assistant" via VMC protocol, and send it as a "Performer".
- Added a function to automatically load the VRM file which was loaded by the user last time.
- Added a function to show warnings when calibration results are doubtful.

## v1.4.1 (18 Jul. 2021)
- Added a function to export motion data as a BVH file.
- Added a function to save and load whole camera setup.
- Improved animation retarget for VRM models.
- Fixed a bug that some cameras do not work in "UE4 Media Player" mode.
- Fixed a bug that Chroma-key map cannot be loaded if Apendix2 is not installed.

## v1.3 (10 Jul. 2021)
- Changed the default library for webcam operation.  
    The new library uses UE4's Media Player, which improves performance at high resolutions, but (probably) makes virtual cameras unusable.  
    If you want to use virtual cameras, select "DirectShow" from the pull-down menu of "Add Camera".
- Added a function to select the GPU to be used for calculation.
- Added a button to reset the detected marker position.
- Added a function to reset the view of the 3D viewport.
- Added a function to make the view of the 3D viewport follow the character.
- Fixed a bug that the offset value of the virtual tracker for the right foot was not loaded correctly at startup.
- Changed the display method of FPS.
- Changed the installatioin method.  
    Precision mode, HDRI maps, MetaHuman Character, and TensorRT mode are now optional.  
    Network Installer was added for easy installation.

## v1.2 (3 Jul. 2021)
- Added a function to display the position of the cameras in 3D viewport.
- Added a function to calibrate camera extrinsic parameters using multiple ArUco markers.
- Added a function to calibrate camera extrinsic parameters using multiple ChArUco diamond markers.
- Added a function to input the marker size, which is used to define the scale of tracking space.

## v1.1 (25 Jun. 2021)
- GPU_CUDA mode is removed.
- GPU_DirectML mode is added.  
	DirectML provides GPU acceleration on DirectX 12 capable GPUs.  
	Supported GPUs include:  
	- NVIDIA Kepler (GTX 600 series) and above  
	- AMD GCN 1st Gen (Radeon HD 7000 series) and above
- CPU version and GPU version are integrated.

## v1.0.1 (18 Jun. 2021)
- Added a function to flip the camera image.

## v1.0 (17 Jun. 2021)
- No change from v0.2 (To match the version number with the full version)

## v0.2
- Camera
    - Changed the library for webcam manipulation from OpenCV to DirectShow.
    - Added a display for camera name.
    - Added a function to change camera image size.
- Calibration
    - Added a function to reset the calibration information when user clicks "Start" in calibration panel.
    - Added a function to reset the calibration information when user changes camera.
- Data export
    - Added a function to automatically enable VMT's option "SetAutoPoseUpdate" when user clicks "As relative position to HMD"
    - Removed the text box to specify HMD serial number. (vmt_010 and before are not supported any longer.)
    - Added options to adjust offsets for virtual trackers of pelvis and feet.
- UI
    - Added a scroll bar in the Settings menu.
    - Added a limitation that some options can be changed only when capture is stopped.
    - Changed the max value from 2 to 5 of the slider in "Settings > Coordinates > Scales".
    - Removed the function to draw tracking positions on camera preview.
- Installation
    - Added a unzip command file for installation.
    - Removed *.pdb which is not necessary to run the app.
