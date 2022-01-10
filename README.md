# Neural_Network_Charity_Analysis

## Purpose & Overview
Alphabet Soup is a non-profit philanthropic foundation dedicated to protecting the environment and people. Alphabet Soup raises money and donates it to other organizations that share the same values and mission as themselves. Unfortunately, not every donation made proves to be successul. As a result, Alphabet Soup is looking for a way to better predict which applicants, if given funding, will prove to be successful.

The below analysis contains data of more than 34,000 organizations that have received funding from Alphabet Soup. The purpose was to create a binary classifier that could be capable of predicting whether an applicant would besuccessful if funded. Once a base model was created (First Model) the goal was to create a duplicate second model (Second Model) where changes could be made to determine if the accuracy could be increased to 75% or higher.

Tools used: Jupyter Notebook, Python (Pandas & Scikit Learn libraries) and Neural Networks (Tensorflow).

## Analysis
The first part of the analysis was to explore the data and determine the dependent and independent variables:

Y, or dependent, or target variable:
- IS_SUCCESSFUL: was the money used effectively

X, or independent, of feasture variables:
- APPLICATION_TYPE: Alphabet Soup application type
- AFFILIATION: Affiliated sector of industry
- CLASSIFICATION: Government organization classification
- USE_CASE: Use case for funding
- ORGANIZATION: Organization type
- STATUS: Active status
- INCOME_AMT: Income classification
- SPECIAL_CONSIDERATIONS: Special consideration for application
- ASK_AMT: Funding amount requested

The following variables were removed as they added to added value to the model:
- EIN: Identification column
- NAME: Identification column

After preparing the dataset and splitting the data into testing and training sets, a neural network was established in order to see if a model could be created that would predict whether or not the entity receiving the money was successful in the endeavor.

### First Model Attempt
- Variables
  - The first model attempt used the X and Y variables identified above.
  - Categorical Variables ```APPLICATION_TYPE``` & ```CLASSIFICATION``` used cutoffs of 500 and 1,500 respectively to bin it's values.
- Number of Hidden Layers: 2
- First hidden layer activation function: ```relu```
- Second hidden layer activation function: ```relu```
- Output layer activiation function: ```sigmoid```
- Epochs: 30
- Accuracy: 69.78%

### Second Model Attempt
The purpose of the 2nd model was to try to improve upon the accuracy of the First Model. Changes between the models are in <b>bold</b>.
- Variables
  - The second model attempt used the X and Y variables identified above.
  - Categorical Variables ```APPLICATION_TYPE``` & ```CLASSIFICATION``` used cutoffs of 500 and 700 respectively to bin it's values.
    -  <b>```CLASSIFICATION``` cutoff was changed to 700 from 1,500</b>
  - However, due to the size/scale of the values for ```ASK_AMT``` the values for this variable were divided by 1,000
  - <b>```application_df["ASK_AMT"] = application_df["ASK_AMT"] / 1000```</b>
- Number of Hidden Layers: 3
  - <b>Added a third hidden layer</b>
- First hidden layer activation function: ```relu```
- Second hidden layer activation function: ```tanh```
  - <b>Changed to ```tanh```</b>
- <b>Third hidden layer activation function: ```tanh```</b>
- Output layer activiation function: ```sigmoid```
- Epochs: 30
- Accuracy: 71.76%

## Results
As can be seen from the analysis summary above and the associated jupyter notebook file, the accuracy between the First and Second models was very similar. With the goal of trying to get the Second Model to 75%, the following was attempted but not included in the final submission:
- Removing each of the other features one at a time to see how the model would react. When each individual feature was removed, the accuracy decreased.
- Only having 1 hidden layer: accuracy went down
- Adding more Epochs: no increase in accuracy
- Adding more neurons: no increase in accuracy
- Changing hidden layer activation functions to ```sigmoid``` caused the accuracy to decrease

## Summary
Unfortunately, the results of the Deep Learning Neural Network on the analysis above did not return a high level of accuracy. Both the First and Second models bore an accuracy of 69.78% and 71.76%. The recommendation for moving forward is to add additional Features (independent variables) that can help with the predictive power. Other variables to consider would be:
- Total Money Raised: what other funds has the organization been able to raise?
- Organization Age: How long has the organization been operating?
- Number of Employees: How many employees does the organization have?
- Country of Origin: Where is the organization based?
- County of Operation: Where will the organization be spending their donated funds?
- Program Evaluation: What is the opinion of the likely success of the organization's program?
