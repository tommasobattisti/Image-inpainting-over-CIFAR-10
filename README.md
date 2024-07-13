# Image inpainting over CIFAR-10


[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/18n-dqxkuzpvocAZZqBeFlcgH6RLSVqnH)
[![DOI](https://zenodo.org/badge/600516016.svg)](https://zenodo.org/doi/10.5281/zenodo.12736943)

A repository containing the Deep Learning model developed for the Machine Learning course of the master's degree in Computer Science of the University of Bologna.

## Contents and project's instructions
The model, the training history, and its application to the test set are contained into the noteook. Its aim is just demonstrative. In particular the architecture and the loss function used for the model have been thought on the basis of the project's requirements and instructions:

> The purpose of this project is to build and train a neural network for image inpainting over the CIFAR-10 dataset.
Inpainting is a restauration process where damaged, deteriorated, or missing parts of an artwork are filled in to present a complete image.
In our case, we create the portion of the image to be filled in by cropping a fixed size rectangular area from CIFAR-10 images.
The network is supposed to take in input the masked image and fill in the missing part. The networks must be trained over the training set, and tested on the test set.
You can split the train set into a validation set, if you wish.
The metrics that will be used to evaluate you result is Mean Square Error.


## Premises
Images' values for each pixel is squashed withing the range [0, 1] before starting by means of the following lines of code, where at first the dataset is loaded.

```python
(x_train, y_train), (x_test, y_test) = cifar10.load_data()
x_train = (x_train/255.).astype(np.float32)
x_test = (x_test/255.).astype(np.float32)
```

The function accounting for the mask generation is the following one:
```python
def mask(X,coords):
  x0,y0,x1,y1 = coords
  X[:,x0:x1,y0:y1] = 0
  return X


masked_x_train = mask(np.copy(x_train),(2,16,30,30))
masked_x_test = mask(np.copy(x_test),(2,16,30,30))
```
The specific mask's dimension and position are the ones defined in the project's instructions.

> **Warning** </br> Be sure to re-train the model every time you decide to change the mask's dimension and/or position.

The function is executed before the training, meanining that the learning process depends in some way on it. However, it is still possible to change the coordinates in order to create different masks, but note that the results can vary a lot depending on the selected regions and the dimensions. 
_______________


**Further information about the model and the explaination of the decisions leading to the model's architecture are contained into the [notebook](https://github.com/tommasobattisti/Image-inpainting-over-CIFAR-10/blob/main/model_and_execution.ipynb).**
