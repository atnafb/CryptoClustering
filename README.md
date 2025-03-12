# CryptoClustering

In this project, I used Python and unsupervised learning techniques to analyze the impact of price changes in cryptocurrencies. 
The objective is to predict if cryptocurrencies are affected by 24-hour or 7-day price changes using K-means clustering and Principal Component Analysis (PCA).

## Overview

This repository contains the steps to perform clustering on cryptocurrency market data, including:

1. **Data Loading & Exploration**
2. **Data Normalization**
3. **Elbow Method for Finding Optimal k**
4. **K-Means Clustering**
5. **Principal Component Analysis (PCA)**
6. **Comparison of Clustering Results Using Original and PCA-transformed Data**

## Files

The following files are included in the repository:

- `Crypto_Clustering.ipynb`: Jupyter notebook with the code for the analysis.
- `crypto_market_data.csv`: Dataset containing cryptocurrency market data.
- `README.md`: Instructions and details for the project.

## Instructions

### 1. Prepare the Data

- Load the `crypto_market_data.csv` file into a DataFrame.
- Get summary statistics and plot the data to understand its structure before proceeding.
  
### 2. Normalize the Data

- Use `StandardScaler()` from `scikit-learn` to scale the data.
- Set the `"coin_id"` index from the original DataFrame as the index for the new DataFrame.

### 3. Find the Best Value for k Using the Scaled DataFrame

- Use the **elbow method** to determine the optimal number of clusters (`k`):
  - Create a list with values of `k` from 1 to 11.
  - Calculate inertia for each value of `k` and plot the elbow curve.
  - Identify the best value for `k` based on the curve.
  
### 4. Cluster Cryptocurrencies Using K-means

- Initialize and fit the K-means model using the best value for `k`.
- Predict the clusters and add a new column with the predicted cluster labels.
- Create a scatter plot to visualize the clusters, using:
  - x-axis: `price_change_percentage_24h`
  - y-axis: `price_change_percentage_7d`
  - Color the points by cluster label and add the `coin_id` as a hover label.
  
### 5. Optimize Clusters with Principal Component Analysis (PCA)

- Perform PCA to reduce the features to three principal components.
- Retrieve the explained variance of each principal component and compute the total explained variance.
  
### 6. Find the Best Value for k Using the PCA DataFrame

- Apply the elbow method again on the scaled PCA data.
- Plot the elbow curve and determine the best value for `k`.
- Compare this result with the best `k` value found using the original scaled data.

### 7. Cluster Cryptocurrencies Using the PCA DataFrame

- Fit a K-means model on the scaled PCA DataFrame.
- Predict the clusters and add a new column for predicted labels.
- Create a scatter plot to visualize the clusters in the PCA space:
  - x-axis: `PCA1`
  - y-axis: `PCA2`
  - Color the points by cluster label and add the `coin_id` as a hover label.
  
### 8. Analysis

- Compare the clustering results using the original scaled data and PCA-transformed data.
- Answer the following questions:
  - What is the impact of using fewer features (PCA) to cluster the data with K-means?

## Requirements

- Python 3.x
- pandas
- scikit-learn
- matplotlib
- hvplot
