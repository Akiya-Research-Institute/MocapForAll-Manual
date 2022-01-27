# Get cameras
You need webcams that can be connected to the PC in which MocapForAll installed.  
To use smartphones or tablets, use apps that turns your smartphones or tablets into webcams, such as [DroidCam](https://www.dev47apps.com/) or [Iriun](https://iriun.com/).   

## What kind of camera should I use?
### Webcams or smartphones
There is no quantitative data on which is more accurate when using a webcam or smartphone. It is best to actually plug and test your device.  
When using battery-powered equipment such as smartphones, be careful not to run out of battery.  
For your information, all official videos of MocapForAll are taken using wirelessly connected smartphone and tablet, except those that state wired cameras are used.

### Wired or wireless
The delay of motion capture by MocapForAll mainly consists of the time it takes for the camera image to be transferred to the PC.
Wired cameras often have less delay than wireless cameras. Also, keep in mind that delays tend to be large when using apps that turn smartphones into webcams or virtual cameras.
To use with VR devices, it is recommended to make the delay as small as possible.

### FOV, frame rate, image size
- The wider the **FOV**, the wider the space for motion capture. However, MocapForAll calculates the 3D position with a simple pinhole camera model, so if the image is distorted like a fisheye lens, the movement cannot be captured correctly. A camera with low distortion and a wide FOV is most suitable. Some people use 120 degree FOV cameras, and it seems they work very well.  
- If the **frame rate** is low, that value can be a bottleneck in the frame rate of the capture. Considering the performance of your PC, get cameras with a higher frame rate than that of your desired capture result. The performance of MocapForAll itself is, using GTX1080Ti for example, about 60fps when MocapForAll is operated alone, and about 20fps when used with VR at the same time.   
- **Image size** does not contribute much to the precision of the capture of body movement. About 640x480 pixels is enough. This is due to the pipeline of the image processing: firstly the image is cropped around the person and then reduced to, for example, 256x256 pixel to input to the AI. However, when capturing hands and faces, the same processing is performed for small areas of hands and face, so the larger the image size (and resolution), the better the accuracy. We usually use cameras with image sizes around HD.

## Where should I put cameras?
Put cameras where they can see your whole body as well as the following conditions are satisfied:

### Vertical position: chest to eye level
It is recommended to place the camera at the height between your chest and your eyes.  
If the camera is looking up or down too much, the accuracy tends to be poor. 

### Horizontal position: 45° left and right from front
It is recommended to place the camera at 45 degree left and right from the front of the captured person.  
If the capture target and the two cameras are positioned in a straight line, the accuracy tend to be poor because the depth information is insufficient.  

This is an example of our camera placement:  

  ![](../images/Camera-Placing.png){ loading=lazy }

## Number of the cameras

By increasing the number of cameras, the occlusion is reduced, so it is expected to improve the accuracy. However, there is no quantitative data on this.    
Since the CPU / GPU usage increases almost in proportion to the number of cameras, increasing the number of cameras will reduce the frame rate of the capture depending on the performance of your PC.  
We recommend that you start with two cameras and consider adding more if you find that occlusion cause problems.  

（Examples: Comparison of 4 cameras vs 2 cameras）  
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Demonstration using 4 cameras. This app has no limit on the number of cameras. Keep in mind that CPU or GPU usage increases in proportion to the number of cameras.<br>↓ 2 cameras ↓<a href="https://t.co/x3ZmseEMpG">https://t.co/x3ZmseEMpG</a> <a href="https://t.co/kbUyE2ZHNm">pic.twitter.com/kbUyE2ZHNm</a></p>&mdash; 空き家総研VRラボ -Akiya Research Institute,VRlab- (@Akiya_Souken_VR) <a href="https://twitter.com/Akiya_Souken_VR/status/1397121512113459202?ref_src=twsrc%5Etfw">May 25, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>