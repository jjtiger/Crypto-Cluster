# Crypto-Cluster
As a Senior Manager at the Advisory Services team on a Big Four firm. One of your most important clients, a prominent investment bank, is interested in offering a new cryptocurrencies investment portfolio for its customers, however, they are lost in the immense universe of cryptocurrencies. Tasked with analysis, interpretation, and presentation by generating a report of what cryptocurrencies are available on the trading market and how they can be grouped using classification.
In this assignment, there are unsupervivsed learning and Amazon SageMaker skills exhibited by clustering cryptocurrencies and creating plots to present results.
Main tasks:


Data Preprocessing: Prepare data for dimension reduction with PCA and clustering using K-Means.


Reducing Data Dimensions Using PCA: Reduce data dimension using the PCA algorithm from sklearn.


Clustering Cryptocurrencies Using K-Means: Predict clusters using the cryptocurrencies data using the KMeans algorithm from sklearn.


Visualizing Results: Create some plots and data tables to present your results.


Optional Challenge: Deploy your notebook to Amazon SageMaker.




Files

crypto_clustering.ipynb



Instructions

Data Preprocessing

Using the following requests library, retreive the necessary data from the following API endpoint from CryptoCompare - https://min-api.cryptocompare.com/data/all/coinlist. HINT: You will need to use the 'Data' key from the json response, then transpose the DataFrame. Name your DataFrame crypto_df.


With the data loaded into a Pandas DataFrame, continue with the following data preprocessing tasks.


Keep only the necessary columns: 'CoinName','Algorithm','IsTrading','ProofType','TotalCoinsMined','TotalCoinSupply'


Keep only the cryptocurrencies that are trading.


Keep only the cryptocurrencies with a working algorithm.


Remove the IsTrading column.


Remove all cryptocurrencies with at least one null value.


Remove all cryptocurrencies that have no coins mined.


Drop all rows where there are 'N/A' text values.


Store the names of all cryptocurrencies in a DataFrame named coins_name, use the crypto_df.index as the index for this new DataFrame.


Remove the CoinName column.


Create dummy variables for all the text features, and store the resulting data in a DataFrame named X.


Use the StandardScaler from sklearn to standardize all the data of the X DataFrame. Remember, this is important prior to using PCA and K-Means algorithms.



Reducing Data Dimensions Using PCA
Use the PCA algorithm from sklearn to reduce the dimensions of the X DataFrame down to three principal components.
Once you have reduced the data dimensions, create a DataFrame named pcs_df using as columns names "PC 1", "PC 2" and "PC 3"; use the crypto_df.index as the index for this new DataFrame.



Clustering Cryptocurrencies Using K-Means
KMeans algorithm from sklearn is used to cluster the cryptocurrencies using the PCA data.
Tasks:


Create an Elbow Curve to find the best value for k using the pcs_df DataFrame.


Once you define the best value for k, run the Kmeans algorithm to predict the k clusters for the cryptocurrencies data. Use the pcs_df to run the KMeans algorithm.


Create a new DataFrame named clustered_df, that includes the following columns "Algorithm", "ProofType", "TotalCoinsMined", "TotalCoinSupply", "PC 1", "PC 2", "PC 3", "CoinName", "Class". You should maintain the index of the crypto_df DataFrames as is shown bellow.




Visualizing Results
Create data visualization to present the final results. Perform the following tasks:


Create a scatter plot using hvplot.scatter, to present the clustered data about cryptocurrencies having x="TotalCoinsMined" and y="TotalCoinSupply" to contrast the number of available coins versus the total number of mined coins. Use the hover_cols=["CoinName"] parameter to include the cryptocurrency name on each data point.


Use hvplot.table to create a data table with all the current tradable cryptocurrencies. The table should have the following columns: "CoinName", "Algorithm", "ProofType", "TotalCoinSupply", "TotalCoinsMined", "Class"



Optional Challenge
For the challenge section, upload Jupyter notebook to Amazon SageMaker and deploy it.
The hvplot library is not included in the built-in anaconda environments, so for this challenge section, use the altair library instead.
Tasks:


Upload  Jupyter notebook and rename it as crypto_clustering_sm.ipynb


Select the conda_python3 environment.


Install the altair library by running the following code before the initial imports.

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
