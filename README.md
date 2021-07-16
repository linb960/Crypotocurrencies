# Crypotocurrencies

## Overview
People are quickly jumping on the Cryptocurrency bandwagon.  Most people know of BitCoin, Ethereum and Doge because of the press they have received and their popularity.  This project starts with a dataset of over 1200 cryptocurrencies and narrows the field to those being traded and mined.  Ulitimately the remaining  coins are grouped together using unsupervised machine learning to visualize the current state of affairs in cryptocurrencies.

## Results
### Preprocessing
The dataset has over 1200 cryptocurrencies in it.  These steps were taken to preprocess the data for analysis:
- Read in the dataset and converted it to a DataFrame.
- Determine which are currently being traded.
- Removed all rows that had null values.
- Filtered data and removed rows where coins mined was less than zero.
- Converted columns of data using get_dummies() to create variables for the text features.
- Used StandardScaler fit_transform() to standarize the features of the DataFrame and create a new scaled DataFrame.

### Principle Component Analysis (PCA)
Using PCA the scaled DataFrame dimensions were reduced to three principal components. The new DataFrame was created from these three components.

### K-Means 
K-Means is used to represent the number of clusters there will be when clustering data in unsupervised machine learning.  The K value is unknown so an Elbow Curve is plotted to find the K used in our Analysis.  The resulting Elbow Curve looks like the following and shows the K value will work best at 4. <br>
<img width="897" alt="Screen Shot 2021-07-16 at 4 38 07 PM" src="https://user-images.githubusercontent.com/79341217/126011010-dc91b6f0-f6cd-4c8e-9123-99f1823614fb.png"><br>

With the K value of 4 we can now take the preprocessed DataFrame and the DataFrame created in our PCA and combine them into one DataFrame.  We'll also add the Coin Names and the Class from the model.labels_ to get the Clustered DataFrame.

### Visualize the Data
The clustered data looks like in our 3D figure:
<img width="918" alt="Screen Shot 2021-07-16 at 5 00 59 PM" src="https://user-images.githubusercontent.com/79341217/126012703-7a7c71c5-ea02-4e6d-bb27-c2ef7eeeb4e5.png">
<br>
After creating the 3D figure a table of the **532** tradable cryptocurriences is created that will allow for sorting.  This helps us to see that there are only 5 types of Coins in group 3 and 1 coin, BitTorrent in group 1.
<br>
Finally using MinMaxScaler().fit_transform the scales of the columns for TotalCoinSupply and TotalCoinsMined become between 1 and 0.  This data is then used to create this scatter plot:
<img width="677" alt="Screen Shot 2021-07-16 at 5 12 35 PM" src="https://user-images.githubusercontent.com/79341217/126013287-529eb297-a8cd-4fcf-a194-1e7311b318dd.png">
<br>

### Conclusion
Most people only know of a few cryptocurrencies yet this analysis shows that there are 532 tradable coins currently.  Of these coins we used unsupervised machine learning to help us visualize the data on these coins.  If I were to redo the analysis I would remove the 6 coins from the set of 532 that skewed the tables.  This might help to see the data a little clearer.
