---
layout: post
title: UoE - Machine Learning October 2024 A - Clustering
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, essay, Module E-Portfolio Learning Activities]
---
---
## Clustering
---

### Analyzing K-Means Clustering through Visualizations

Both animations provided unique insights into the K-Means clustering algorithm, highlighting its iterative nature, reliance on centroid initialization, and optimization process.

The K-Means Algorithm is an iterative algorithm that splits a data set into non-overlapping subgroups called clusters. The number of clusters created is determined by the value of k, a hyperparameter chosen before the algorithm runs. 

Steps for K-Means

1. Choose the number of clusters(k) you wish to put the data into

2. Randomly initialise k points; these are called centroids

3. Identify the points closest to each centroid

4. Calculate the mean of the points in each cluster and move each centroid to that mean point

5. Repeat Step 3and four until the centroid value stays the same

### Shabal’s Visualization:

This animation clearly illustrates the iterative process of K-Means. Random initialization is followed by repeated assignment of points to the nearest centroid and centroid updates until convergence. The visualization demonstrates how centroids move to minimize intra-cluster variance and maximize inter-cluster separation. While intuitive, it does not delve into how initialization choices affect clustering outcomes. 

![image](/assets/images/banners/ML5-1.jpg)
![image](/assets/images/banners/ML5-2.jpg)
![image](/assets/images/banners/ML5-3.jpg)
![image](/assets/images/banners/ML5-4.jpg)
![image](/assets/images/banners/ML5-5.jpg)

### Naftali Harris’s Visualization:

This animation complements Shabal’s by emphasizing the sensitivity of K-Means to centroid initialization. The “I’ll choose” option shows how poor placement of centroids can lead to suboptimal clustering. The "Uniform Points" option highlights the algorithm’s strength in symmetrical datasets but also reveals its limitations, such as handling overlapping clusters. The dynamic visualization of distances provides deeper insight into the assignment step. 

![image](/assets/images/banners/ML5-6.jpg)
![image](/assets/images/banners/ML5-7.jpg)
![image](/assets/images/banners/ML5-8.jpg)

### Key Learnings from Both:

The animations collectively reinforce the core logic of K-Means: iterative assignment and update steps leading to convergence. They also highlight K-Means’ reliance on good initialization and its sensitivity to overlapping clusters or non-spherical shapes. Together, they provide a nuanced understanding of the algorithm, bridging theory and practice.

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML5-9.png)

---
## Personal Reflection
---

Exploring K-Means clustering through animations and practical insights provided me with a deeper understanding of this essential machine learning algorithm. Both Shabal’s and Naftali Harris’s visualizations offered unique perspectives, transforming abstract concepts into tangible and dynamic representations.

Understanding the K-Means Process
- The visualizations helped solidify my understanding of how K-Means iteratively works. From the random initialization of centroids to the continuous assignment of data points and centroid updates, I could clearly see how the algorithm converges toward a solution. The simplicity of the algorithm’s steps belies its power in grouping data effectively, making it an excellent starting point for understanding clustering techniques.

- I was particularly fascinated by how centroids "moved" toward the mean of their respective clusters with each iteration. This dynamic aspect of K-Means, which I had previously understood only theoretically, came to life through the animations, making the optimization process much more intuitive.

Insights into Initialization Sensitivity
- Naftali Harris’s visualization emphasized an aspect of K-Means that I had not fully appreciated before: its sensitivity to centroid initialization. Poor initial placement can lead to suboptimal clustering or convergence to a local minimum, resulting in inaccurate or misleading outcomes. Watching how centroid placement influenced the final clusters deepened my appreciation for techniques like K-Means++ initialization, which aim to optimize the starting points.

- This realization also taught me the importance of running K-Means multiple times with different random seeds to ensure robustness. It highlighted that while K-Means is simple to implement, achieving reliable results requires thoughtful consideration of its initialization and hyperparameter selection.

Challenges with K-Means
- Both visualizations revealed some of the inherent limitations of K-Means. The algorithm works well for symmetrical, well-separated clusters, as shown in Harris’s “Uniform Points” example. However, it struggles with overlapping clusters, non-spherical shapes, or datasets with varying cluster densities. These limitations reinforced the importance of understanding the data before applying K-Means or any clustering technique.

- This also opened my eyes to the importance of alternative clustering methods, such as DBSCAN or hierarchical clustering, when working with complex datasets. It reminded me that no single algorithm fits all scenarios, and the choice of method should be guided by the data’s characteristics.

Practical Takeaways
- The animations highlighted the iterative and dynamic nature of K-Means, bridging the gap between theory and practice. They emphasized the importance of hyperparameter tuning, such as selecting the appropriate number of clusters (k), and the risks associated with poor initialization. I also realized the need for evaluation metrics like the silhouette score to assess clustering quality beyond visual inspection.

- These insights have significantly enhanced my confidence in applying K-Means in real-world scenarios. I now feel more equipped to not only use the algorithm but also critically evaluate its results and identify scenarios where it might fall short.

Professional Growth
- This experience has strengthened my skills in unsupervised learning and clustering techniques, which are critical in data exploration and segmentation tasks. It also reinforced my analytical thinking, as I learned to interpret the outcomes of the clustering process and consider the algorithm’s limitations.

- Furthermore, visualizations like these have inspired me to incorporate similar tools in future projects to better communicate complex concepts to non-technical stakeholders. They’ve shown me the value of making technical processes accessible and engaging.

Moving Forward
- Moving forward, I plan to explore advanced clustering techniques and learn how to combine K-Means with dimensionality reduction methods like PCA for high-dimensional datasets. I am also interested in experimenting with real-world datasets to better understand the nuances of clustering in practice.

In conclusion, analyzing K-Means through these visualizations was an eye-opening experience. It not only enhanced my theoretical understanding but also gave me practical insights into applying and evaluating the algorithm effectively. These lessons will undoubtedly enrich my journey in machine learning and data science.

