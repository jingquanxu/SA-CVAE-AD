SA-CVAE

## Project Introduction

Source codes for the paper "An anomaly detection method for gas turbines in power plants using conditional variational autoencoder optimized with self-attention": [Reliability Engineering and System Safety 267 (2026) 111894]
by Dongchao Chen, Xiuxia Li, Jingquan Xu, Zhong Wang.


## The source code will be coming soon ##


This project implements a Conditional Variational Autoencoder (CVAE) integrated with a Self-Attention mechanism (SA-CVAE) for industrial equipment/complex system anomaly detection. 
The model learns latent space distributions from normal operational data and identifies anomalies by quantifying reconstruction probability deviations.
This document describes the project structure, environment configuration, execution methods, and output content.

Core Features:
Conditional Encoding: It jointly considers feature variables and operational condition variables.
Feature Self-Attention: The self-attention operation is computed across feature dimensions to strengthen the model's capacity for salient feature extraction.
Anomaly Detection: Threshold-based anomaly detection is implemented by analyzing reconstruction probability distributions using KDE or the 3σ rule for boundary definition.
Scalability: Feature variables and operational condition variables can be customized for different datasets.

## Project Structure

project_root/
│
├── src/
│ ├── init.py
│ ├── data_processing.py		# Data normalization, denormalization, and utility functions
│ ├── model.py			# CVAEWithAttention and other model definitions
│ ├── optimization.py 		
│ ├── utils.py			# Metrics calculation, KDE thresholding, and other utilities
│ └── evaluation.py		# Anomaly detection metrics calculation
│
├── data/ 
│ ├── data_normal.pkl 	    	# Normal Dataset
│ └── data_fault.pkl	    	# Anomaly Dataset
│
├── results/			# Training and testing output results
│
├── train.py 			# Data Loading + Model Training
├── test.py			# Model Testing + Evaluation
├── requirements.txt		# Dependencies
└── README.md 			# Project Documentation


## Dependencies
requirements.txt

##Data Preparation
data/normal.xlsx：Normal Dataset
data/fault.xlsx：Anomaly Dataset
The dataset must contain numerical feature columns, and the Time column may be omitted.

## Train Model
python train.py
Load normal data
Split into training and validation sets
Standardize the data
Initialize and train the SA-CVAE model
Save the trained weights and validation set reconstruction results

## Model Testing and Evaluation
python test.py
Load the trained model weights
Reconstruct test data or full dataset
Calculate reconstruction probability
Perform anomaly detection based on thresholds
Save results and evaluation metrics (MAE, MSE, R², confusion matrix, ROC curve, etc.)
Save output results

## Usage Instructions
Place the data files in the data folder
Adjust the configurations in train.py 
Tune hyperparameters as needed
Run train.py to complete model training
Run test.py for model testing and evaluation
Check the results folder for output results

