# computer-vision-hackpack

The task we have chosen is building an image classifier that recognises the party-parrot and party-blob slackmojis from scratch! This includes the process from building the dataset to having a final model that can make predictions. When you’re building models for new tasks, oftentimes there aren't any pre-existing datasets that are available for use. If you come up with an idea that requires a classification problem that hasn't been adressed before, this hackpack can help you start out! We take the example of parrot-blob classification but any of these steps can be subsituted with your own classes. 

Pre-requisites:
1. How to use a jupyter notebook
2. Basics of python

This hackpack doesn't cover the fundamentals of deep learning, but is just something to give you a start in creating your model with libraries such as tensorflow as well as understanding how to create a project for your own specific tasks. We're going to be classifying two really fun slackmojis- the party-parrot and party-blob! 

![kernel-popcorn (2)](https://user-images.githubusercontent.com/93958307/210043334-f0b32ae4-bf38-4960-af0c-39b804c3076f.jpg)

## Project Setup and Installations

On your computer, create a folder titled 'computer_vision_hackpack'. Within that, create two folders- 'blob-parrot' and 'augmented_data'. Within each of these folders, create two more folders titled- 'parrot' and 'blob'. 

Use the environment.yml file to install dependencies. 
```conda env create --file=environment.yml```

If you are an M1/M2 mac user, there may be some issues you face while installing tensorflow. I followed this video's instructions which worked flawlessly- https://www.youtube.com/watch?v=_CO-ND1FTOU (your mac may be running the intel chip instead of the M1 which would allow you to take advantage of the GPU!)

## Making the dataset

For supervised machine learning, forming a dataset is one of the most crucial steps. Your classifier is as good as its data. If you are interested in just learning about image classification and tinkering with a model, there are several public datasets available to do so including MNIST, cat-dog classification, imagenet, etc. There are a ton of challenges on Kaggle, and many datasets on platforms such as UCI Machine Learning Repository, Google’s Datasets Search Engine, and Lionbridge AI to name a few. 

However, if you wish to tackle a specific problem, you will need to collect data for it if there isn't a pre-existing public dataset that has the data you require. There are a few ways to go about this to build an image classification dataset: 
1. Web Scraping- You can read about web scraping online. Some tools that are good Scrapy, ProWebScraper, and ScraperAPI. 
2. Synthetic Datasets
3. Manual Data Generation- Build the dataset by manual collection! Sometimes you've just gotta... The most popular platform for crowdsourcing is Amazon Mechanical Turk where tasks are assigned to human workers, who are compensated for finishing the tasks.

Once you've found a way to best collect data, it's time to setup your folders and begin adding that data to your dataset! In this hackpack, we organize the data by having a single folder titled "blob-parrot" containing two seperate folders for each class (categories you are classifying)- "parrot" and "blob". It is also good practice to have the split of data be equal for each of the classes (i.e., approximately equal number of images for each class). 

For this hackpack, we collected the data from google images to curate our dataset. If you'd like to do so as well, go for it! Make sure to have all your images be in .jpg form. It can be a bit of a tedious process so you can also download our dataset here- //add link//. 

## Augmentation 

As can be seen, this is a very small dataset with only around 50 images in each class (this is a very very small dataset). To increase the size of our dataset, we perform something called 'Data Augmentation'. Data augmentation is a technique used to artificially increase the size of a dataset by generating new, modified versions of existing data samples, helping us increase the size and diversity of our dataset. This technique addresses the problem of overfitting, which occurs when a model is trained on a small, limited dataset and is not able to generalize well. This is an example of our augmented data:

![dataaug_example](https://user-images.githubusercontent.com/93958307/210051307-2c525e9c-6044-411e-8c05-a3672653ddd2.png)

We augment the data with two parametes: rotation_range=90, horizontal_flip=True. Follow the code in data-processing.ipynb to see this in action! 

## Pre-processing 

We make them unifrom size... 
Go over processing it and then saving it into a pickle file. 

## The model

The model is created using the Sequential class from the Keras library, which allows the layers to be added one by one in a linear fashion. The input to the model is a set of images represented as a 4D array (X), with dimensions corresponding to the number of samples, height, width, and channels (color depth). Our model architecture is as follows:

![blob-parrot-cnn (2)](https://user-images.githubusercontent.com/93958307/210061992-e0e599ea-cbe4-43c2-bc83-066ba2ba0a9a.png)

Some details of the architecture are:
1. Conv2D: This is a 2D convolutional layer that applies a set of filters to the input data, resulting in a set of feature maps. The filters are trained to recognize certain patterns or features in the input data, and each filter produces one feature map. The size of the filters and the number of filters in the layer are determined by the layer_size variable. The (3, 3) tuple specifies the size of the filters.
2. Activation: This layer applies an activation function to the output of the preceding layer. In this case, the activation function is the ReLU (Rectified Linear Unit) function, which outputs the input value if it is positive, and 0 if it is negative. This helps the model learn non-linear relationships in the data.
3. MaxPooling2D: This is a 2D pooling layer that downsamples the input data by taking the maximum value in each pooling window and creating a new feature map from it. The (2, 2) tuple specifies the size of the pooling window. Pooling helps reduce the size of the data, which can make the model more efficient and reduce the risk of overfitting.
4. Flatten: This layer flattens the output of the preceding layers into a single 1D vector, which is then input into the dense layers.
5. Dense: This is a fully connected (dense) layer that applies a set of weights to the input data and produces a set of outputs. The number of weights and outputs is determined by the layer_size variable.
6. Activation: This layer applies the sigmoid activation function to the output of the preceding layer. The sigmoid function maps the output to a value between 0 and 1, which can be interpreted as a probability.

Furthermore, the follwing are used:
1. model.compile: This function configures the model's learning process, setting the loss function, optimization algorithm, and performance metrics to be used during training. In this case, the loss function is binary cross-entropy, which is commonly used for binary classification tasks, and the optimization algorithm is Adam. The model will also be evaluated using the accuracy metric.
2. model.fit: This function trains the model on the given data (X and y) using the configuration specified in model.compile. The model is trained using mini-batch gradient descent with a batch size of 32 and for 25 epochs. During training, the model's performance on a validation set (a subset of the training data) is monitored using the TensorBoard callback, which logs the model's performance and allows it to be visualized using TensorFlow's visualization tool.
3. model.summary: This function outputs a summary of all the layers in our model! 

## Using the model to make predictions

We save the model using the .save method. You will now have a folder in your project called 'Parrot-Blob-CNN.model'. You can now load this model to be used without having to train it again! The method for using it to predict on images can be seen in the .ipynb file in the repo. As can be seen, any image that we wish to put into our model needs to be prepared in a certain format which is covered by the 'prepare' function. Furthermoe, the model outputs a probability score and not a class. Hence, the 'predict' function converts this probability into either 'parrot' or 'blob'.  

## Improvements

This is a relatively optimistic expectation...  

Changing the model
Using transfer learning
Get more data!!! 
For this problem specifically, it is a relatively easy classification task since the images do not have much variation and hence do not require too much diversity in its dataset. However, for many other problems, you need to be sure to check if you are covering all the edge cases and broadening your datset as much as possible to get the most accurate model! 

# About HackPacks 🌲

HackPacks are built by the TreeHacks team to help hackers build great projects at our hackathon that happens every February at Stanford. We believe that everyone of every skill level can learn to make awesome things, and this is one way we help facilitate hacker culture. We open source our hackpacks (along with our internal tech) so everyone can learn from and use them! Feel free to use these at your own hackathons, workshops, and anything else that promotes building :)

If you're interested in attending TreeHacks, you can apply on our website during the application period.

You can follow us here on GitHub to see all the open source work we do (we love issues, contributions, and feedback of any kind!), and on Facebook, Twitter, and Instagram to see general updates from TreeHacks.
