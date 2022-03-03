# Cryptocurrencies
Using unsupervised machine learning on cryptocurrencies that are on the trading market and how they could be grouped to create a classification system for this new investment.

## Overview of Cryptocurrencies:
Martha is a senior manager for the Advisory Services Team at Accountability Accounting, one of your most important clients. Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. A classification system for this new investment needs to be created   that includes what cryptocurrencies are on the trading market and how they could be grouped.

## Resources:
* Data: crypto_data.csv
* Software: Jupyter Notebook 6.4.8 , Python 3.7.11

## Results:
The results can be verified in [crypto_clustering.ipynb](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/crypto_clustering.ipynb)
## Deliverable 1: Preprocessing the Data for PCA
* The data from crypto_data.csv after loading

![crypto_data](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/crypto_data.png)

* All cryptocurrencies that are not being traded are removed.
* The IsTrading column is dropped.
* All the rows that have at least one null value are removed.
* All the rows that do not have coins being mined are removed.
* The CoinName column is dropped.
* A new DataFrame is created that stores all cryptocurrency names from the CoinName column and retains the index from the crypto_df DataFrame

![cleaned](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/cleaned.png)

* The get_dummies() method is used to create variables for the text features, which are then stored in a new DataFrame, X

![encoding](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/encoding.png)

* The features from the X DataFrame have been standardized using the StandardScaler fit_transform() function.

![scalar](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/scalar.png)

## Deliverable 2: Reducing Data Dimension Using PCA
* The PCA algorithm reduces the dimensions of the X DataFrame down to three principal components.

![PCA](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/PCA.png)

* The pcs_df DataFrame is created and has the following three columns, PC 1, PC 2, and PC 3, and has the index from the crypto_df DataFrame 

![pcs_df](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/pcs_df.png)

## Deliverable 3: Clustering Cryptocurrencies Using K-means

The K-means algorithm is used to cluster the cryptocurrencies using the PCA data, where the following steps have been completed:
* An elbow curve is created using hvPlot to find the best value for K.

![elbow](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/elbow.png)

* Predictions are made on the K clusters of the cryptocurrencies’ data.

![k_means](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/k_means.png)

* A new DataFrame is created with the same index as the crypto_df DataFrame and has the following columns: Algorithm, ProofType, TotalCoinsMined, TotalCoinSupply, PC 1, PC 2, PC 3, CoinName, and Class.

![clustered_df](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/clustered_df.png)

## Deliverable 4: Visualizing Cryptocurrencies Results
* The clusters are plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover.

![3d_scatter](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/3d_scatter.png)

* A table with tradable cryptocurrencies is created using the hvplot.table() function

![hvplot_table](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/hvplot_table.png)

* The total number of tradable cryptocurrencies is 532.

* A DataFrame is created that contains the clustered_df DataFrame index, the scaled data, and the CoinName and Class columns.

![plot_df](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/plot_df.png)

* A hvplot scatter plot is created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point.

![hvplot_scatter](https://github.com/sucharita1/Cryptocurrencies/blob/8d2932b39fd2bf873e3fdefd244f8d2526aff846/Resources/Images/hvplot_scatter.png)



