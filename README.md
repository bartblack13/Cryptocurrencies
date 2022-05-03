# Cryptocurrencies
Unsupervised Machine Learning, clustering, K-means, PCA python and jupyter notebook

## Purpose:
* Describe the differences between supervised and unsupervised learning, including real-world examples of each.
* Preprocess data for unsupervised learning.
* Cluster data using the K-means algorithm.
* Determine the best number of centroids for K-means using the elbow curve.
* Use PCA to limit features and speed up the model.

## Method and Results:

Deliverable 1: Pre-process the data 
The initial data was provided to me as a CSV file, which consisted of 1252 rows of data across 7 columns.  The columns contained a mix of both numerical and non-numerical data.  As part of the pre-processing phase, I removed unnecessary columns and rows with null values, and I also removed any cryptocurrency that is not actively trading.  The pre-processing resulted in 532 rows and 4 columns: TotalCoinsMined, TotalCoinSupply, Algorithm, and ProofType (see Figure 1).  I then used get_dummies to parse out the algorithm types of each cryptocurrency, as well as the prooftype.  This resulted in a dataframe with 532 rows and 98 columns.  I then scaled the data using StandardScaler.
<br><br>

![This is an image]()<br>
Figure 1: cleaned dataframe<br><br>

Deliverable 2: Reduce data dimensions using PCA
Once the data was scaled, I used Principle Component Analysis to reduce the 98 features down to 3 (PC 1, PC 2, PC 3), which was then saved as a dataframe (see Figure 2).

![This is an image]()<br>
Figure 2: PCA dataframe<br><br>

Deliverable 3: Clustering Crytocurrencies Using K-Means
The PCA results was fed into the K-Means model.  This required that I use a for-loop to calculate out the inertia, which was then used to generate an elbow curve (see Figure 3).  The Elbow Curve showed a drastic leveling off of the slope at k = 4, so I used this value as n_clusters to initialize the K-Means model.  I then fit the data to the model and generated cluster predictions.  I then generated a new dataframe by concatenating the cleaned dataframe with the PCA dataframe, and then adding two more columns, CoinName and Class, where Class values were the previously generated cluster predictions from the K-Means model (see Figure 4).


![This is an image]()<br>
Figure 3: Elbow Curve<br><br>

![This is an image]()<br>
Figure 4: Post K-Means Dataframe with PCA components and corresponding cluster predictions<br><br>


Deliverable 4: Visualizing Cryptocurrencies Results
I used this new dataframe in combination with px.scatter_3d to generate a 3D scatter plot.  The PCA components were the x, y, z axes, and the color and symbol attributes used the values from the Class columns (See Figure 5).  I also created a searchable/sortable table from the clustered data (See Figure 6).  Next, I used MinMaxScaler to scale the TotalCoinSupply and TotalCoinsMined columns, so that I could graph their values in a 2D scatter plot (See Figure 7)


![This is an image]()<br>
Figure 5: 3D Scatter plot, showing grouping based on the principle component anaysis<br><br>

![This is an image]()<br>
Figure 6: Searchable and Sortable table, containing 532 tradable cryptocurrencies<br><br>

![This is an image]()<br>
Figure 7: 2D Scatter Plot of TotalCoinsMined vs. TotalCoinsSupply; Class Color is representative of the clustering predictions mentioned in Delieverable 3 (see Figure 4)<br><br>

