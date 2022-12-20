
<h1 align="center">Multi Clustering Development project on stock</h1>
<h3 >Baptiste Loyer</h2>
</h3>

<h4 align="center">
	🚧 Development project using Python and Sk Learn 🚀   🚧
</h4>

<hr>
<br>

## :rocket: Objectives

The following skills/tasks were aimed by this project:

-  Develop good programming practices
-  Use standard development tools

- Write the Python functions implementing the workflow in one single .py file.
- Apply the workflow onto the two datasets, using either a Python script or a notebook.
- Important: Your .py file containing the functions must be the same when applied to one or the other dataset

## :dart: About
I Present the project:
In the first part, I will work on `pandas` data analysis. 
In the second part, I will implement a clustering algorithm to group companies based on their stock price movements. 
In the final part, I will explore ways to extend and improve this analysis.



## DATA 📊
The assignment comes with two files containing company data:
- `SP_500_firms.csv` with firm and ticker names
- `SP_500_close_2015.csv` with stock price data for 2015

The methods we used:

Methods
In Depth Analysis
Hard clustering classification method which aims to partition the data into clusters. It affects each sample to the class which has the closest centroid.
## 4.1 Spectral Clustering

![4 1](https://user-images.githubusercontent.com/91438136/208402087-ad3ce1d4-2b17-4867-ade6-17d06adf4ba3.PNG)

1) Introduction: Spectral clustering techniques make use of the spectrum (eigenvalues) of the similarity matrix of the data to perform dimensionality reduction before clustering in fewer dimensions.

2) Input: Graph distance. The similarity matrix is provided as an input and consists of a quantitative assessment of the relative similarity of each pair of points in the dataset. For this experiment, we took the corralation matrix as the graph distance matrix.

3) Benefits: Optimize weighted kernel k-means problem by multi-level method. Also, in the trivial case of determining connected graph components, spectral clustering is also related to a spectral version of DBSCAN clustering that finds density-connected components.

## 4.2 Mean Shift

![4 2](https://user-images.githubusercontent.com/91438136/208402114-caec4919-6d38-4a8c-81f3-0ec3100b2c41.PNG)


1) Introduction: MeanShift clustering aims to discover blobs in a smooth density of samples. It is a centroid based algorithm, which works by updating candidates for centroids to be the mean of the points within a given region. These candidates are then filtered in a post-processing stage to eliminate near-duplicates to form the final set of centroids.

2) Input: Distances between points, which is the correlation of data points.

## 4.3 Affinity propagation

![4 3](https://user-images.githubusercontent.com/91438136/208402139-2f008349-ae04-4aa4-884c-20954c1d0fa8.PNG)


1) Introduction: Each item in a dataset can be mapped into Euclidean space using feature values. Affinity propagation depends on a matrix containing Euclidean distances between data points. Since the matrix can quickly become quite large, we should be careful not to take up too much memory.

2) Input:Distances between points, which is the correlation of data points.

## 4.4 Kmeans

![4 4](https://user-images.githubusercontent.com/91438136/208402163-67dbfbe8-31a6-452a-ac54-b24f71ed639a.PNG)


) Introduction: The KMeans algorithm clusters data by trying to separate samples in n groups of equal variance, minimizing a criterion known as the inertia or within-cluster sum-of-squares (see below). This algorithm requires the number of clusters to be specified. It scales well to large numbers of samples and has been used across a large range of application areas in many different fields.

∑ i = 0 n min μ j ∈ C ( | | x i − μ j | | 2 )
2) Input: Graph distance. The similarity matrix is provided as an input and consists of a quantitative assessment of the relative similarity of each pair of points in the dataset. For this experiment, we took the corralation matrix as the graph distance matrix.


In depth analysis:
Clustering analysis for different time periods:
In this part, we repeat the analysis for two more different time periods: 2016 and 2018. To explore the change in the stock markets, we investigate the change of correlations between companies we analyzed in previous parts, and create new clusters based on new set of data.

The first step is to read data from Yahoo Finance using pandas, and use the closing price of these company througout the year to create new dataframes. 
Note that stock price of some companies became unavailable on Yahoo Fiance, so we have dataframes of less columns than the data from 2015. 
This will not influence our results too much becuase those stocks that disappeared have relatively smaller market shares

Hence, we can see the change of the clusters which include the company PCG over these years. In 2015, this company was assigned into a cluster of a few companies, and it's assigned to a much bigger cluster in 2016. However, PCG is in the cluster that only contains itself in 2018. We can also notice that the companies in this cluster in 2016 and 2015 has big differnces, where many different companies joined the cluster but many left as well. The cause may be the change of market trend.

Discussions on drawbacks of this clustering method and possible leader stock in a cluster
One drawback of this clustering method is it tends to crunstruct long and thin clusters because the merging of clusters are performed by simply connecting two elements that has the highest correlation, which means not every pairs of elements in the merged cluster have high correlations. 
Therefore, in each clusters, there might still exist some pairs of companies that are not really significantly correlated. 
Hence, if we want to dicide a leader stock, which its growth could imply the growth of whole cluster, the best option is to choose a stock that is highly correlated with most of the companies in the cluster.
 
