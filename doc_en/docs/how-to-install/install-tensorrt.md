# Install TensorRT

!!! Info "You can skip this page"
    If you are not going to use TensorRT, you can skip this page. 

This section is only for enthusiasts who want to improve performance even by 1ms/frame.  
(Using GTX1080Ti in our dev env, TensorRT has better performance than DirectML by 1ms/frame/camera in Precision mode, for example.)  
Requires an Nvidia GPU that supports CUDA, cuDNN, and TensorRT.    
Please note that the versions of cuDNN and TensorRT are different for RTX30** series and others as shown below.   

|              | Other than RTX30** series               | RTX30** series                             |
| ------------ | --------------------------------------- | ------------------------------------------ |
| **CUDA**     | 11.0.3                                  | 11.0.3                                     |
| **cuDNN**    | v8.0.2 (July 24th, 2020), for CUDA 11.0 | v8.0.5 (November 9th, 2020), for CUDA 11.0 |
| **TensorRT** | 7.1.3.4 for CUDA 11.0                   | 7.2.2.3 for CUDA 11.0                      |

!!! Note "Acknowledgements"
    The versions for RTX30** series were provided by [漆原 鎌足](https://twitter.com/kamatari_san/status/1435536643901902852) san. Thank you!

!!! Warning "For RTX2080Ti users"
    If you are using RTX2080Ti, you might need to use cuDNN v8.0.5. Please try various combinations.

!!! Warning "For RTX30** series users"
    For the RTX30** series, we only tested RTX3060Ti and RTX3070. Others are not tested.

From now on, we will only explain the case of **other than RTX30\*\* series**. If you are using RTX30\*\* series, please read the versions as appropriate.

1. Install [CUDA 11.0.3](https://developer.nvidia.com/cuda-11.0-update1-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exenetwork)   
    Please note that the installer may fail to install the NVIDIA driver. In that case, please install the latest NVIDIA driver manually.    
    ![](../images/Install-TensorRT-CUDA.png){ loading=lazy }
2. Download and unzip [cuDNN v8.0.2 (July 24th, 2020), for CUDA 11.0](https://developer.nvidia.com/rdp/cudnn-archive)  
    ![](../images/Install-TensorRT-cuDNN.png){ loading=lazy }
3. Overwrite the following folders  
    * C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\bin
    * C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\include
    * C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\lib  
    
    with unzipped  
    
    * cudnn-11.0-windows-x64-v8.0.2.39\cuda\bin
    * cudnn-11.0-windows-x64-v8.0.2.39\cuda\include
    * cudnn-11.0-windows-x64-v8.0.2.39\cuda\lib  
    
4. Add an environment variable "CUDNN_PATH", and set its value to "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0".  
5. Download and unzip [TensorRT7.1.3.4](https://developer.nvidia.com/nvidia-tensorrt-7x-download)
    Note that a Nvidia account is required.  
    ![](../images/Install-TensorRT.png){ loading=lazy }

6. Add the path of lib folder in that to the environment variable "PATH", for example "C:\Program Files\NVIDIA GPU Computing Toolkit\TensorRT-7.1.3.4\lib"  

7. Add an environment variable "ORT_TENSORRT_ENGINE_CACHE_ENABLE" and set its value to "1".  

8. Add an environment variable "ORT_TENSORRT_CACHE_PATH" and set its value to any path where you want to save the cache files, for example "C:\temp".  

    (For other options of TensorRT, see [the official documentation](https://www.onnxruntime.ai/docs/reference/execution-providers/TensorRT-ExecutionProvider.html#configuration-options))  
    (Your environment variables will be something like this)  
    ![Install-TensorRT-EnvironmentVariables](../images/Install-TensorRT-EnvironmentVariables.png){ loading=lazy }    
    ![Install-TensorRT-EnvironmentVariables2](../images/Install-TensorRT-EnvironmentVariables2.png){ loading=lazy }  
​    (Your environment variable "Path" will be something like this)  
    ![Install-TensorRT-EnvironmentVariables-Path](../images/Install-TensorRT-EnvironmentVariables-Path.png){ loading=lazy }  
