# Blood Cell Detection Model
Ready to deploy blood cell detection model for NVIDIA Jetson platform on DeepStream SDK. Trained with using TAO Toolkit based on DetectNet V2 pre-trained model. The model can detect RBCs and WBCs from peripheral blood smear.

## Prerequisities

- NVIDIA Jetson Developer Kits or Production Module Systems
- CSI Camera, USB Camera or h264 Encoded Video
- Ubuntu 18.04 L4T
- NVIDIA JetPack SDK 4.6.1
- NVIDIA DeepStream SDK 6.0.1

## Dataset
I used [blood cell detection dataset]() which I collected and annotated when I was in medical school. Visit the dataset repository for further information.

## Example Usage
1. Be sure that you properly installed JetPack SDK 4.6.1.
2. Install NVIDIA DeepStream SDK 6.0.1.
3. Clone [DeepStream TAO Apps](https://github.com/NVIDIA-AI-IOT/deepstream_tao_apps/tree/release/tao3.0_ds6.0.1) repository. *Notice that we cloned the branch for DeepStream 6.0.1 version.* an

```
git clone -b release/tao3.0_ds6.0.1 https://github.com/NVIDIA-AI-IOT/deepstream_tao_apps/
```

4. Open *deepstream_tao_apps* directory, set CUDA version variable and compile.

```
cd deepstream_tao_apps
export CUDA_VER=xy.z
make
```

5. Clone *blood-cell-detection-model* repository.

```
git clone https://github.com/draaslan/blood-cell-detection-model
```


6. Run *ds-tao-detection* app with config and test video. *This process can be take a while.*

```
./apps/tao_detection/d-tao-detection -d \
    -c apps/blood-cell-detection-model/inference_config.txt \
    -i apps/blood-cell-detection-model/test.h264 
```

7. Model output will be saved as h624 format and inference result will be open on a window.

## Future Work
- Add video and image demonstration.
- Train model using more data with augmentation.
- Improve inference config.
- Containerize full application.

## Licence
See LICENSE for details.