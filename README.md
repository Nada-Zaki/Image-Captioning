# Overview

Image captioning is a new technology that combines RNN text generation with the computer vision powers of a convolutional neural network.

In this repository, we will use LSTM and CNN to create a basic image captioning system.

we will work on [Flicker30k image dataset](https://www.kaggle.com/hsankesara/flickr-image-dataset) from Kaggle. Each image has five captions. This data also contains a csv file that consists of three columns, the first column is the names of the images, the second column is the caption numbers and the third column is the captions.

We will use the MobileNet model that has been pre-trained for classifying images. But instead of using the last classification layer, we will redirect the output of the previous layer. This gives us a vector with 1024 elements that summarizes the image-contents. This part is called an encoder.

We will use this vector as the initial state of the LSTM units and we will use an intermediate fully-connected (dense) layer to map the vector with 1024 elements down to a vector with only 512 elements.

The decoder then uses this initial-state together with a start-marker "sss" to begin producing output words and a stop-marker "eee" that marks the end of the text.

We will use [Glove](http://nlp.stanford.edu/data/glove.6B.zip) for the text embedding to extract features from the raw text.

The decoder will be implemented by creating LSTM model that will be trained to map the vectors with transfer-values from the image-recognition model into sequences of integer-tokens that can be converted into text.

