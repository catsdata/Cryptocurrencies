# Cryptocurrencies

**Table of Contents**

1. [Overview](https://github.com/catsdata/Cryptocurrencies#overview)
2. [Resources](https://github.com/catsdata/Cryptocurrencies#resources)
3. [Results](https://github.com/catsdata/Cryptocurrencies#results)
    - [Preprocessing the Data for PCA](https://github.com/catsdata/Cryptocurrencies#preprocessing-the-data-for-pca)
    - [Reducing Data Dimensions Using PCA](https://github.com/catsdata/Cryptocurrencies#reducing-data-dimensions-using-pca)
    - [Clustering Cryptocurrencies Using K-means](https://github.com/catsdata/Cryptocurrencies#clustering-cryptocurrencies-using-k-means)
    - [Visualizing Cryptocurrencies Results](https://github.com/catsdata/Cryptocurrencies#visualizing-cryptocurrencies-results)
4. [Summary](https://github.com/catsdata/Cryptocurrencies#summary)


## Overview

Create an analysis for clients who are preparing to get into the cryptocurrency market.

Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked for a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

## Resources

- Data Sources: 
    - [Crypto Data](https://github.com/catsdata/Cryptocurrencies/blob/main/Resources/crypto_data.csv)
- Software/Packages:  
    - Unupervised Machine Learning (mlenv)
        - Python
        - Pandas
        - SKLearn
            - StandardScaler
            - MinMaxScaler
            - PCA
            - KMeans
    - Jupyter Notebook

## Results

### Preprocessing the Data for PCA

- The following five preprocessing steps have been performed on the crypto_df DataFrame:
    - All cryptocurrencies that are not being traded are removed
    - The IsTrading column is dropped
    - All the rows that have at least one null value are removed
    - All the rows that do not have coins being mined are removed
    - The CoinName column is dropped
- A new DataFrame was created that stores all cryptocurrency names from the CoinName column and retains the index from the crypto_df DataFrame
- The get_dummies() method was used to create variables for the text features, which are then stored in a new DataFrame, X
- The features from the X DataFrame have been standardized using the StandardScaler fit_transform() function

![del1](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del1.PNG)

### Reducing Data Dimensions Using PCA

- The PCA algorithm reduced the dimensions of the X DataFrame down to three principal components
- The pcs_df DataFrame was created and has the following three columns, PC1, PC2, and P 3, and has the index from the crypto_df DataFrame

![del2](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del2.PNG)

### Clustering Cryptocurrencies Using K-means

- The K-means algorithm was used to cluster the cryptocurrencies using the PCA data, where the following steps were completed:
    - An elbow curve was created using hvPlot to find the best value for K
    - Predictions were made on the K clusters of the cryptocurrencies’ data
    - A new DataFrame was created with the same index as the crypto_df DataFrame and has the following columns: Algorithm, ProofType, TotalCoinsMined, TotalCoinSupply, PC1, PC2, PC3, CoinName, and class

![del3](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del3.PNG)

![del3_2](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del3_2.PNG)

### Visualizing Cryptocurrencies Results

- The clusters were plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover
- A table with tradable cryptocurrencies was created using the hvplot.table() function
- The total number of tradable cryptocurrencies was printed
- A DataFrame was created that contains the clustered_df DataFrame index, the scaled data, and the CoinName and class columns
- A hvplot scatter plot was created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "class", and it shows the CoinName when you hover over the data point

![del4](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del4.png)

![del4_2](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del4_2.png)

![del4_3](https://github.com/catsdata/Cryptocurrencies/blob/main/Images/del4_3.png)

## Summary


