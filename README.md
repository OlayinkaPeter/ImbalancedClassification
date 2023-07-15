# Credit Risk Scoring Challenge | Logistic Regression | GermanCredit

The steps in the notebook are as follows: 
 

## 1. Install & import necessary libraries.

## 2. Cleaning our data
First, I check the number of datapoints available for each class.

Turns out that Value counts show that target variable - Class, is imbalanced.
To address this - I need to perform oversampling on the minority class - because 
undersampling will leave us with less datapoints. Dataset does not appear too 
large to need reduction.

## 3. Pre-processing
The minority class will be oversampled and concatenated back to the majority class.
I save the count for the majority and minority class in their variables and use it to 
subset the dataset.

Then I implement normalisation as the data-scaling technique - min_max in this case

## 4. Building the model: Logistic Regression with Keras
A logistic regression neural network is a type of artificial neural network that is used for 
classification problems. It is a linear model that uses the logistic function to map the input 
data to the output data. The logistic function is a sigmoid function that is used to map the 
real-valued input data to the probability of a binary output.

Logistic regression neural networks are often used for binary classification problems, but 
they can also be used for multi-class classification problems. To use a logistic regression 
neural network for a multi-class classification problem, the output layer of the network is 
typically replaced with a softmax layer. The softmax layer is a type of activation function 
that is used to map the output of the network to a probability distribution over the possible 
output classes.

Logistic regression neural networks are relatively simple to train and they can achieve good 
performance on a variety of classification problems. However, they can be sensitive to 
overfitting, and they can be difficult to interpret.

Here, I use a Sequential model with a single inner dense layer, the sigmoid activation 
function, and a unit that returns a classified value: either 0 or 1.

## 5. Train the model
I now train the model for 1000 epochs, and record the training and validation accuracy in the `history` object.

## 6. Evaluate the model
Model evaluation is the process of assessing the performance of a machine 
learning model. It is important to evaluate models to ensure that they are 
working as intended and to identify any potential problems. There are a 
number of different types of model evaluation metrics, which can be used 
to assess different aspects of model performance.

In this case, I have fairly reliable loss scores for all the error functions:
- Loss
- Mean Average Error
- Mean Squared Error

with MSE seeming the best for now.

## 7. Run predictions on validation data  
After running predictions, it doesn't look perfect. And there are a fair number of false positives. 
But there is absolutely room for improvement
I also take a look at the error distribution.

## 8. Deployment
An extra step I do not miss is saving a model in TensorFlow Serving once completed
TensorFlow Serving is a tool that allows you to deploy and serve machine learning models in production. It provides a variety of features that make it easy to deploy models, including:

- A RESTful API for serving models
- Support for multiple programming languages
- A variety of serving options, including on-premise, cloud, and edge

To save a model in TensorFlow Serving, you can use the tensorflow_serving.saved_model.save() function. This function takes a SavedModel object as input and saves it to a specified location.

Once I have saved my model, I can easily deploy it using the TensorFlow Serving API.

## 9. Reloading packaged saved models
TensorFlow Serving allows to reload saved models without having to restart the server. 
This can be useful for updating models with new data or for debugging models.