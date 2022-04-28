![](coolclusters.jpg)

# Crypto-Cluster
As a Senior Manager at the Advisory Services team on a Big Four firm. One of your most important clients, a prominent investment bank, is interested in offering a new cryptocurrencies investment portfolio for its customers, however, they are lost in the immense universe of cryptocurrencies. 

Tasked with analysis, interpretation, and presentation by generating a report of what cryptocurrencies are available on the trading market and how they can be grouped using classification.
In this project, there are unsupervivsed learning and Amazon SageMaker skills exhibited by clustering cryptocurrencies and creating plots to present results.

Main goals:


Data Preprocessing: Prepare data for dimension reduction with PCA and clustering using K-Means.


Reducing Data Dimensions Using PCA: Reduce data dimension using the PCA algorithm from sklearn.


Clustering Cryptocurrencies Using K-Means: Predict clusters using the cryptocurrencies data using the KMeans algorithm from sklearn.


Visualizing Results: Create some plots and data tables to present your results.


Optional Challenge: Deploy your notebook to Amazon SageMaker.




Files

crypto_clustering.ipynb

Data Preprocessing

Using the following requests library, retreive the necessary data from the following API endpoint from CryptoCompare - https://min-api.cryptocompare.com/data/all/coinlist.

Data loaded into a Pandas DataFrame


Clean columns: 'CoinName','Algorithm','IsTrading','ProofType','TotalCoinsMined','TotalCoinSupply'


Keept only the cryptocurrencies that are trading.


Keept only the cryptocurrencies with a working algorithm.


Removed the IsTrading column.


Removed all cryptocurrencies with at least one null value.


Removed all cryptocurrencies that have no coins mined.


Dropped all rows where there are 'N/A' text values.


Stored the names of all cryptocurrencies in a DataFrame named coins_name, use the crypto_df.index as the index for this new DataFrame.


Removed the CoinName column.


Created dummy variables for all the text features, and store the resulting data in a DataFrame named X.


Used the StandardScaler from sklearn to standardize all the data of the X DataFrame. Remember, this is important prior to using PCA and K-Means algorithms.



Reducing Data Dimensions Using PCA
Used the PCA algorithm from sklearn to reduce the dimensions of the X DataFrame down to three principal components.

Once reduced, created a DataFrame named pcs_df using as columns names "PC 1", "PC 2" and "PC 3"; use the crypto_df.index as the index for this new DataFrame.

Clustering Cryptocurrencies Using K-Means

Used KMeans algorithm from sklearn is used to cluster the cryptocurrencies using the PCA data.

Created an Elbow Curve to find the best value for k using the pcs_df DataFrame.

Defined the best value for k, ran the Kmeans algorithm to predict the k clusters for the cryptocurrencies data. Used the pcs_df to run the KMeans algorithm.


Created a new DataFrame named clustered_df, that included the following columns "Algorithm", "ProofType", "TotalCoinsMined", "TotalCoinSupply", "PC 1", "PC 2", "PC 3", "CoinName", "Class". Maintained the index of the crypto_df DataFrames as shown.




Visualizing Results
Created data visualization to present the final results. Performed the following tasks:


Created a scatter plot using hvplot.scatter, to present the clustered data about cryptocurrencies having x="TotalCoinsMined" and y="TotalCoinSupply" to contrast the number of available coins versus the total number of mined coins. Used the hover_cols=["CoinName"] parameter to include the cryptocurrency name on each data point.


Used hvplot.table to create a data table with all the current tradable cryptocurrencies. The table has the following columns: "CoinName", "Algorithm", "ProofType", "TotalCoinSupply", "TotalCoinsMined", "Class"




!pip install -U altair




Use the altair scatter plot to create the Elbow Curve.


Use the altair scatter plot to visualize the clusters. Since this is a 2D-Scatter, use x="PC 1" and y="PC 2" for the axes, and add the following columns as tool tips: "CoinName", "Algorithm", "TotalCoinsMined", "TotalCoinSupply".


Use the altair scatter plot to visualize the tradable cryptocurrencies using x="TotalCoinsMined" and y="TotalCoinSupply" for the axes.


Show the table of current tradable cryptocurrencies using the display() command.


Remove all hvplot references from your code.



Complementary Resources


Altair visualization library website.


Simple line chart using Altair.


Simple Scatter Plot with Tooltips using Altair


Color customization on Altair


Printing all rows from a DataFrame


Install External Libraries and Kernels in Amazon SageMaker Notebook Instances



Additional Submission


Code your solution using the provided starter Jupyter notebook.


For the Challenge section, create a new Jupyter notebook named crypto_clustering_sm.ipynb and include the necessary code to import the additional required library.


Create and upload a repository with the above files to GitHub and post a link in BootCamp Spot.
