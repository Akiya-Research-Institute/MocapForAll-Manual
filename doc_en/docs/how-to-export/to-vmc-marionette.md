---
title: Export to VMC marionette
---

# Export motion to apps which accept VMC protocol

You can send the captured motion to various applications via VMC protocol. The following are confirmed to work:

- Sending tracker to [VirtualMotionCapture](https://vmc.info/)
- Sending bones to [VSeeFace](https://www.vseeface.icu/), and receiving facial expression morphs from VSeeFace
- Sending bones and facial expression morphs to [EVMC4U](https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity)
- Sending bones and facial expression morphs to [VMC4UE](https://github.com/HAL9HARUKU/VMC4UE)
- Sending bones to [VMC4B](https://tonimono.booth.pm/items/3432915)

## Load VRM models

- Stop capturing
- Drag and drop the VRM file into the MocapForAll window

!!! Info "Notice"
    Load the same VRM model with the destination app.  

!!! Question "Direct or Indirect mode?"
    Try Direct mode first. Indirect mode is only for models which do not work with Direct mode properly.

![](../../images/Settings-General-Character-VRM.gif){ loading=lazy }

## Settings to send data

![](../../images/Settings-DataExport-VMC.png){ loading=lazy }

- Set `Settings > Data export > Destination IP address for VMT and VMC` as follows:
    - If the destination is the same PC: `127.0.0.1`
    - If the destination is another PC: `IP address of the destination PC`
        - You can check it by typing `ipconfig /all` in the command prompt
- Turn on `Settings > Data export > VMC protocol > Send bones`
- Set the port of `Settings> Data export> VMC protocol> Send tracking points` according to the destination port.

!!! Info "Advanced setting: `As trackers`"
    If you want to send as trackers (/VMC/Ext/Tra/Pos), not bones (/VMC/Ext/Bone/Pos), set the following:  
    (For example, this setting is required to send data to VirtualMotionCapture.)

    - Turn on `Settings > Data export > VMC protocol > Send bones > As trackers (/VMC/Ext/Tra/Pos)`

## Settings to receive and send facial expressions

To receive facial expression morph data, set as follows:

- Turn on `Settings > Data export > VMC protocol > Receive facial morphs`
- Set the port of `Settings > Data export > VMC protocol > Receive facial morphs` according to the destination port specified by the source app.
- Set `Settings > Data export > VMC protocol > Receive facial morphs > From other device` as follows:
    - If the source app is running on the same PC: `Off`
    - If the source app is running on other device: `On`

The received facial expression morph data will be sent as it is if [Settings to send data](#settings-to-send-data) is set.