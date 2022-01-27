# Execute calibration

## Get intrinsic parameters

- Display [this image](https://raw.githubusercontent.com/Akiya-Research-Institute/MocapForAll-Wiki/main/resources/calibration/IntrinsicCalibration.png) on your PC's screen as large as possible.
- In MocapForAll, click `Start` button under `Camera > Calibration > Intrinsic`.   
- Take images with the camera from various angles for about 10 seconds. If the camera is already fixed, move the image instead of the camera.  

When calibration is completed, intrinsic parameters will be displayed on the app's screen and `Intrinsic  ☑Calibrated` will be shown.  

![](../../images/Camera-Calibration-Intrinsic-Execution.gif){ loading=lazy }

Save the camera calibration result from `Save`.

## Get extrinsic parameters

The procedure differs depending on the [4 methods to get extrinsic parameters](../what-is-camera-calibration/#4-methods-to-get-extrinsic-parameters) explained before.

=== "ChArUco board method"
    - Place the image printed in [Prepare markers](../prepare-markers/#print-marker-for-extrinsic-parameter-calibration) section on the floor. This will be the origin of the captured motion.  
    - Place the cameras where they can see the placed image.  
    - In MocapForAll, select `ChArUco board (default)` in `Settings > Calibration > Extrinsic calibration method`.  
    - Click `Start` button under `Camera > Calibration > Extrinsic`.  

    When calibration is completed, extrinsic parameters and the camera position will be displayed, and it will shows `Extrinsic  ☑Calibrated`.  
 
    !!! Tip "If it does not read the AR marker properly, try [If the marker cannot be read properly](#if-the-marker-cannot-be-read-properly)."

    ![](../../images/Camera-Calibration-Extrinsic-Execution-Charuco.gif){ loading=lazy }
    
=== "ArUco cluster method"
    - Place the images printed in [Prepare markers](../prepare-markers/#print-marker-for-extrinsic-parameter-calibration) section on the floor. `arucoMarker0.png` will be the origin of the captured motion.  
    - Place the cameras where they can see the placed images.  
    - In MocapForAll, select `ArUco cluster` in `Settings > Calibration > Extrinsic calibration method`.  
    - Click `Scan markers` button under `Camera > Calibration > Extrinsic`.  This will scan the relative positions of the markers. After a while, the markers will appear in the 3D viewport.
    - After all markers appeared, click **`Stop scanning`** and then **`Start`** under `Camera > Calibration > Extrinsic`.
    
    When calibration is completed, extrinsic parameters and the camera position will be displayed, and it will shows `Extrinsic  ☑Calibrated`.  
    
    !!! Tip "If it does not read the AR marker properly, try [If the marker cannot be read properly](#if-the-marker-cannot-be-read-properly)."
    
    ![](../../images/Camera-Calibration-Extrinsic-Execution-Aruco.gif){ loading=lazy }
   
=== "Diamond cluster method"
    - Place the images printed in [Prepare markers](../prepare-markers/#print-marker-for-extrinsic-parameter-calibration) section at a distance that fits in a frame of the camera. It does not have to be in the same plane. `diamondMarker0.png` will be the origin of the captured motion, so place this on the floor.  
    - In MocapForAll, select **`Diamond cluster`** in `Settings > Calibration > Extrinsic calibration method`.  
    - Click **`Scan markers`** button under `Camera > Calibration > Extrinsic` in one of the cameras. Take pictures of `diamondMarker0.png` and one of the markers at the same time. After a while, the position of another marker will be fixed with `diamondMarker0.png` as the origin, and the marker will be displayed on the 3D viewport. 
    - Repeat the above step for markers whose positions have been fixed and markers whose positions have not been fixed, and click `Stop scanning` when the positions of all markers have been fixed.
    - Place the cameras where they can see at least one of the markers whose position is fixed. 
    - Click **`Start`** under `Camera > Calibration > Extrinsic`.
    
    When calibration is completed, extrinsic parameters and the camera position will be displayed, and it will shows `Extrinsic  ☑Calibrated`.  

    !!! Tip "If it does not read the AR marker properly, try [If the marker cannot be read properly](#if-the-marker-cannot-be-read-properly)."

    ![](../../images/Camera-Calibration-Extrinsic-Execution-Diamond.gif){ loading=lazy }

=== "Human motion method" 
    - Place the cameras so that at least two of them can see your whole body at the same time.
    - In MocapForAll, select **`Human motion`** in `Settings > Calibration > Extrinsic calibration method`.  
    - Select **`GPU_DirectML`** in `Settings > General > Run DNN on` if your hardware support it. (If you have already installed the `GPU_TensorRT` mode in the Appendix, you can also use it.）  
    - Select **`Speed`** in `Settings > General > Capture body` if your PC's performance is enough for it. (If you have already installed the `Precision` mode in the Appendix, you can also use it.）  
    - Click **`Start calibration` button at the top of the window**, and walk around on the floor where the cameras can see your whole body.  
    Your motion will be captured and the positions of your joints will be used to find the cameras relative positions.
    
    After all cameras' extrinsic parameters calibrated, click the **`Find Ground`** button at the top of the window and walk around in the same way as [If the marker cannot be read properly](#if-the-marker-cannot-be-read-properly) described below. This will determine the absolute position of the cameras.  
    
    ![](../../images/Camera-Calibration-Extrinsic-Execution-Human.gif){ loading=lazy }

### If the marker cannot be read properly
??? Tip "Method to place marker on the wall"

    Since the position of the marker will be the plane with zero height of the captured motion, it is basically recommended to place the marker on the floor, but it may be difficult to read the marker on the floor depending on the placement and specification of the camera.

    In that case, you can **hang the marker on the wall to calibrate the camera and adjust the floor level later** as follows:

    - Replace the word "on the floor" with "on the wall" and execute the calibration procedure.  
    - Select **`GPU_DirectML`** in `Settings > General > Run DNN on` if your hardware support it. (If you have already installed the `GPU_TensorRT` mode in the Appendix, you can also use it.）  
      Select **`Speed`** in `Settings > General > Capture body` if your PC's performance is enough for it. (If you have already installed the `Precision` mode in the Appendix, you can also use it.）  
    - Click the **`Find Ground`** button at the top of the window and walk around where at least 2 cameras can see your whole body. After a while, the position of the floor level will be adjusted automatically.  

    ![](../../images/Camera-Calibration-Extrinsic-Execution-FindGround.gif){ loading=lazy }

### Confirm the results

If you have input the correct marker size in [Prepare markers](../prepare-markers/#measure-the-marker-size) section, you can see the position of the camera in the 3D viewport.  
Use the WASD key and mouse drag to move the viewport on MocapForAll.  
<img src="../../../images/App-wasd.png" alt="App-wasd" style="zoom:50%;" />  

!!! Warning "Cameras may appear below the floor"
    In this case, the calibration has failed.

## Save and load the results
![](../../images/Camera-Calibration-Save.gif){ loading=lazy }

### For each camera 
After calibration is completed, save the calibration result of each camera by clicking **`Save`** under `Camera > Calibration > Intrinsic` and `Extrinsic`. The saved result can be loaded by clicking **`Load`** button.  

### For all cameras
You can save and load the whole camera setup by clicking **`Save All Cameras`** and **`Load All Cameras`** buttons.  

!!! Warning "Caution when saving all camera settings"
    The camera selection is saved as the index inside the combo box. If you remove cameras from your PC, the order of the cameras in the combo box will change and you will not be able to load the cameras properly.
