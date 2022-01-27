---
title: Install MocapForAll
---

# How to install MocapForAll

You can install from Steam or BOOTH.

=== "From Steam"

    Demo and Paid versions are available.  
    Before purchase,  

    - Read and accept [the terms and conditions](https://store.steampowered.com//eula/1759710_eula_0).  
    - Try Demo version to check if the app works in your environment properly.  

    [Go to Steam store](https://store.steampowered.com/app/1759710/MocapForAll/){: .md-button .md-button--primary } 

    ??? Question "Demo version limitation"
        Demo version has limited functionality only for data export.

        - Data sending via VMT protocol and VMC protocol stops and restarts every 10 seconds.
        - Maximum frames in a BVH file is limited to 300.

    !!! Question "Appendix"

        All **Appendix** are installed automatically.  

        ??? Question "Appendix features"
            Appendix is originally the feature separated from the main program.  
            There are four Appendix as follows:

            - Appendix1：Precision mode  
            Adds "Precision" mode for precise motion capture. Since the CPU / GPU usage is very high, it is not recommended to use with VR apps at the same time.
            - Appendix2：HDRI maps  
            Adds maps which use HDRI images from [HDRI Haven](https://hdrihaven.com).  
            - Appendix3：MetaHuman character  
            Adds a character created by Epic games' MetaHuman Creator. Used to test motion capture on MocapForAll.
            - Appendix4：TensorRT mode (Deprecated)  
            Adds "GPU_TensorRT" mode which provides GPU acceleration on supported NVIDIA GPUs. As described below, CUDA, cuDNN, and TensorRT need to be installed. (In most cases, the standard "GPU_DirectML" mode will suffice.)
            This feature is deprecated because the improvement of performance is often very small or sometimes negative, and whether it works depends on the user's environment.

        If you want to use GPU acceleration by TensorRT, you need to manually [install CUDA, cuDNN, and TensorRT](../install-tensorrt).  

=== "From BOOTH"
    ## Download
    #### Free trial version

    [Download from BOOTH](https://akiya-souken.booth.pm/items/3026474){: .md-button .md-button--primary }  

    ??? Question "Free trial version limitation"
        Free trial version has limited functionality only for data export.

        - Data sending via VMT protocol and VMC protocol stops and restarts every 10 seconds.
        - Maximum frames in a BVH file is limited to 300.

    #### Paid version
    Before purchase,
    
    - Read and accept [the terms and conditions](https://vrlab.akiya-souken.co.jp/eula).  
    - It is required to try free trial version to check if the app works in your environment properly.  

    If you agree, you can get your purchase password from our HP and proceed to the purchase page at BOOTH.  

    [Our HP](https://vrlab.akiya-souken.co.jp/product#buy){: .md-button .md-button--primary }  

    ## Install
    You can install manually or by using network installer.  

    === "Manual install"

        #### Main files
        1. Download and unzip "MocapForAll_Full_vN.N.N.zip"
        2. Execute MocapForAll.exe in "MocapForAll_Full_vN.N.N" folder
        3. If the "UE4 Prerequisites" installation screen is displayed, install it.

        #### Appendix (Optional)

        If you do not need the functions in Appendix, you can skip this step.  

        ??? Question "Appendix features"
            Appendix is the feature separated from the main program.  
            There are four Appendix as follows:

            - Appendix1：Precision mode  
            Adds "Precision" mode for precise motion capture. Since the CPU / GPU usage is very high, it is not recommended to use with VR apps at the same time.
            - Appendix2：HDRI maps  
            Adds maps which use HDRI images from [HDRI Haven](https://hdrihaven.com).  
            - Appendix3：MetaHuman character  
            Adds a character created by Epic games' MetaHuman Creator. Used to test motion capture on MocapForAll.
            - Appendix4：TensorRT mode (Deprecated)  
            Adds "GPU_TensorRT" mode which provides GPU acceleration on supported NVIDIA GPUs. As described below, CUDA, cuDNN, and TensorRT need to be installed. (In most cases, the standard "GPU_DirectML" mode will suffice.)
            This feature is deprecated because the improvement of performance is often very small or sometimes negative, and whether it works depends on the user's environment.

        1. Download and unzip "AppendixN_xxxxx_yyyyy.zip".
        2. Overwrite "MocapForAll_Full_vN.N.N\MocapForAll" with "AppendixN_xxxxx_yyyyy\MocapForAll".
        3. If you install "Appendix4_TensorRT_mode", follow the [installation guide of TensorRT](../install-tensorrt).


    === "By Network Installer"
        1. Download and unzip "Network_Installer_-_MocapForAll_Full_vN.N.N.zip".

        2. Execute "Network_Installer_-_MocapForAll_Full_vN.N.N.exe".

        3. Select the Appendix you use.
        
            ??? Question "Appendix features"
                Appendix is the feature separated from the main program.  
                There are four Appendix as follows:

                - Appendix1：Precision mode  
                Adds "Precision" mode for precise motion capture. Since the CPU / GPU usage is very high, it is not recommended to use with VR apps at the same time.
                - Appendix2：HDRI maps  
                Adds maps which use HDRI images from [HDRI Haven](https://hdrihaven.com).  
                - Appendix3：MetaHuman character  
                Adds a character created by Epic games' MetaHuman Creator. Used to test motion capture on MocapForAll.
                - Appendix4：TensorRT mode (Deprecated)  
                Adds "GPU_TensorRT" mode which provides GPU acceleration on supported NVIDIA GPUs. As described below, CUDA, cuDNN, and TensorRT need to be installed. (In most cases, the standard "GPU_DirectML" mode will suffice.)  
                This feature is deprecated because the improvement of performance is often very small or sometimes negative, and whether it works depends on the user's environment.  
                To use "Appendix4_TensorRT_mode", see [Installation of TensorRT](../install-tensorrt) and install the required software.

        4. Run MocapForAll from the Start menu or MocapForAll.exe in the installation path.

        5. If the "UE4 Prerequisites" installation screen is displayed, install it.


    ## Update

    You can update manually or by using network installer.

    === "Manual update"

        1. Download and unzip "MocapForAll_Full_vN.N.N.zip".
        2. Overwrite the old version of "MocapForAll_Full_vM.M.M" folder with new "MocapForAll_Full_vN.N.N" folder.

    === "By Network Installer"

        Same as installation.

        !!! Tip "Reduce donwload size"
            If you wan to reduce the data size to download, select only "Main Files" in "Select Components" screen without selecting "Appendix" and execute installation.   
            Since the installer does not delete files, the previous Appendix remains .  
            After that, Appendix will be treated as not installed on the "Select Components" screen of the installer, but this cause no problem.