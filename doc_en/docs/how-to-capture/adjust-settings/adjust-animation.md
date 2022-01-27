# Adjust animation

![](../../images/Settings-AnimationPostProcess.png){ loading=lazy }  
The captured motion will be displayed on the screen after the following post processes.  

## Whether to force feet to be grounded 

There is a function to control the positions of the feet so that they do not float in the air or sink into the floor.

- If the **contact between feet and ground** is important to you, turn **on** `Settings > Animation Post Process > Force feet grouded`.
- If the **natural movement of the whole leg** is important to you, turn **off** `Settings > Animation Post Process > Force feet grouded`.  

!!! Info "VR users can skip this"
    Data **before** applying the above adjustment is exported when `Settings > Data export > VMT protocol > Send tracking points` is turned on.  
    In other words, **if you use with VMT and SteamVR, you do not need to care about this setting.**

!!! Failure "If the feet stick to the ground"
    The threshold of the distance between the foot and the ground to determine whether to apply this adjustment is automatically calculated using the value `Settings > Coordinates > Scale > Lower body`.  
    If [Prepare marker](../../calibrate-cameras/prepare-markers/#measure-the-marker-size) was not done properly and the scale of `Lower body` was too big, the character's feet may not be able to get off the ground at all. In that case, redo [Prepare marker](../../calibrate-cameras/prepare-markers/#measure-the-marker-size) and [Execute calibration](../../calibrate-cameras/execute-calibration/#get-extrinsic-parameters), or turn off `Force feet grounded`.  

## Adjust the smoothing

There is a function to smooth the captured motion.  
After applying this smoothing, data is exported externally.  

### Turn on/off the smoothing

If the application that receive the captured motion performs its own smoothing, you may want to turn off the smoothing on the MocapForAll.  
You can do it by turning off `Settings > Animation Post Process > Smoothing on body`, `Smoothing on finger` and `Smoothing on facial expression`.

### Adjust the smoothing intensity

You can change the intensity of the smoothing.

- Start the capture and observe the noise when standing upright without moving. If you want less noise, decrease the value of ***fc0***.  
- Next, move your body at a speed which is appropriate for your purpose. If the captured motion cannot keep up with your body, increase the value of ***Beta***.

!!! Question "How it works"

    [One euro filter](http://cristal.univ-lille.fr/~casiez/1euro/) is used for the smoothing. One euro filter is simply "low-pass filter whose cutoff frequency increases in proportion to speed". Normal low-pass filter cannot keep up with quick movements when trying to suppress jitter. On the other hand, one euro filter can **loosen noise suppression only for quick movements** to ensure tracking for them, as well as suppressing noise at low speeds in the same way as normal low-pass filter.  

    You can adjust the following 3 parameters:

    - *fc0*: Cutoff frequency at speed is zero. **The smaller this value, the less noise at low speeds.**
    - *Beta*: How much the cutoff frequency increases in proportion to the speed. **The higher this value, the quicker movement can be tracked.**
    - *fcv*: Cutoff frequency for speed. For speed, a normal lowpass filter with the cutoff frequency specified by this value is applied.