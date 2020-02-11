# Coding and Classification using Bayesian Optimization 
This repository contains the code to perform text classification utilizing Bayesian optimization, where loss function is defined by fastText technique. 

## Requirements
* Anaconda (python 3.6)/Google Colab
* Sklearn
* Scipy
* bfastText

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

### caeser_cipher.py
#### Import a package
unicodedata
#### Define a function strip_accents() to return a unicode text to pure ascii. 
##### Input
A sentence, called text.
##### Algorithm
1. Perform a Canonical Decomposition (NFD) of the Unicode text;
2. Transform the NFD mapped characters into ascii;
3.  Decode characters with UTF-8.
#### Import a package
unicodedata
#### Define a function cipher() to encrypt text using the Caesar Cipher technique.
##### Input
1.	A sentence, called sentence.
2.	An integer indicates the shift, called shift_value.
##### Algorithm
1.	Traverse the given text one character at a time;
2.	Get the ascii representation of the character, then add the shifted value on it;
3.	Encrypt uppercase characters and lowercase characters separately;
4.	Concatenate encrypted characters together.

### Bayesian Tunng.ipynb
Code reference: https://github.com/thuijskens/bayesian-optimization
#### Import packages
sklearn.guassian_process, numpy, pandas, scipy.stats.norm, scipy.optimize.minimize, fastText, os
#### Define a function get_tuning_params() to get tunning parameters.
##### Input
1.	A list of boundaries of hyperparameters, called bounds.
2.	A list of keys of hyperparameters, called hyper_params.
##### Algorithm
1.	A list of boundaries of hyperparameters, called bounds.
2.	A list of keys of hyperparameters, called hyper_params.
#### Define a function expected_improvement() to get expected improvements.
##### Input
1.	An array with a dimension of number of samples times number of hyperparameters, called x.
2.	A GuassianProcessRegressor object that is trained on previously evaluated hyperparameters, called guassian_process.
3.	An array of values of loss function for the previously evaluated hyperparameters, called evaluated_loss.
4.	 A Boolean value indicates whether the loss function is to be maximized or minimized, called greater_is_better.
5.	An integer indicates the number of hyperparameters, called n_params.
##### Algorithm
1.	Reshape x to have a dimension of number of samples times number of hyperparameters;
2.	Acquire values of mu, sigma, loss, and scaling factor for the Gaussian Process;
3.	Calculate expected improvement.
#### Define a function sample_next_ hyperparameter() to get the next hyperparameter to sample the loss function for. 
##### Input
1.	An objective function to be optimized, called acquisition_func.
2.	A GuassianProcessRegressor object that is trained on previously evaluated hyperparameters, called guassian_process.
3.	An array of values of loss function for the previously evaluated hyperparameters, called evaluated_loss.
4.	A Boolean value indicates whether the loss function is to be maximized or minimized, called greater_is_better.
5.	A tuple contains bounds of the L-BFGS optimizer, called bounds.
6.	An integer indicates the number of times to run the minimizer with different start points.
##### Algorithm
1.	Optimize the objective function with method ‘L-BFGS-B’ (a type of quasi-Newton methods using a limited amount of computer memory).
2.	Compare the optimized value with initial value
#### Define a function Bayesian_optimisation() to optimize the loss function sample_loss using Gaussian Processes. 
##### Input
1.	An integer indicates the number of iterations to run the search algorithm, called n_iters
2.	A loss function to be optimized, called sample_loss.
3.	An array contains lower and upper bounds on the parameters of the function sample_loss, called bounds.
4.	A list of lists from which each list contains a key of hyperparameter and initial values (low and high) of this hyperparameter, called tuning_vars.
5.	An integer indicates the number of points to sample from the loss function, called n_pre_samples.
6.	A dictionary contains parameters to pass on to the Gaussian Process, gp_params.
7.	An integer indicates whether to perform a random search or a L-BFGS-B optimization over the acquisition function, called random_search.
8.	A double indicates the variance of the error term of the Gaussian Process, called alpha.
9.	A double indicates the precision tolerance for floats, called epsilon.
##### Algorithm
1.	Initialize values of parameters and loss;
2.	Create the Gaussian Process;
3.	Sample the next parameter using random search method or L-BFGS-B method;
4.	In case of duplicates, randomly draw next query point from a uniform distribution;
5.	Recall loss function to sample loss for new set of parameters;
6.  Update the values of parameters and loss at each iteration.
