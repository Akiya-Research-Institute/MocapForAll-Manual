---
title: Export to BVH files
---

# Export motion to BVH files

![](../../images/Settings-DataExport-BVH.gif){ loading=lazy }

- Click `Stop capture`.
- Drag and drop the VRM file into the MocapForAll window to load a VRM model.
- Turn on `Settings > Data export > Record to BVH file`
    - `Settings  > General > Character` will be automatically set to `VRM runtime load`
- Click `Start capture` to start saving the data in BVH format.
- Click `Stop capture` to generate the final BVH file.
    - In the case of the free trial version, a BVH file will be automatically generated after 300 frames have passed, and data saving will be stopped.

!!! Info "Bone structure is based on VRM"
    After retargeting the animation to the VRM model on MocapForAll, the animation is exported in BVH format.  
    Therefore, when exporting data in BVH format, it automatically switches to the mode that uses VRM.  

!!! Info "If you do not own VRM models"
    Please select `VRM runtime load` in `Settings > General > Character` without actually loading a model.  
    A dummy VRM model runs in background.  

!!! Info "The unit of length is meters"
    The unit of bone length in the generated BVH file is meters. Set the appropriate unit in the application which loads the BVH file.