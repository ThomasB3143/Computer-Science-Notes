Section: [[Machine Learning (Root)]]
# Steps of Machine Learning

## Problem Framing

- Identifying training sets, features and labels
- Measure of success?
## Data Preparation

- **Cleaning** data by removing:
	- Anomalous entries
	- Incomplete entries
	- Noise (irrelevant features)
- **Separating** data into:
	- Training set
	- Test set
## Algorithm Selection

- Pick a machine learning algorithm:
	- Regression
	- Regularisation
	- Instance-based
	- Tree-based
	- Clustering
	- Bayesian
	- Ensemble
	- Dimensionality Reduction
## Model Training

- Training data is used to incrementally improve performance of the model
## Model Testing

- Using the model on data from the **test set** (not trained using this)
- Calculate a **measure of success**
## Hyperparameter Tuning

The model has **parameters**, which are variables changed during training. The training process has **hyperparameters**, which determine the rate at which the model learns (and the parameters change)