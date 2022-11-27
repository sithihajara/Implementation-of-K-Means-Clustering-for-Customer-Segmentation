# Implementation of K-Means Clustering for Customer Segmentation

# AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

# EQUIPMENTS REQUIRED:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

# ALGORITHM:
1. Import the necessary packages using import statement.
2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
3. Import KMeans and use for loop to cluster the data.
4. Predict the cluster and plot data graphs.
5. Print the outputs and end the program.

# PROGRAM:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SITHI HAJARA I
Register Number: 212221230102   
*/
```

```
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="yellow",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="pink",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="purple",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

# OUTPUT:
![image](https://user-images.githubusercontent.com/94219582/204132469-a331679e-18b2-4e66-b3b5-353ce2fc0830.png)
![image](https://user-images.githubusercontent.com/94219582/204132477-5fcec0af-3a10-47b1-8607-fde3f329995a.png)
![image](https://user-images.githubusercontent.com/94219582/204132495-315fc095-5b19-418d-ada5-96a35618dd76.png)
![image](https://user-images.githubusercontent.com/94219582/204132503-2a9b92bb-652d-4fb5-bd44-7e82cd6cd0d3.png)
![image](https://user-images.githubusercontent.com/94219582/204132520-975e4736-e2cf-46c2-8efc-2a97aa77acef.png)


# RESULT:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
