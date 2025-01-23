---
layout: post
title: UoE - Machine Learning October 2024 A - K-Means Clustering Tutorial
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## K-Means Clustering Tutorial
---

### Pre-Processing

    import pandas as pd
    
    # Load the datasets
        iris_path = '/content/Unit06 iris.csv'
        wine_path = '/content/Unit06 wine.csv'
        weatherAUS_path = '/content/Unit06 weatherAUS.csv'

        iris_data = pd.read_csv(iris_path)
        wine_data = pd.read_csv(wine_path)
        weather_data = pd.read_csv(weatherAUS_path)

    # Display basic information about the datasets to understand their structure
        iris_info = iris_data.info()
        wine_info = wine_data.info()
        weather_info = weather_data.info()

        iris_head = iris_data.head()
        wine_head = wine_data.head()
        weather_head = weather_data.head()

        iris_info, iris_head, wine_info, wine_head, weather_info, weather_head

### Task A: Iris Dataset

    from sklearn.cluster import KMeans
    from sklearn.preprocessing import LabelEncoder
    from sklearn.metrics import adjusted_rand_score
    import numpy as np

    # Preprocessing
        iris_features = iris_data.drop('species', axis=1)
        iris_labels = LabelEncoder().fit_transform(iris_data['species'])

    # K-Means Clustering with K=3
        kmeans_iris = KMeans(n_clusters=3, random_state=42)
        iris_clusters = kmeans_iris.fit_predict(iris_features)

    # Evaluate clustering using Adjusted Rand Index (ARI)
        ari_iris = adjusted_rand_score(iris_labels, iris_clusters)

    # Display results
        iris_results = {
            "Cluster Centers": kmeans_iris.cluster_centers_,
            "ARI (K=3)": ari_iris
            }
        iris_results

### Task B: Wine data

    # Preprocessing
        wine_features = wine_data.drop('Wine', axis=1)
        wine_labels = wine_data['Wine'] - 1  # Convert wine labels to 0, 1, 2

    # K-Means Clustering with K=3
        kmeans_wine = KMeans(n_clusters=3, random_state=42)
        wine_clusters = kmeans_wine.fit_predict(wine_features)

    # Evaluate clustering using Adjusted Rand Index (ARI)
        ari_wine = adjusted_rand_score(wine_labels, wine_clusters)

    # Display results
        wine_results = {
            "Cluster Centers": kmeans_wine.cluster_centers_,
            "ARI (K=3)": ari_wine
            }
        wine_results

### Task C: WeatherAUS Dataset

    import matplotlib.pyplot as plt
    from sklearn.decomposition import PCA

    # Preprocessing
        weather_features = weather_data.select_dtypes(include=['float64']).dropna()  # Use only numeric columns and drop NaNs

    # Perform PCA for 2D visualization
        pca = PCA(n_components=2)
        weather_pca = pca.fit_transform(weather_features)

    # Run K-Means for K values from 2 to 6
        k_values = range(2, 7)
        weather_results = {}

    for k in k_values:
        kmeans_weather = KMeans(n_clusters=k, random_state=42)
        clusters_weather = kmeans_weather.fit_predict(weather_features)
        weather_results[k] = {
            "Cluster Centers": kmeans_weather.cluster_centers_,
            "Inertia": kmeans_weather.inertia_
        }

    # Plot the results for visualization
        plt.figure(figsize=(8, 6))
        plt.scatter(weather_pca[:, 0], weather_pca[:, 1], c=clusters_weather, cmap='viridis', s=10)
        plt.title(f'K-Means Clustering with K={k}')
        plt.xlabel('PCA Component 1')
        plt.ylabel('PCA Component 2')
        plt.colorbar(label='Cluster Label')
        plt.show()

        weather_results

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML7-1.png)
![image](/assets/images/banners/ML7-2.png)
![image](/assets/images/banners/ML7-3.png)
![image](/assets/images/banners/ML7-4.png)
![image](/assets/images/banners/ML7-5.png)
![image](/assets/images/banners/ML7-6.png)
![image](/assets/images/banners/ML7-7.png)
![image](/assets/images/banners/ML7-8.png)
![image](/assets/images/banners/ML7-9.png)
![image](/assets/images/banners/ML7-10.png)
![image](/assets/images/banners/ML7-11.png)

---
## Personal Reflection
---

Engaging with the K-Means clustering tutorial provided me with valuable insights into the practical applications of unsupervised learning techniques across diverse datasets. Each task offered a unique challenge, deepening my understanding of clustering, preprocessing, and evaluating the results.

Task A: Iris Dataset
- Working with the Iris dataset was an excellent starting point because of its simplicity and well-structured format. Applying K-Means clustering and evaluating the results using the Adjusted Rand Index (ARI) helped solidify my understanding of clustering accuracy in comparison to true labels. The ARI score provided a quantitative measure to assess how well the clustering aligned with the actual species.

- This exercise reinforced the importance of preprocessing, particularly label encoding for categorical data. Additionally, observing how the algorithm grouped data based on the features highlighted the power of K-Means in finding natural patterns. It was satisfying to see that K-Means could effectively separate the species, even without labels during training.

Task B: Wine Dataset
- The Wine dataset introduced a more complex scenario due to the increased number of features. Dropping the target column and converting labels for evaluation required additional preprocessing steps, which challenged me to think more critically about data preparation.

- Evaluating the clusters using ARI once again demonstrated the algorithm’s ability to find meaningful patterns. However, I noticed that the clustering results were slightly less aligned with the actual labels compared to the Iris dataset. This experience highlighted how the complexity and dimensionality of data can affect clustering performance. It also made me curious about dimensionality reduction techniques, such as Principal Component Analysis (PCA), to simplify such datasets before clustering.

Task C: WeatherAUS Dataset
- The WeatherAUS dataset presented the most challenging task due to its size, complexity, and missing values. Using only numeric columns and dropping rows with missing values taught me the importance of selecting relevant features and handling incomplete data carefully.

- Performing PCA for dimensionality reduction before visualizing the clusters provided a fresh perspective on how high-dimensional data can be effectively summarized in two dimensions. Running K-Means for different values of K (from 2 to 6) helped me understand how the number of clusters impacts both the algorithm's inertia (a measure of within-cluster variance) and the resulting visualizations.

- Visualizing the clustering results was especially insightful. It demonstrated how K-Means attempts to group data points into distinct clusters and how the choice of K affects the grouping. This hands-on experience with PCA and visualization tools highlighted the practical steps necessary to interpret clustering results in real-world datasets.

Key Learnings
- Preprocessing Matters: This tutorial emphasized the importance of preprocessing for successful clustering. Tasks like handling missing values, label encoding, and feature selection were crucial for producing meaningful results.

- Cluster Evaluation: Using ARI for the Iris and Wine datasets provided a clear metric to assess clustering quality, while observing inertia for the WeatherAUS dataset helped evaluate the performance of different K values.

- Dimensionality Reduction: Applying PCA to the WeatherAUS dataset showed me the value of simplifying high-dimensional data for both visualization and clustering, particularly in datasets with many features.

- K-Means Limitations: Throughout the tasks, I noticed K-Means struggles with datasets containing overlapping clusters, high dimensionality, or non-spherical cluster shapes. These limitations highlighted the importance of choosing the right algorithm for the data and using evaluation metrics to validate results.

Challenges Faced
- The most significant challenge was handling the WeatherAUS dataset due to its size and missing values. Cleaning and preparing the data required careful consideration to ensure the clustering results were reliable. Additionally, interpreting the PCA-reduced clusters required me to think critically about how dimensionality reduction impacts the original data structure.

- Another challenge was deciding on the optimal number of clusters (K) for each dataset. While the Iris and Wine datasets had predefined clusters for comparison, the WeatherAUS dataset required experimentation with different values of K, which was both a learning opportunity and a challenge.

Professional Development
- This tutorial enhanced my technical skills in using Python libraries such as pandas, sklearn, and matplotlib for clustering tasks. I also gained a deeper understanding of the K-Means algorithm, its iterative nature, and how to evaluate clustering performance. These skills are directly applicable to real-world scenarios, such as customer segmentation, anomaly detection, and exploratory data analysis.

- Beyond technical skills, this exercise reinforced the importance of a structured approach to data analysis, from preprocessing and modeling to evaluation and visualization. These learnings will undoubtedly benefit me in future data science projects, where understanding data patterns is critical.

Moving Forward
- This tutorial has inspired me to explore more advanced clustering techniques, such as DBSCAN and hierarchical clustering, to address the limitations of K-Means. I am also interested in experimenting with hybrid approaches, such as combining clustering with classification or regression tasks, to solve more complex problems.

- Additionally, I plan to explore practical use cases for clustering in fields like healthcare, marketing, and finance, where grouping similar data points can provide actionable insights.

In conclusion, the K-Means clustering tutorial was an engaging and enriching experience that bridged theoretical knowledge with practical applications. It strengthened my analytical and technical skills while highlighting areas for further exploration and growth in unsupervised learning.
