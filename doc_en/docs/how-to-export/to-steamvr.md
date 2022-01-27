---
title: Export to SteamVR
---

# Export motion to SteamVR

You can use captured motion as virtual trackers in SteamVR by using "[Virtual Motion Tracker](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/)"(VMT) created by gpsnmeajp.    

!!! Warning
    Please note that VMT is a separated program from MocapForAll.  
    DO NOT contact the author of VMT for any issues you encountered when using MocapForAll and VMT together.

## Install VMT

- [Download from here](https://github.com/KenjiAsaba/VirtualMotionTracker/releases).
- Follow the [setup procedure](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/setup/) of VMT.  

!!! Question "Which version of VMT should I use?"
    Use the special version of VMT modifed for MocapForAll to [align automatically the coordinates of SteamVR and MocapForAll](#align-coordinates-of-steamvr-and-mocapforall).  
    If you align them manually, you do not need to use that version. Use vmt_011 or above. vmt_013c is recommended.

!!! Info "If trackers don't work for your app"
    Some application requires [settings of controller binding](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/advanced/#how-to-set-the-controller-bainding).

!!! Info "If you have problems with VMT"
    First, see [trouble shooting page](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/trouble/).

## Settings to send data

![](../../images/Settings-DataExport-VMT-SteamVR.png){ loading=lazy }

- Set `Settings > Data export > Destination IP address for VMT and VMC` as follows:
    - If the destination is the same PC: `127.0.0.1`
    - If the destination is another PC: `IP address of the destination PC`
        - You can check it by typing `ipconfig /all` in the command prompt
        - By running MocapForAll and SteamVR on different PCs, you can offload the mocap calculation and play VR games comfortably.
- Turn on `Settings > Data export > VMT protocol > Send tracking points`
- Set the port of `Settings> Data export> VMT protocol> Send tracking points` to `39570`.
- Turn on the required parts under `Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent`.
    - For example, if you want to use it in VRChat, turn on `Pelvis` and `Feet`
    - You can adjust the offset of the virtual tracker position by clicking the `>` on the left side of each.

!!! Info "Advanced setting: `As relative position to HMD`"

    For the following settings, please decide on/off by your preference. We recommend that you try turning on first, and then try turning off if you are really serious about the motion.

    - `Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD`

        - When turned **off**, the actual tracking positions will be used as the positions of the virtual trackers.  
            - The delay of the movements of the virtual trackers with respect to the head-mounted display will be **visible as it is**.  
            (For example, when you start walking, it looks like only the head moves first and the rest moves later.)
            - You **need to adjust the scale and the positions properly** in [Align coordinates of SteamVR and MocapForAll](#Align-coordinates-of-SteamVR-and-MocapForAll) section described below.  
            (If the scale is not set properly, the horizontal position of the virtual trackers relative to the HMD shifts as you move in the room.)
        - When turned **on**, the relative positions of your head and the rest parts will be transformed to the relative positions of HMD and the virtual trackers.  
            - The delay of the movements of the virtual trackers with respect to the HMD will be **less noticeable**.  
            (For example, when you start walking, it looks like the rest part slides along with the head.)
            - You **do not need to input precise number to the scale, and do not need to input the positions** in [Align coordinates of SteamVR and MocapForAll](#Align-coordinates-of-SteamVR-and-MocapForAll) section described below.  

## Align coordinates of SteamVR and MocapForAll

The coordinate of the HMD tracked by SteamVR and the coordinate of the body positions tracked by MocapForAll do not match as they are. You need to align them manually or automatically.

=== "Align automatically"
    
    !!! Info "Prerequisite"
        As described in [Install VMT](#install-vmt) section, you need to install [the modified version of Virtual Motion Tracker for MocapForAll](https://github.com/KenjiAsaba/VirtualMotionTracker/releases).

    - Close application which uses port 39571 including VMT Manager.
    - Turn on `Settings > Data export > VMT protocol > Send tracking points`
    - Put on the head-mounted display and keep SteamVR running.
    - Stand in a position where HMD is tracked by SteamVR and your body is tracked by MocapForAll.
    - In MocapForAll, click `Align coord. To VR` at the top of the window.
    - Walk around. After a while, the value of `Settings > Coordinates` will be updated automatically, and the coordinates of SteamVR and MocapForAll will be aligned.

    ![](../../images/Settings-DataExport-VMT-SteamVR-Align.gif){ loading=lazy }  

=== "Align manually"
    - Preparation
        - Click `Start capture` at the top of the MocapForAll window to start motion capture
        - Put on your head-mounted display, quit apps running on SteamVR, including SteamVR Home, and make your virtual tracker visible on the SteamVR default screen.

    - Adjust the scale
        - In MocapForAll,
            - Turn on **`Head`** under `Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent`
            - Tunr **off** `Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD`
        - Set the values of `Settings > Coordinates > Scale > Upper body` and `Lower body` so that the height of your eye level matches the height of the `Head` virtual tracker. `Upper body` and `Lower body` scales should basically have the same value.
        
    - Adjust the orientation
        - In MocapForAll,
            - Turn on **`Feet`** under `Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent`
            - Tunr **on** `Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD`
        - Move your foot back and forth and set the value of `Settings > Coordinates > Coord. rotation` so that the direction of the movement of `Foot` virtual tracker matches the direction of the actual movement of your foot.
        
    - Adjust the position

        - In MocapForAll,
            - Turn on **`Feet`** under `Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent`
            - Tunr **off** `Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD`
    - Set the value of `Settings > Coordinates > Origin position` so that the position of your feet matches the position of the virtual tracker of `Feet`.