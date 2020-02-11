# Coding and Classification using Bayesian Optimization 
This repository contains the code to perform text classification utilizing Bayesian optimization, where loss function is defined by fastText technique. 

## Requirements
Anaconda (python 3.6)/Google Colab
Sklearn
Scipy
fastText

## Deployment
1.	Modify the train_data and test_data objects in Bayesian Tuning.ipynb to the formatted training dataset and testing dataset;
2.	Run Bayesian Tuning.ipynb.

## Dataset
Brief description of the datasets with explanations of the column headers.

| Column Header  | Description | Example |
| ------------- | ------------- |------------- |
| Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  |
| ...  | ...  | ...  |

## Code Files Explanation
### Import a package
unicodedata
### Define a function strip_accents() to return a unicode text to pure ascii. 
### Input
A sentence, called text.
### Algorithm
1. Perform a Canonical Decomposition (NFD) of the Unicode text;
2. Transform the NFD mapped characters into ascii;
3.  Decode characters with UTF-8.




