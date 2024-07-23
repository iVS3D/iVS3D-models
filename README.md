# iVS3D-models

## Overview
This repository contains a selection of models to be used with iVS3D plugins such as Visual Similarity or Semantic Segmentation. These models are a selection and there are many more neural network models available for use with our plugins, the ones uploaded here serve as an starting point and a reference on how to integrate your own models with our plugins.

## Usage
To use the models, download the files within the `neural_network_models` folder and place them in your iVS3D installation in the resources directory:
```
|-- iVS3D-core
|-- plugins
|   |-- SemanticSegmentation.so
|   |-- VisualSimilarity.so
|   |-- resources
|   |   |-- neural_network_models
|   |   |   |-- ImageEmbedding_ResNet18_32_512x512.onnx
|   |   |   |-- Segmentation_ConvNeXt-base_Aerial_1024x1024.onnx
|   |   |   |-- Segmentation_ConvNeXt-base_Aerial_1024x1024.txt
|   |-- ...
```

## Visual Similarity
The models for the Visual Similarity plugin follow the naming convention `ImageEmbedding_ARC_SIZE_HEIGHTxWIDTH.onnx` where 
- `ARC` is the name of the network architecture, e.g. ResNet18
- `SIZE` is the dimension of the embedding vector, e.g. 32
- `WIDTH` and `HEIGHT` are the size of the input

## Semantic Segmentation
The models for the Semantic Segmentation plugin follow the naming convention `Segmentation_ARC_DATASET_HEIGHTxWIDTH.onnx` where 
- `ARC` is the name of the network architecture, e.g. ConvNeXt-base
- `DATASET` is the dataset used for training, e.g. Cityscapes or Aerial
- `WIDTH` and `HEIGHT` are the size of the input and output

In addition to the onnx model, the class labels along with a color for visualization need to be provided with the model. This is done using a `.txt` file with the same name as the model: `Segmentation_ARC_DATASET_HEIGHTxWIDTH.onnx`.  In this file, each row represents a class with the label and color being separated by a semicolon. The color is given as comma-separated RGB values in the range [0, 255]: 
```
Building; 120,120,120;
Road; 128,64,128;
Vegetation; 60,142,35;
Vehicle; 220,20,60;
```

## Contributors
Special thanks to [Raoul Saipt](https://github.com/ruelll) for contributing to iVS3D by training the neural network model used for segmentation.
