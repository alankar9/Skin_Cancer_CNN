# Detecting Melanoma with a CNN based model
> Building a CNN based model to accurately detect Melanoma, a type of skin cancer that can be deadly if not detected early. This model evaluates images and alert dermatologists about the presence of melanoma, and helps to reduce a lot of manual effort needed in diagnosis.


## Data information
> The dataset consists of 2357 images of malignant and benign oncological diseases, which were formed from the International Skin Imaging Collaboration (ISIC). All images were sorted according to the classification taken with ISIC, and all subsets were divided into the same number of images, with the exception of melanomas and moles, whose images are slightly dominant.

## The data set contains the following diseases:
- Actinic keratosis
- Basal cell carcinoma
- Dermatofibroma
- Melanoma
- Nevus
- Pigmented benign keratosis
- Seborrheic keratosis
- Squamous cell carcinoma
- Vascular lesion

## Technologies used
- google colab
- python
- tensorflow - 2.11.0

## Project Pipeline
### Data Reading/Data Understanding
Loaded the data in to google drive, and mounted the drive in colab.
Imported data from Train folder, which include 2357 images under 9 classes.
### Dataset Creation
Created train & validation dataset from the train directory with a batch size of 32 by resizing all images to 180*180.
### Dataset visualisation
Using matplotlib visualised images from all 9 classes.
### Model1 : Model Building & training on given data
Original images pixel has range of [0,255]. so we normalise the data and bring the range of [0,1] to fit our nerual network model.

An input network that takes in images of dimension 180 by 180 by 3, with a ReLU activation function.

Started with 2-dimensional convolution layer with 16 filters, where each filter size is 3x3. continued convolutions with 32, 64, and 128 lasyers by Maxpoolong at each layer.
- #### Conclusion
Compared accuracy, and loss from both training and validation sets. noticed an evidence of mode overfitting.
### Augmentation
To solve above problem, we will preprocess the images by rotating, cropping, translating, and zooming randomly.
we will also try drop out method in next model.
### Model2 : Model Building & trainingon augmented data
Applied random changes augmentaiton method on images.
this time dropped 16 layer convolutions, and added 128 layer convolution.
- #### Conclusion
the accuracy comparision between Train and Test data shows neither underfitting nor overfitting. However the maximum accuracy reached up to 0.46 which is indicates the model needs further improvement.
### Handling class imbalances
Class imbalance is found in the data. Out of 9 classes, 4 are dominating the count.
So we will increase each class count by adding 500 images.
### Model3 : Model Building & trainingon rectified class imbalance data
Build third model on rectified class imbalance data, and ran 30 epochs by dropping out the layers.
- #### Conclusion
after balancing the classes by adding 500 samples to each class, the model performed better.
However after 20 epochs there is no further improvement noticed. 20 epochs should be enough for the model
