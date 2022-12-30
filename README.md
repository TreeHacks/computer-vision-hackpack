# computer-vision-hackpack

The task we have chosen is building an image classifier that recognises the party-parrot and party-blob slackmojis from scratch! This includes the process from building the dataset to having a final model/making a flask app. When you’re building models for new tasks, oftentimes there aren't any pre-existing datasets that are available for use. If you come up with an idea that requires a novel classification problem that hasn't been adressed before, this hackpack can help you start out! We take the example of parrot-blob classification but any of these steps can be subsituted with your own classes. 

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

![kernel-popcorn (1)](https://user-images.githubusercontent.com/93958307/210040449-33d31adc-2212-439f-9e55-4b62a9e5f4c6.jpg)

## Making the dataset

For supervised machine learning, forming a dataset is one of the most crucial steps. Your classifier is as good as its data. If you are interested in just learning about image classification and tinkering with a model, there are several public datasets available to do so including MNIST, cat-dog classification, imagenet, etc. There are a ton of challenges on Kaggle, and many datasets on platforms such as UCI Machine Learning Repository, Google’s Datasets Search Engine, and Lionbridge AI to name a few. 

However, if you wish to tackle a specific problem, you will need to collect data for it if there isn't a pre-existing public dataset that has the data you require. There are a few ways to go about this to build an image classification dataset: 
1. Web Scraping- You can read about web scraping online. Some tools that are good Scrapy, ProWebScraper, and ScraperAPI. 
2. Synthetic Datasets
3. Manual Data Generation- Build the dataset by manual collection! Sometimes you've just gotta... The most popular platform for crowdsourcing is Amazon Mechanical Turk where tasks are assigned to human workers, who are compensated for finishing the tasks.

Once you've found a way to best collect data, it's time to setup your folders and begin adding that data to your dataset! In this hackpack, we organize the data by having a single folder titled "parrot-blob-data" containing two seperate folders for each class (categories you are classifying)- "parrot" and "blob". It is also good practice to have the split of data be equal for each of the classes (i.e., approximately equal number of images for each class). Our folder structure looks like this:

![folderstruc](https://user-images.githubusercontent.com/93958307/210040804-be1c1658-2e75-458e-95b0-e86031e94342.gif)

For this hackpack, we collected the data from google images to curate our dataset. If you'd like to do so as well, go for it! It can be a bit of a tedious process so you can also download our dataset here- //add link//. 

## Installations

go over installing tensorflow + how there is indeed a problem w mac m1/m2. 
make sure you have python installed correctly + arm stuff and etc.
install tensorflow 

## Augmentation 

As can be seen, this is a very small dataset with only ___ number of images in each class. To increase the size of our dataset, we perform something called 'Data Augmentation'. Follow the ... 

Image of the augmented data...

Go over code of augmenting and saving it. Show that it will create a new folder called 'augmented_images' with each of the classes. 

#### Pre-processing 

Go over processing it and then saving it into a pickle file. 

## The model


## Using the model to make predictions

## Improvements

This is a relatively optimistic expectation...  

Changing the model
Using transfer learning
