---
title: Export to game engines
---

# Export motion to game engines

## By receiver Plugins

Plugins for Unreal Engine 4, Unreal Engine 5, and Unity are available [here](https://booth.pm/ja/items/3026430). 

!!! Question "Does it use VMT?"
    These plugin uses VMT protocol for the communication, though they do not need Virtual Motion Tracker itself and SteamVR. 

### How to use Unreal Engine plugin
- [Manual of the receiver plugin for UE4](https://github.com/Akiya-Research-Institute/MocapForAll-Receiver-Plugin-for-UE4/wiki)
- [Manual of the receiver plugin for UE5](https://github.com/Akiya-Research-Institute/MocapForAll-Receiver-Plugin-for-UE5/wiki)

### How to use Unity plugin
- Set `Settings > Data export > Destination IP address for VMT and VMC` as follows
    - If the destination is the same PC: `127.0.0.1`
    - If the destination is another PC: `IP address of the destination PC`
        - You can check it by typing `ipconfig /all` in the command prompt
- Set one of the followings:
    - Turn on `Settings > Data export > VMT protocol > Send bones` and set the port according to the destination app
    - Turn on `Settings > Data export > VMT protocol > Send tracking points` and set the port according to the destination app

## By VMC4UE or EVMC4U
- As described in [To vmc marionette](../to-vmc-marionette) section, set MocapForAll settings.
- VMC4UE
    - As described in [official wiki page](https://github.com/HAL9HARUKU/VMC4UE/wiki#ue4-の使い方), set up UE4.
    - Click `Play` on UE4 editor. (You do not need last  "VirtualMotionCapture の使い方" section.)
- EVMC4U
    - Execute "0. Open Unity project" to "4. Let's play" of [ExternalReceiverPack setup in official wiki page](https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity/wiki/How-to-use#externalreceiverpack-easy)