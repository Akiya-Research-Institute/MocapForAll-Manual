---
title: Export to VRChat
---

# Export to VRChat

You can export joint positions as [OSC Tracker](https://docs.vrchat.com/docs/osc-trackers) for full-body tracking in VRChat.

!!! Warning "OSC Tracker is a beta feature"
    As of February 1, 2023, OSC Tracker is not an officially released feature of VRChat and is not guaranteed to work properly.  
    Please see the VRChat documentation for more information.  
    Reference: [OSC Overview](https://docs.vrchat.com/docs/osc-overview)

## Basic settings

![](../../images/Settings-VRChatOSC.png){ loading=lazy }

- Turn on `Settings > Data export > VRChat OSC (β)` and set `Dest. IP address` as follows:
    - If the destination is the same PC: `127.0.0.1`
    - If the destination is another device (for example, Quest 2): `IP address of the destination PC`

## Alignment on VRChat

As described in [VRChat's documentation here](https://docs.vrchat.com/docs/osc-trackers#auto-center-osc-trackers), you can press `Auto-center OSC Trackers` to automatically align the tracking spaces of VRChat and MocapForAll.  
Note that this button only appears when VRChat is receiving data via OSC.

## Select joints

- By turning on/off each joint under `Settings > Data export > VRChat OSC (β)`, you can select the joints to be sent.
- Input `Tracker index` for each joint.

!!! Tip "Move relative to the head"
    If "Tracker index" is set to "0", the position of that joint is sent as "/tracking/trackers/head".  
    (By default, index=0 is set for the head joint.)  
    This is used when you want to move each joint relative to the head-mounted display.

    - With this feature, the relative position of each joint to the head in MocapForAll is converted to the relative position of each tracker to the head-mounted display in VRChat.  
      The delay of the movements of the virtual trackers with respect to the HMD will be **less noticeable**.  
      (For example, when you start walking, it looks like the rest part slides along with the head.)

    - If this feature is not used, the actual tracking position of each joint is used as the virtual tracker position.
      The delay of the movements of the virtual trackers with respect to the head-mounted display will be **visible as it is**.  
      (For example, when you start walking, it looks like only the head moves first and the rest moves later.)

    Note that this function will also automatically align the orientation of the VRChat and MocapForAll tracking coordinates based on the orientation of the head.  
    For this to work properly, you must specify Z=90 as the **orientation offset** for MocapForAll's head joint.  
    This value is already specified by default.

    ![](../../images/Settings-VRChatOSC-Head.png){ loading=lazy }

    See [VRChat's documentation here](https://docs.vrchat.com/docs/osc-trackers#receiving-head-data) for more information.