# Adjust scales

![](../../images/Settings-Coordinates-Scales.png){ loading=lazy }

Click `Start capture` at the top of the window and let the cameras to see your whole body to capture your motion.
By observing the captured result, adjust the scales as shown below to animate the character properly.   

!!! Info "VR users can skip this"
    If you are using Virtual Motion Tracker and SteamVR, the scales will be adjusted in [Align coordinates of SteamVR and MocapForAll](../../../how-to-export/to-steamvr/#align-coordinates-of-steamvr-and-mocapforall) section described later, so you can skip this section.

!!! Question "Why there are 2 scales"
    Game characters generally have longer legs than real humans, so the scale is divided into ones for upper and lower body. (Therefore, the ratio of the upper body scale to the lower body scale depends on the character you want to apply.)
    
## Lower body scale

Affects to pelvis, hips, knees, feet, as well as the root position of the whole movement.

- If the character is always crunching, increase the value at `Settings > Coordinates > Scale > Lower body`.
- If the character is floating in the air, decrease the value at `Settings > Coordinates > Scale > Lower body`.

## Upper body scale

Affects to chest, neck, head, shoulders, elbows, hands, fingers.

- If the character's shoulder is always facing down,  increase the value at `Settings > Coordinates > Scale > Upper body`.
- If the character's shoulder is always facing up,  decrease the value at `Settings > Coordinates > Scale > Upper body`.