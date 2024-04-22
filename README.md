# Overview
This is a system that produces an image representing the Indian Sign Language alphabet for the given American Sign Language alphabet image. The working of the system is described as follows:
![image](https://github.com/YogitaGarani/Mudra-A-Translation-System-from-ASL-to-ISL/assets/142418313/7faa9ab0-40e0-4df8-87e5-4a2f77dd57a6)
The input ASL image is classified into it's representative alphabet class. This prediction is further used to retrieve the corresponding ISL image to that prediction.

# Datasets
## American Sign Language Dataset
The American Sign Language dataset used to implement the solution has meticulously and manually been curated.
It has been separated into directories representing each alphabet.
This dataset contains a total of 546 validated grayscale images.
All images have been resized to 224x224 pixels and pixel values normalized to [0, 1] for numerical stability and compatibility with pre-trained models. 
Data augmentation techniques like rotation, flipping, scaling, skewing, and brightness/contrast adjustments have been applied.

Here is a sample from our dataset - each image represents the same alphabet D but has been captured in different angles and with different lighting.
![image](https://github.com/YogitaGarani/Mudra-A-Translation-System-from-ASL-to-ISL/assets/142418313/3da792b5-d3be-434e-9803-d554524b3145)

A publicly available dataset for ASL images has also been implemented to fine-tune one model. This dataset contains 3000 images per alphabet and has been organized into dierectories for each alphabet.
It can be accessed here: https://www.kaggle.com/datasets/grassknoted/asl-alphabet
## Indian Sign Language Dataset
The Indian Sign Language dataset used to implement the solution has also meticulously and manually been curated.
It has been separated into directories representing each alphabet.
This dataset contains a total of 1170 validated grayscale images.
All images have been resized to 224x224 pixels and pixel values normalized to [0, 1] for numerical stability and compatibility with pre-trained models. 
Data augmentation techniques like rotation, flipping, scaling, skewing, and brightness/contrast adjustments have been applied.

Here is a sample from our ISL dataset. Each image represents the alphabet D but shows different brightness and contrast properties.
![image](https://github.com/YogitaGarani/Mudra-A-Translation-System-from-ASL-to-ISL/assets/142418313/012fbe23-28c1-493f-ba74-30ad96d69491)


# Models
The following models have beeen implemented to obtain predictions:
1) Xception Model BASE - fine-tuned on the curated ASL Dataset
2) ResNET Model BASE - fine-tuned on the curated ASL Dataset
3) Xception Model BASE - fine-tuned on the kaggle ASL Dataset
4) Custom CNN Classification Model - trained on the curated ASL Dataset

## Xception Model and ResNET Model Customization for fine-tuning
Additional Layers:
Following the base model, additional layers have been added to tailor the network for this classification task.
1) Batch Normalization: This layer helps stabilize and speed up training by normalizing previous layer.
2) Dense Layer (256 neurons, ReLU activation): This adds a fully connected neural network layer with 256 neurons, using ReLU activation to learn more complex patterns from the Xception model's features.
3) Dropout (50%): Dropout randomly drops 50% of connections between neurons during training, preventing overfitting by promoting more robust feature learning.
4) Output Layer: The final layer consists of a Dense layer with 26 neurons (one for each ASL class), using softmax activation to convert raw outputs into class probabilities.

## Custom CNN Classification Model
The model consists of the following layers:
1) Input layer: Accepts images of size 128 x 128
2) Convolution Layers: The model contains 2 2D Convolution Layers each with 32 kernels of size 3 x 3
3) Pooling Layers: The model contains 2 max-pooling layers, each one present after one convolutional layer.
4) BatchNormalization Layer: The output of the convolution is normalized.
5) Fully Connected Dense Layers: 3 FC layers with dropout applied to the 1st and 3rd layers. Each layer uses ‘relu’ activation.
6) Output Layer: The output layer uses ‘sigmoid’ activation and consists of 26 units.

# Results
Various metrics like accuracy, precision and recall have been used to evaluate the performance of the models. The following image shows the results obtained by all the models.
![image](https://github.com/YogitaGarani/Mudra-A-Translation-System-from-ASL-to-ISL/assets/142418313/8d0cd886-15c7-4343-b184-c8df8c501e80)
