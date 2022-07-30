# Neural_Network_Charity_Analysis
Using deep Learning neural networks to choose charities for future donations. 

## Overview 

This project analyzed data from charitable organizations which have received donations in the past targeting the success or failure of these projects in order to best direct the foundation in which organizations to fund in the future and prevent donating to projects which are likely to fail. Using Neural Networks, we will create a binary classifier to categorize future donation requests as likely to succeed or fail. 


## Results

### Data Preprocessing

The first step in running a Neural Network is to process the data and select the target and feature variables.

* Target variables: "IS_SUCCESSFUL" column
    * 1 = Successful
    * 0 = Not successful
* Feature variables: 
    * Application Type (binned and encoded)
    * Affiliation (encoded)
    * Classification (binned and encoded)
    * Use_Case (encoded)
    * Organization (encoded)
    * Income amount (encoded)
    * Special considerations (encoded)
    * Ask amount
* Data to be removed from dataset: (neither features nor variables)
    * Name
    * EIN (tax identification number)
    * Status (was not helpful in categorization)

### Compiling, Training, and Evaluating the Model

#### Final Neural Network Design:
* 3 Layers: Input layer, 1 hidden layers, output layer
* Neurons: 
    * Layer 1 (input): 80
    * Layer 2: 30
    * Layer 3 (output): 1
* Activation functions:
    * Layer 1: ReLu
    * Layer 2: ReLu
    * Layer 3: Sigmoid (for binary classification)


The attempted neural network designs had accuracy scores between 0.708 and 0.730, but optimization was not successful in raising the accuracy score above 0.750. The final model was chosen for having the highest accuracy score of .730 which used the ReLu functions and Sigmoid functions with an increased number of nodes per layer of 80, 30, and 1 resuling in 5,901 parameters. 

#### Optimization Attempts: 

Original Neuron Design: 
* Layer 1 (input) w/ ReLu: 10
* Layer 2 w/ ReLu: 5
* Layer 3 (output) w/ Sigmoid: 1
Epochs: 100
Result: Accuracy Score of 0.730

1. Increased Epochs to 150 
    * Layer 1 (input) w/ ReLu: 10
    * Layer 2 w/ ReLu: 5
    * Layer 3 (output) w/ Sigmoid: 1
    Epochs: 150
    Result: Accuracy Score decreased to 0.728

2. Changed activation function in 2nd layer to Tanh
    * Layer 1 (input) w/ ReLu: 10
    * Layer 2 w/ Tanh: 5
    * Layer 3 (output) w/ Sigmoid: 1
    Epochs: 100
    Result: Accuracy Score increased slightly to 0.729

3. Added a 4th layer and increased nodes within each layer:
    * Layer 1 (input) w/ ReLu: 100
    * Layer 2 w/ ReLu: 30
    * Layer 3 w/ ReLu: 6
    * Layer 4 (output) w/ Sigmoid: 1
    Epochs: 150
    Result: Accuracy Score decreased slightly to 0.728

Additional attepmts to remove columns from the data set such as "APPLICATION_TYPE", "ASK_AMOUNT" and "SPECIAL_CONSIDERATIONS" resulted in an even lower Accuracy score of 0.708. 




## Summary

Final Neuron Design: 
Removed columns of STATUS and kept original Neuron Design, but increased the number of nodes within the layers:
    * Layer 1 (input) w/ ReLu: 80
    * Layer 2 w/ ReLu: 30
    * Layer 3 (output) w/ Sigmoid: 1
    Epochs: 100
    Result: Accuracy Score of .729

I found the biggest improvement to be adding increase neurons in the 3 layer model using the ReLu function. The general rule of thumb is to use 2-3 times the nodes in the first layer as the input features. This data set has 39 input features, so using 80 nodes in the first layer was the best option, as using 100 nodes did not create a higher accuracy score. 

I could not get the accuracy score above 0.730, but there are additional model variations that could be helpful. Increasing the number of layers and epochs was time consuming, but it could be helpful to add another 2 layers and continue increasing nodes such as a 4 layer design as such:
Layer 1 (input) w/ ReLu: 120
Layer 2 w/ ReLu: 80
Layer 3 w/ ReLu: 40
Layer 4 w/ ReLu: 20
Layer 4 (output) w/ Sigmoid: 1

I believe there is additional testing with the outliers in the data as well. Some donation ask amounts were very high and additional analysis needs to be done on the raw data to mitigate these outliers. My attempt to remove the column or remove the outlier data did not improve performance, but a more robust statistical assessment could be better.
