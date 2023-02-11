# Image inpainting over CIFAR-10
A repository containing the Deep Learning model developed for the Machine Learning course of the master's degree in Computer Science of the University of Bologna.

## Contents and project's instructions
The model, the training history, and its application to the test set are contained into the noteook. Its aim is just demonstrative. In particular the architecture and the loss function used for the model have been thought on the basis of the project's requirements and instructions:

> The purpose of this project is to build and train a neural network for image inpainting over the CIFAR-10 dataset.
Inpainting is a restauration process where damaged, deteriorated, or missing parts of an artwork are filled in to present a complete image.
In our case, we create the portion of the image to be filled in by cropping a fixed size rectangular area from CIFAR-10 images.
The network is supposed to take in input the masked image and fill in the missing part. The networks must be trained over the training set, and tested on the test set.
You can split the train set into a validation set, if you wish.
The metrics that will be used to evaluate you result is Mean Square Error.
