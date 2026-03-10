# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import required libraries.
2. Load the dataset.
3. Select relevant features (Annual Income & Spending Score).
4. Use the Elbow Method to find optimal number of clusters.
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SUNDARESH K
RegisterNumber: 212225220111
```
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

data = pd.read_csv("/content/Mall_Customers.csv")

print(data.head())

print(data.info())

print(data.isnull().sum())

wcss = []

for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", random_state=42)
    kmeans.fit(data.iloc[:, 3:5])   
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

km = KMeans(n_clusters=5, init="k-means++", random_state=42)
km.fit(data.iloc[:, 3:5])

y_pred = km.predict(data.iloc[:, 3:5])

data["cluster"] = y_pred

df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="Cluster 4")

plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()
```
## Output:
<img width="903" height="164" alt="Screenshot 2026-03-10 093023" src="https://github.com/user-attachments/assets/fcc932cb-f6be-4a30-8ea0-1a31967dacb1" />
<img width="769" height="341" alt="Screenshot 2026-03-10 093030" src="https://github.com/user-attachments/assets/6ceca2f2-c501-4365-bb23-eb4f38087780" />
<img width="668" height="169" alt="Screenshot 2026-03-10 093038" src="https://github.com/user-attachments/assets/4c7deb58-7cd9-4feb-8742-1e6381cf6edf" />
<img width="1145" height="683" alt="image" src="https://github.com/user-attachments/assets/bdc05546-bd0a-4c88-8a3b-90fb3cac24d5" />
<img width="1170" height="677" alt="image" src="https://github.com/user-attachments/assets/4c3dab27-3b05-4bd4-9428-a24eda98647c" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
