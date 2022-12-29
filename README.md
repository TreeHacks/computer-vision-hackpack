# computer-vision-hackpack

What you'll learn:
1. Making a dataset
2. Processing dataset
3. Choosing architecture
4. ...

Pre-requisites:
1. How to use a jupyter notebook
2. 

+ add something to use it w a flask app 

This doesn't cover the details of... + the math behind it and stuff. 

The project- We're going to make a model that classifies popcorn and unpopped popcorn kernels:

Pic of each one 

## Installations

go over installing tensorflow + how there is indeed a problem w mac m1/m2. 

## The dataset 

// taking pictures
// Putting it into labelled folders
// making a pickle file

... 

For several tasks, there are datasets that already exist. However, for our chosen problem there isn't a dataset that has already been made so we're going to make our own! There are a few ways to go about this:
1. Scrapping images
2. Taking images
3. etc. put tools here

The best way to organize your data is to have a folder containing seperate folders for each of your classes (categories you are classifying). It is also good practice to have the split of data be equal for each of the classes (i.e., approximately equal number of images for each class). For our specific task, it is a binary classification problem which means that we only have two classes- Popcorn and Kernel. Hence, our data looks like this:

Download it here! 

#### Augmentation 

As can be seen, this is a very small dataset with only ___ number of images in each class. To increase the size of our dataset, we perform something called 'Data Augmentation'. Follow the ... 

Image of the augmented data...

Go over code of augmenting and saving it. Show that it will create a new folder called 'augmented_images' with each of the classes. 

#### Pre-processing 

Go over processing it and then saving it into a pickle file. 

## The model


## Using the model to make predictions

## Improvements

Changing the model
Using transfer learning

make sure you have python installed correctly + arm stuff and etc.
install tensorflow 

then etc. 
