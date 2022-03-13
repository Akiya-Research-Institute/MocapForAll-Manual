---
title: Export to FBX files
---

# Export motion to FBX files

- Turn on `Settings > Data export > Record to FBX file`
    - `Settings  > General > Character` will be automatically set to `UE Mannequin`
- Click `Start capture` to start saving the data in FBX format.
- Click `Stop capture` to generate the final FBX file.
    - In the case of the free trial version, a FBX file will be automatically generated after 300 frames have passed, and data saving will be stopped.

!!! Info "Bone structure is based on UE Mannequin"
    After retargeting the animation to the UE Mannequin model on MocapForAll, the animation is exported in FBX format.  
    Therefore, when exporting data in FBX format, it automatically switches to the UE Mannequin model.  

!!! Info "Animation is baked at fixed framerate of 25fps"
    After baking the animation at fixed framerate of 25fps on MocapForAll, the animation is exported in FBX format.  

!!! Warning "No facial expression exported"
    Facial expressions are not supported to export.
