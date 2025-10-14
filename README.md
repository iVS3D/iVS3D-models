# iVS3D-models

## Overview
This repository contains a selection of models to be used with iVS3D plugins such as Deep Visual Similarity or Semantic Segmentation. These models are a selection and there are many more neural network models available for use with our plugins, the ones uploaded here serve as an starting point and a reference on how to integrate your own models with our plugins.

## Usage
To use the models, download the files within the `neural_network_models` folder and place them in your iVS3D installation in the resources directory:
```
|-- iVS3D-core
|-- plugins
|   |-- libSemanticSegmentation.so
|   |-- libVisualSimilarity.so
|   |-- resources
|   |   |-- neural_network_models
|   |   |   |-- ImageEmbedding_CosPlace_ResNet18_32.onnx
|   |   |   |-- ImageEmbedding_EigenPlace_ResNet18_512.onnx
|   |   |   |-- Segmentation_ConvNeXt-base_Aerial.onnx
|   |   |   |-- Segmentation_ConvNeXt-base_Aerial.json
|   |-- ...
```

## Deep Visual Similarity
The models for the Deep Visual Similarity plugin follow the naming convention `ImageEmbedding_NAME_ARC_SIZE.onnx` where 
- `NAME` is the name of the method used for embedding
- `ARC` is the name of the network architecture, e.g. ResNet18
- `SIZE` is the dimension of the embedding vector, e.g. 32

These model are currently provided for use with Deep Visual Similarity:
- `ImageEmbedding_CosPlace_ResNet18_32.onnx` from [[1]](#1).
- `ImageEmbedding_EigenPlace_ResNet18_512.onnx` from [[2]](#2).

## Semantic Segmentation
The models for the Semantic Segmentation plugin follow the naming convention `Segmentation_ARC_USECASE.onnx` where 
- `ARC` is the name of the network architecture, e.g. ConvNeXt-base
- `USECASE` is a short description of the use case, e.g. Sky Segmentation or Aerial Segmentation

In addition to the onnx model, the class labels along with a color for visualization as well as mean and standard deviation for input normalization need to be provided with the model. This is done using a `json` file with the same name as the model: `Segmentation_ARC_USECASE.json`.

For reference, take a look at [Segmentation_Unet_Sky.json](neural_network_models/Segmentation_Unet_Sky.json). 
> Note that the mean and standard deviation values are are applied to inputs in range $[0, 255]$. The values in the original papers might be given in the range $[0, 1]$ and need to be converted accordingly.

These model are currently provided for use with Semantic Segmentation:
- `Segmentation_ConvNeXt-base_Aerial.onnx` and
- `Segmentation_BiseNetV2_Aerial.onnx` from [Raoul Saipt](https://github.com/ruelll)
- `Segmentation_Unet_Saliency_Map.onnx` from [[3]](#3) 
- `Segmentation_Unet_Sky.json` from [[4]](#4).

## References
<a id="1">[1]</a> 
Berton et al. (2022). 
Rethinking Visual Geo-Localization for Large-Scale Applications.
Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV), 2022(June), 4878-4888.

<a id="2">[2]</a> 
Berton et al. (2023). 
EigenPlaces: Training Viewpoint Robust Models for Visual Place Recognition.
Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV), 2023(Oktober), 11080-11090.

<a id="3">[3]</a> 
Qin et al. (2020). 
U2-Net: Going Deeper with Nested U-Structure for Salient Object Detection
Pattern Recognition, 107404.

<a id="4">[4]</a> 
Liba et al. (2020). 
Sky Optimization: Semantically Aware Image Processing of Skies in Low-Light Photography
Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition Workshops, 526-527.

## Contributors
Special thanks to [Raoul Saipt](https://github.com/ruelll) for contributing to iVS3D by training the neural network model used for segmentation.
