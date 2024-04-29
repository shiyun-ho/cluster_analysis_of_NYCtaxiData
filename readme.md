# Exploratory Data Analysis of New York Taxi Data

## Using Yellow Taxi Data obtained from NYC Taxi Limousine Comission 
<br>

### *Outline* ###
- [Introduction](#Introduction)
    - [Research Questions](#Research-Questions)
    - [Installation Guidelines](#Installation-guidelines)
    - [Table of Contents](#Table-of-contents)
- [Collecting Data](#Collecting-Data)
- [Data Scrubbing](#Data-Scrubbing)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Cluster Analysis](#Cluster-Analysis)
    - [K-means](#K-means-Analysis)
    - [DBSCAN](#DBSCAN)
    - [HDBSCAN](#HDBSCAN)
- [Credits](#Links-to-references)

<br>

### **Introduction** ###

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>


> This project details our foray into conducting exploratory data analysis regarding NYC Yellow Taxi Cab data in June 2016. This code project contains code which can be used for analysing the spatiotemporal aspects of taxi data and visualising the results of clustering through the use of K-means, DBSCAN and HDBSCAN. 

<br><br>

#### **Research Questions** ####

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Our research is primarily driven by curiosities over the spatiotemporal aspects of NYC taxi data. In particular, the code we have used are aimed at addressing the following research questions:

<br>

> 1. What is the temporal pattern of Yellow Taxi data? 
> 2. What regions have the most pickups and dropoffs?
> 3. What are the characteristics of traffic flows? 
> 4. What are the differences between short and long-distance trips?
> 5. Can clustering algorithms to identify a more accurate spatial pattern of Yellow taxi trips?


<br><br>

#### **Installation guidelines** ####

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Prior to running the code files within this project, please make sure that you've installed the following packages within your choice of Integrated Development Environment (IDE). Our code is solely computed within Jupyter Notebook and our code should be compatible with this environment. <br>

> For data cleaning/ scrubbing: `arcpy, pandas, geopandas`

> For Exploratory Data Analysis and Sankey diagram: `matplotlib, numpy, shapefile, zipfile, random, itertools, plotly, math`

> For Cluster Analysis: `tdqm, sklearn, ipywidgets, collections, hdbscan, folium and re`

<br>

*Do note that packages which are previously installed in previous steps will not be indicated in subsequent steps.

<br><br>

#### **Table of contents** ####

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

For quick reference to the files relating to the steps used in this analysis, please refer to the table below:

<br>

| S/N | Step in Analysis | File Name | Description |
| --- | ---------------- | --------  | ----------  |
| 1   | Data Scrubbing/ Cleaning | 01_DataPreprocessing.ipynb | Contains code for data cleaning and code for preliminary data analysis. |
| 2   | Exploratory Data Analysis for month | 02a_ExploratoryDataAnalysisforMonth.ipynb | Contains code for visualising data for the entire month of June 2016. | 
| 3   | Exploratory Data Analysis for day | 02b_ExploratoryDataAnalysisforDay.ipynb | Contains code for visualising data for a single day of 9th June 2016. |
| 4   | Sankey Diagram | 02c_ExploratoryDataSankeyDiagram.ipynb | Contains code to compute taxi flow between boroughs and how to generate Sankey diagram. |
| 5   | Cluster Analysis | 03_ClusterAnalysis.ipynb | Contains code for computing K-means, DBSCAN and HDBSCAN cluster algorithms. |

<br><br>

---

<br>

#### Collecting Data ###

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Data collected for our research can be found on New York City Taxi and Limousine Comission's (NYC TLC) [website](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page). To download the original link and raw data where we have used for analysis, you may go to this [website](https://s3.amazonaws.com/nyc-tlc/trip+data/yellow_tripdata_2016-06.csv).

<br>

---

<br>

#### Data Scrubbing ###

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

To clean data acquired from NYC TLC, you may use the code file  **01_DataPreprocessing.ipynb**.

| Input     | Input File Name | Output | Output File Name | Description | Comments |
| --- | --- | --- | --- | --- | --- |
| Yellow Taxi Data in June 2016 | yellow_tripdata_2016-06.csv  | Cleaned Yellow Taxi Data for the entire month  | data06.csv | Cleaned Yellow Taxi Data after data quality checks. | To be used for EDA: Temporal attributes and determining short and long distance threshold |
|  |   | Extracted one day's worth of cleaned data for Yellow Taxi  | data0609nyc2.csv | Yellow Taxi Data on June 9th 2016 | To be used for EDA and finding spatiotemporal attributes of taxi data |
| Shape File for Taxi Zones |  NYC_taxi_zones.shp | Extracted hour data for Yellow Taxi  | data060908.csv | Yellow Taxi data on 8am, June 9th 2016 | To be used for Cluster Analysis |
|  |   | Taxi data with taxi zone ID number  |  | Joining cleaned taxi data with associated taxi zones | To be used for EDA and Sankey Diagram |
<br>

---
<br>

### Exploratory Data Analysis ###

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

#### EDA for June 2016 ####

<br>

The following table details the input and outputs generated from the code file **02a_ExploratoryDataforMonth.ipynb**. This section addresses the research questions (Q1-4) using data from the month of June 2016. 

<br>

| Input | Input File Name | Output | Description | Comments |
| --- | --- | --- | --- | --- |
| June 2016 Taxi Data | data06.csv | Histogram | Distribution of trip distance for all trips in June 2016 - helps determine threshold distance for short and long distance trips | Month data |
|  |  | Radial Time Plot |  Radial Time Plot for June 2016 | Month data |

<br>

#### EDA for 9th June 2016 ####

<br>

The following table details the input and outputs generated from the code file **02b_ExploratoryDataforDay.ipynb**. This section addresses the research questions (Q1-4) using data from 9th June 2016. 

<br>

| Input | Input File Name | Output | Description | Comments |
| --- | --- | --- | --- | --- |
| 9 June 2016 Taxi Data | data0609nyc2.csv | Highest pickups and dropoffs borough map | Map detailing the boroughs with highest pickups and dropoffs | Day data |
|  |  | Highest pickups and dropoffs zones map | Map detailing the zones with highest pickups and dropoffs | Day data |
|  |  | Highest pickup and dropoffs by zones for short and long distance trips | Map detailing the zones with highest pickups and dropoffs by short and long distance | Day data |
|  |  | Histogram | Passenger count difference for all trips | Day data |
<br>

#### Sankey Diagram ####

<br>

**02c_ExploratoryDataSankeyDiagram.ipynb** contains the code to compute values to measure the magnitude of flow between boroughs in NYC and how to generate a Sankey diagram based on these values. 

<br> 

| Input | Input File Name | Output | Description | Comments |
| --- | --- | --- | --- | --- |
| 9 June 2016 Taxi Data | data0609nyc2.csv | Sankey Diagram | Sankey Diagram illustrating flow of taxis between boroughs in NYC | Flow of taxis on 9 June 2016 |

<br>


<br>

---
<br>

### Cluster Analysis ###

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Code to run cluster analysis for **KMeans**, **DBSCAN**, and **HDBSCAN** can be found in the file **03_ClusterAnalysis.ipynb**. As our preliminary observation and exploration of data shows that data from the entire day can be rather hard to spot clusters, we have opted to use an hour's data instead. The table below shows the input and outputs of the code file. 

<br>

| Input | Input File Name | Output | Description | Comments |
| --- | --- | --- | --- | --- |
| Yellow Taxi Data on 8am, 9th June 2016 | data060908.csv | K=100 clustering result | Clustering result from K-means when k=100 | Refer to K-means Analysis section for more information. |
|  |  | K=2 clustering result | Clustering result from K-means when k=2 |  |
|  |  | DBSCAN result | Clustering result from DBSCAN | Refer to DBSCAN for more information. |
|  |  | HDBSCAN result | Clustering result from HDBSCAN  | Refer to HDBSCAN for more information. |
<br>

#### K-means Analysis ####

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Multiple attempts were made to produce outputs of K-means clustering. At first, we have decided on the use of K=100 as there are multiple taxi zones within NYC and a large number such as this could perhaps reflect the key zones where demand is relatively higher.

<br> 

To ensure that comparison is valid, we also used Silhouette analysis to determine the best K value. We found out that K=2 scores the best amidst all other values but the generated clustering result is insufficient to reflect our objective of meeting specific areas where demand is high. You may choose to change the K value according by changing the following code:

<br>

Here is how you can change the **k value:** <br>

```python 
    #specify X as numpy array of df8 (with only pickup longitude and latitude as float values)
    X = np.array(df8[['pickup_longitude','pickup_latitude']], dtype='float64')

    #specify k
    k = **100**    #change k value here

    #creates model
    model = KMeans(n_clusters=k, random_state=17).fit(X)
    #predict for class values for each instance in the numpy array
    class_predictions = model.predict(X)
    #df8 to now reflect the class prediction values 
    df8[f'CLUSTER_kmeans{k}'] = class_predictions

```
<br>

Here's how you can determine the best K value with Silhouette analysis: 

<br>

```python
    #to define best silhouette score and best k
    best_silhouette, best_k = -1, 0

    #commence for-loop to show progress in calculating silhouette score for each k value
    for k in tqdm(range(2,100)):
        model = KMeans(n_clusters=k, random_state=1).fit(X)  #generate model where k-value is iterative
        class_predictions = model.predict(X)  #predict for class values for each instance in array
        
        curr_silhouette = silhouette_score(X, class_predictions)   #defines current silhouette score for current k value 
        if curr_silhouette > best_silhouette:   #if current score is more than best silhouette score
            best_k = k    #best k value is the current k value
            best_silhouette = curr_silhouette    #then best silhouette score is current score
            
    print(f'K={best_k}')    #prints best k value
    print(f'Silhouette Score: {best_silhouette}')   #prints best silhouette score

```
<br>

Do note that you need to have tqdm package installed to illustrate Silhouette's progress in determining extent and progress of calculating best K value. 

<br>

#### DBSCAN ####

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Parameters for DBSCAN have been decided to be epsilon=0.01, and samples = 30. You may adjust the epsilon (i.e. radius of the neighbourhood around core points) and samples according to what you feel is appropriate. In our case, we have done this clustering algorithm multiple times and chose 30 samples as we feel that it is an appropriate number to reflect sufficient demand for taxis within an area. You may choose to adjust the parameters accordingly depending on the geographic and temporal context you are looking at. 

<br>

Here is how you can change the **parameters epsilon and samples:** <br>

```python
    # create the model of DBSCAN
    model = DBSCAN(eps=***0.01***, min_samples=***30***).fit(X)    #change eps = ??? and min_samples=??? accordingly
    # fit the model to data
    class_predictions = model.labels_
    # assign the value of class_prediction to the field of CLUSTERS_DBSCAN
    df8['CLUSTERS_DBSCAN'] = class_predictions

```
<br>

#### HDBSCAN ####

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Our choice of parameters is inherited from our DBSCAN analysis earlier to reflect the intrisic differences in clustering between the two density based clustering algorithms. After attempting multiple times, we decided on the parameters where epsilon=0.01, minimum samples = 30, and minimum cluster size=60. You may also choose to adjust the parameters according to best reflect clusters. 

<br>

Here is how you can change the **parameters:** <br>

```python
    # create  HDBSCAN clustering model 
    model = hdbscan.HDBSCAN(min_cluster_size=***60***, min_samples= ***30***, cluster_selection_epsilon=***0.01***)   #change parameters here
    # fit the model to data 
    class_predictions = model.fit_predict(arr8pu)
    # add the cluster group id number from the model to the original data frame
    df8['CLUSTERPU8_HDBSCAN'] = class_predictions

```
<br>

---

<br>

### References ###

<br>

[(Back to top)](#Exploratory-Data-Analysis-of-New-York-Taxi-Data)

<br>

Ari, A. (n.d.). Clustering Geolocation Data Intelligently in Python. Coursera. Retrieved April 21, 2021, from <span>www.</span>coursera<span>.org/</span>projects/clustering-geolocation-data-intelligently-python

<br>

Hsu, C. (2018, May 14). Analyze the NYC Taxi Data. An Explorer of Things. Retrieved March 22, 2021 from chih-ling-hsu.github.io<span>/</span>2018/05/
14/NYC



<br>

