# Cryptocurrencies

## About the Project 

This analysis uses the unsupervised machine learning technique of K Means Clustering on cryptocurrencies data to group the data and create a classification system.  A unsupervised technique is used because there is no known output we are specifically looking for.  My analysis is then displayed in a 3D plot using plotly.express and in a scatter plot using hvplot.

### Preprocessing Steps

After using pandas to load the csv file into a dataframe, I preformed the below steps:

1. Removed cryptocurrencies that weren't being trading from the dataframe.  
2. Eensured all cryptocurrencies had a working Algorithm, therefore checking if there were any null values in the Algorithm column.
3. Removed the "IsTrading" column and dropped any rows with null values from the entire dataframe.
4. Kept only rows where coins are mined.
5. Created a new dataframe with just the "CoinName" column, which became the "Y" dataframe
6. Dropped the "CoinName" column from the first dataframe, which became the "X" dataframe
7. Changed the "TotalCoinSupply" column to a float variable type on the "X" dataframe
8. Used get_dummies() to create variables for text features on the "X" dataframe
9. Standardized the data with StandardScaler() on the "X" dataframe

### Reducing Dimensions

I applied the Principal Component Analysis (PCA) algorithm to reduce the dimensions of the "X" dataframe into 3 principal components.  This is done by using sklearn.decomposition.PCA.  PCA will reduce the the larger data set into a smaller set.  After the PCA components were fit and transformed, they were loaded into a new dataframe with the column labels "PC 1", "PC 2", and "PC 3".  The new dataframe is the input for the KMeans machine learning model.

### The Machine Learning Algorithm

The unsupervised machine learning model of KMeans clustering puts data in clusters that are determined by the mean of data points.  To determine the number of clusters used in the model, we use an elbow cuve that plots k, numbers 1-10 on the x axis, and y as inertia.  We pick the number, k, where the curve distinctively turns.  I ran my model and developed predictions with 4 clusters.  
My final dataframe will include the original input columns, the coin name, the PCA generated columns, and a new column with the predicted cluster to the corresponding data. 

### Visualization

My 3D visualization displays the 3 PCA factors as x, y, and z values and colors the points according to their predicted class.

![3d_plot](/Images/3d_plot.png)

My scatterplot visualization plots the Total Coins Mined on the x axis and the Total Coin Supply on the y axis.  Each point is colored by the predicted class.  

![scatter_plot](/Images/scatter_plot.png)


### Built With
- Python
- Jupyter Notebook
- pandas
- hvplot.pandas
- plotly.express
- sklearn.preprocessing
- sklearn.decomposition
- sklearn.cluster
