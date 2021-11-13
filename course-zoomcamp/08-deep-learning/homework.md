## Homework

### Dataset

In this homework, we'll build a model for predicting if we have an image of a dog or a cat. For this,
we will use the "Dogs & Cats" dataset that can be downloaded from [Kaggle](https://www.kaggle.com/c/dogs-vs-cats/data). 

You need to download the `train.zip` file.

If you have troubles downloading from Kaggle, use [this link](https://github.com/alexeygrigorev/large-datasets/releases/download/dogs-cats/train.zip) instead:

```bash
wget https://github.com/alexeygrigorev/large-datasets/releases/download/dogs-cats/train.zip
```

In the lectures we saw how to use a pre-trained neural network. In the homework, we'll train a much smaller model from scratch. 

**Note:** You don't need a computer with a GPU for this homework. A laptop or any personal computer should be sufficient. 


### Data Preparation

The dataset contains 12,500 images of cats and 12,500 images of dogs. 

Now we need to split this data into train and validation

* Create a `train` and `validation` folders
* In each folder, create `cats` and `dogs` folders
* Move the first 10,000 images to the train folder (from 0 to 9999) for boths cats and dogs - and put them in respective folders
* Move the remaining 2,500 images to the validation folder (from 10000 to 12499)

You can do this manually or with Python (check `os` and `shutil` packages).


### Model

For this homework we will use Convolutional Neural Network (CNN. Like in the lectures, we'll use Keras.

You need to develop the model with following structure:

* The shape for input should be `(150, 150, 3)`
* Next, create a covolutional layer ([`Conv2D`](https://keras.io/api/layers/convolution_layers/convolution2d/)):
    * Use 32 filters
    * Kernel size should be `(3, 3)` (that's the size of the filter)
    * Use `'relu'` as activation 
* Reduce the size of the feature map with max pooling ([`MaxPooling2D`](https://keras.io/api/layers/pooling_layers/max_pooling2d/))
    * Set the pooling size to `(2, 2)`
* Turn the multi-dimensional result into vectors using a [`Flatten`](https://keras.io/api/layers/reshaping_layers/flatten/) layer
* Next, add a `Dense` layer with 64 neurons and `'relu'` activation
* Finally, create the `Dense` layer with 1 neuron - this will be the output

As optimizer use [`SGD`](https://keras.io/api/optimizers/sgd/) with the following parameters:

* `SGD(lr=0.002, momentum=0.8)`

TODO: add clarification for kernel size and max pooling


### Question 1

Since we have a binary classification problem, what is the best loss function for us?


### Question 2

What's the total number of parameters of the model? You can use the `summary` method for that. 


### Generators and Training

For the next two questions, create a data generator:

```python
ImageDataGenerator(rescale=1./255)
```

We don't need to do any additional pre-processing for the images.

For training use `.fit()` with the following params:

```python
model.fit(
    train_generator,
    steps_per_epoch=100,
    epochs=10,
    validation_data=validation_generator,
    validation_steps=50
)
```

### Question 3

What is the median of training accuracy for non-augmented model?

### Question 4

What is the standard deviation of training loss for non-augmented model?

### Data Augmentation

For the next two questions, we'll generate more data using data augmentations. 

Add the following augmentations to your data generator:

* `rotation_range=40,`
* `width_shift_range=0.2,`
* `height_shift_range=0.2,`
* `shear_range=0.2,`
* `zoom_range=0.2,`
* `horizontal_flip=True,`
* `fill_mode='nearest'`


### Question 5 

What is the mean of validation loss for augmented model?

### Question 6

What is the standard deviation of validation accuracy for augmented model?


## Submit the results

Submit your results here: **TODO**

If your answer doesn't match options exactly, select the closest one.


## Deadline

The deadline for submitting is 22 November, 17:00 CET. After that, the form will be closed.


## Nagivation

* [Machine Learning Zoomcamp course](../)
* [Session 8: Neural Networks and Deep Learning](./)
* Previous: [Explore more](14-explore-more.md)
