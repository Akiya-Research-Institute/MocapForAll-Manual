# Optimize performance 

Setup to reduce the CPU / GPU usage according to your environment and purpose.

![](../../images/Settings-General+Performance.png){ loading=lazy }

## Check the frame rate

Turn on `Settings > Performance > Show frame rate` to display current frame rate at the bottom of the window.

## Use GPU

MocapForAll uses AI to estimate a person's pose. AI calculations are often faster on the GPU than on the CPU.  
If you have a GPU, it is highly recommended to select **`GPU_DriectML`** from `Settings > General > Run DNN on`.

!!! Tip "Select from multiple GPUs"
    If you have multiple GPUs, you can also choose which GPU to use by `Settings > General > Run DNN on > GPU`.

!!! Question "Should I use TensorRT?"
    When using a GPU, you have two options, `GPU_DriectML` or `GPU_TensorRT`.  
    TensorRT is difficult to install, takes a long time to load, and has little reward. So, it is recommended to use `GPU_DriectML` in many cases.

    - GPU_DriectML:  
      DirectML provides GPU acceleration on DirectX 12 capable GPUs. Examples of compatible hardware include:
        - NVIDIA Kepler (GTX 600 series) and above
        - AMD GCN 1st Gen (Radeon HD 7000 series) and above

    - GPU_TensorRT:  
      TensorRT provides GPU acceleration on supported NVIDIA GPUs.
      To use this, you need to [install CUDA, cuDNN, TensorRT](../../../how-to-install/install-tensorrt), and [`Appendix4_TensorRT_mode`](../../../how-to-install/install-mocapforall).

## Select capturing mode

From `Settings > General > Capture body`, you can choose what to prioritize.

- In many cases, **`Speed`** is recommended.
- `Speed+` is recommended when using a PC with low performance such as a laptop PC or when using together with a very heavy VR application.  
- Use `Precision` mode when you want to capture motion precisely such as for movie production. You need to install [`Appendix1_Precision_mode`](../../../how-to-install/install-mocapforall).

## Reduce drawing

With the following settings, you can reduce the drawing on MocapForAll and reduce the CPU / GPU usage.

- Select **`Empty`** character in `Settings > General > Character`.
- Select **`Minimum`** map in `Settings > General > Map`.
- Set small value (30% for example) and turn **on** `Settings > Performance > Set screen percentage to`,  
  or turn **off** `Settings > Performance > Render the viewport`

## Limit the frame rate

Set the target frame rate (30FPS for example) and turn **on** `Settings > Performance > Limit framerate to:`.  
MocapForAll runs up to this frame rate.