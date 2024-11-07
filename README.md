# Module 21 Report

## Overview of the Analysis

The purpose of this analysis was to build and optimize a neural network/deep learning model that can identify which applicants for funding had the best chance of success in their endeavors. The data used to train the model included information from 34,000 organizations that had previously recieved nonprofit funding. The file was composed of the following information:

* EIN and NAME — Identification columns
* APPLICATION_TYPE — Alphabet Soup application type
* AFFILIATION — Affiliated sector of industry
* CLASSIFICATION — Government organization classification
* USE_CASE — Use case for funding
* ORGANIZATION — Organization type
* STATUS — Active status
* INCOME_AMT — Income classification
* SPECIAL_CONSIDERATIONS — Special considerations for application
* ASK_AMT — Funding amount requested
* IS_SUCCESSFUL — Was the money used effectively

## Preprocessing

First the identification columns were removed from the dataset. After doing so, the APPLICATION_TYPE and CLASSIFICATION columns were placed into bins. Then the appropriate columns were transformed into dummy variables. Finally, the dataset was standardized and split into training and testing data. The IS_SUCCESSFUL column was the y value and the rest of the data made up the X values. A quick value count of the y variable showed that it was evenly sampled.

## Results

# Model 1
The first model consisted of 2 hidden layers. The first layer had 100 neurons and the second layer had 30. Both used the 'relu' activation function. The output layer had only 1 neuron and used the 'sigmoid' function and this did not change in the other optimization attempts.

The model ran for 100 epochs and had an accuracy score of 72.96%.

# Optimization Attempt 1
The first attempt at optimizing the model in the AlphabetSoupCharity_Optimization.ipynb file began by removing the SPECIAL_CONSIDERATIONS variables from the testing data. My thinking was that the presence of special considerations with no clue as to what they are would be less useful to the model than a variable such as funding amount. In addition, too much information in the training data may result in the model assigning too much weight to one element and not enough on another. 

However, after running the same model with the same number of hidden layers and neurons on the smaller dataset, the model performed slightly less well at 72.94%. I then ran the model again on the smaller data but increased the number of neurons and it became even less accurate at 72.81%. 

# Optimization Attempt 2
I then made a second optimization file which used the original preprocessed data. For the second optimization attempt, I added a third hidden layer. This again caused the model to decline slightly in accuracy to 72.90%. I then significantly increased the number of neurons in each hidden layer which again further decreased the usability of the model to 72.81% accuracy.

# Optimization Attempt 3
For the final attempt to optimize the model and increase the accuracy to 75%, I removed the third hidden layer and kept the neurons the remaining two to 200 and 100 respectively. In addition, I increased the number of epochs to 200 so that the model would have more time to train. This finally resulted in an accuracy score of 73.16%.

## Summary

Typically the number of neurons per hidden layer is 2 to 4 times the number of inputs for a deep learning model. I ended up using more than that for one of my hidden layers. Ultimately it was the number of epochs that increased the accuracy of the model.