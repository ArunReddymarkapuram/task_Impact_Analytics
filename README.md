# task_Impact_Analytics
Keras implementation of the Bidirectional LSTM and CNN model for CoNLL 2003

# Result
The implementation achieves a test F1 score of ~86 with 30 epochs. Increase the number of epochs to 80 reach an F1 over 90 or more.

# GloVe vector representation
For glove vector representation please visit tis article https://nlp.stanford.edu/projects/glove/

# Dependencies 
    1) numpy 1.15
    2) Keras 2.1.6
    3) Tensorflow 1.8
    4) Stanford GloVE embeddings
Apart form LSTM conditional random field might work. With good choice in c1 and c2 paraameters and with good regularization parameters conditional random filed algorithm would be a good choice.

The model mainly had 3 inputs, namely  a  character-level, word-level and casing input, each of which encodes a different aspect.
The processing is done independently but merged to process further.
And  the data is divided in to 64 batchs. Using batch normalisazion must increase the accuracy of the model. 
Also I used GloVE for word embedding, with custome embedding acuraccy will be improved for sure.

# Character embedding
The vocabilary of 97 possible charecters are mapped to 30 dimentional embedding, intialized randomly. And number of words vary from batch to batch. Maximum number of charecters for a word are 52.

# Dropout 
drop at at 5.0 gave good results.

# CNN
CNN layer gets one dimentional charecter as its input, it has 30 kernals with stride of 3. Next layer is maxpooling as always, of size 52 with stride 52 which converts cahrecter size to 1. And for word embedding I used GloVE. And embedding layer will mapp the words to the casing types(8). The output is concatinated 

# LSTM
The LSTM used is a bidirectional LSTM. Concatinated data is given to the LSTM, which is transformed two vectors which are then given for forward recursion and backword recursion.

# softmax layer
softmax is applied to output to give a prediction to classify the sequence. 
