---
title: Export to shared memory
---

# Export motion to shared memory

You can export bone transform and facial expression raw data to shared memory.

## Settings to send data

- Turn on `Settings > Data export > Shared Memory > Export to shared memory`

!!! Info "Change the name of destination shared memory"
    Data will be written to the shared memory of the name specified in `Settings > Data export > Shared Memory > Names of shared memories`

## Format of output data

- The first 1 byte is a counter that is incremented by 1 each time the data is updated (after 255, it returns to 0).
- The next 4 bytes are the int type value which describes the length of the remaining data in bytes.
- The rest are array of 4-byte float values.

### Body

![](../../images/DataFormat-SharedMemory-Body.png){ loading=lazy }

### Hand

The orientation and position of 15 bones are exported in the similar format as the Body data. The arrangement of bones is as follows.

![](../../images/DataFormat-SharedMemory-Hand.png){ loading=lazy }

### Face

Only positions (no rotations) are exported for 468 face landmarks. The position is represented by a three-dimensional value with the XY coordinates in pixels in the camera image cropped to the area of the face and the Z coordinate of the same scale in the depth direction.

![](../../images/DataFormat-SharedMemory-Face1.png){ loading=lazy }

Enlarge the image below to see where each landmark corresponds to your face.

![](../../images/DataFormat-SharedMemory-Face.jpg){ loading=lazy }

### Eye

In the same format as the Face data, the positions of 5 points for the iris and 71 points for the eyelid are exported.

## Sample project

A sample project to read the transform data from shared memory with Unity and apply it to GameObjects is [available here](https://github.com/Akiya-Research-Institute/MocapForAll-SharedMemory-Plugin-for-Unity).
