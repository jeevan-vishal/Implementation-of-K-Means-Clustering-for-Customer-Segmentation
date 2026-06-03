# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and preprocess data: Import data, inspect it, and handle missing values if any.
2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.
4. Assign cluster labels to each data point.
5. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Jeevan Vishal.G.D
RegisterNumber: 212224240062
```
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

# Load dataset
customers = pd.read_csv(r"C:\Users\admin\Downloads\Mall_Customers.csv")

# Display sample records
print(customers.head())

# Dataset information
print(customers.info())

# Check missing values
print(customers.isna().sum())

# Selecting required features
X = customers.iloc[:, 3:]

# Finding optimal clusters using Elbow Method
inertia_values = []

for clusters in range(1, 11):
    model = KMeans(
        n_clusters=clusters,
        init='k-means++',
        n_init=10
    )

    model.fit(X)
    inertia_values.append(model.inertia_)

# Plot Elbow Graph
plt.figure(figsize=(6,4))
plt.plot(range(1, 11), inertia_values, marker='o')
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

# Applying KMeans with 5 clusters
k_model = KMeans(n_clusters=5, n_init=10)

cluster_labels = k_model.fit_predict(X)

# Adding cluster labels to dataset
customers["cluster"] = cluster_labels

# Separating clusters
cluster0 = customers[customers["cluster"] == 0]
cluster1 = customers[customers["cluster"] == 1]
cluster2 = customers[customers["cluster"] == 2]
cluster3 = customers[customers["cluster"] == 3]
cluster4 = customers[customers["cluster"] == 4]

# Visualizing clusters
plt.scatter(cluster0["Annual Income (k$)"],
            cluster0["Spending Score (1-100)"],
            c='red', label='cluster1')

plt.scatter(cluster1["Annual Income (k$)"],
            cluster1["Spending Score (1-100)"],
            c='black', label='cluster2')

plt.scatter(cluster2["Annual Income (k$)"],
            cluster2["Spending Score (1-100)"],
            c='blue', label='cluster3')

plt.scatter(cluster3["Annual Income (k$)"],
            cluster3["Spending Score (1-100)"],
            c='green', label='cluster4')

plt.scatter(cluster4["Annual Income (k$)"],
            cluster4["Spending Score (1-100)"],
            c='magenta', label='cluster5')

plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()
```

## Output:

<img width="836" height="677" alt="image" src="https://github.com/user-attachments/assets/017b26ce-bc2f-4b79-bfe7-2ad8527f91c2" />

<img width="817" height="477" alt="image" src="https://github.com/user-attachments/assets/75091b26-a787-4581-a383-c1391f98d27f" />

<img width="1243" height="552" alt="image" src="https://github.com/user-attachments/assets/1547c96f-1d0f-494c-a370-eebf0ecc85b4" />

<img width="1252" height="491" alt="image" src="https://github.com/user-attachments/assets/52c7fbe3-8ee9-404e-a3be-578023217b95" />

<img width="1256" height="576" alt="image" src="https://github.com/user-attachments/assets/e98eff30-f85b-4af7-a238-0eb39145b283" />





## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.

