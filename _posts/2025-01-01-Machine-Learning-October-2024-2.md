---
layout: post
title: UoE - Machine Learning October 2024 A - EDA Tutorial
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## EDA Tutorial
---

### The Auto-MPG dataset has 398 entries with nine columns. Here are some initial observations:

- Columns include numerical features (e.g., mpg, cylinders, displacement, weight, acceleration, model year) and an origin column, which appears to represent categorical regions.

- horsepower is currently read as an object, which likely contains some non-numeric values (e.g., missing values marked as text).

- Car name is a textual feature that may not be necessary for EDA unless we are interested in specific brands.

### Steps for EDA

1.	Identify missing values: Check for missing or invalid values in columns, especially horsepower.

2.	Estimate Skewness and Kurtosis: For each numeric feature, calculate skewness and kurtosis to understand distribution shapes.

3.	Correlation Heat Map: Generate a heatmap to visualize correlations among numeric features.

4.	Scatter Plot: Create scatter plots to observe relationships among key features.

5.	Replace Categorical Values: Convert the origin column to numerical categories (e.g., 1 for America, 2 for Europe, 3 for Asia).

### Code Spinet

    import pandas as pd

    # Load the Auto-mpg dataset to get a sense of its structure and contents
        file_path = "/content/Unit02 auto-mpg (1).csv"
        auto_mpg_df = pd.read_csv(file_path)

    # Display basic information about the dataset
        auto_mpg_df.info(), auto_mpg_df.head()

Step 1: Identify missing values and explore the 'horsepower' column specifically

    # Check for missing values across the dataset
        missing_values = auto_mpg_df.isnull().sum()

    # Explore unique values in the 'horsepower' column to identify non-numeric entries
        unique_horsepower_values = auto_mpg_df['horsepower'].unique()
    
        missing_values, unique_horsepower_values[:10]  # Show first 10 unique values for inspection

    # Replace any non-numeric values in 'horsepower' with NaN, then convert the column to numeric
        auto_mpg_df['horsepower'] = pd.to_numeric(auto_mpg_df['horsepower'], errors='coerce')

    # Check for new missing values in 'horsepower' after conversion
        missing_values_after_conversion = auto_mpg_df['horsepower'].isnull().sum()
        missing_values_after_conversion

    # Fill missing values in 'horsepower' with the mean of the column
        auto_mpg_df['horsepower'] = auto_mpg_df['horsepower'].fillna(auto_mpg_df['horsepower'].mean())

Step 2: Estimate Skewness and Kurtosis for each numeric column
    
        numeric_columns = auto_mpg_df.select_dtypes(include=['float64', 'int64']).columns
        skew_kurtosis = auto_mpg_df[numeric_columns].agg(['skew', 'kurtosis']).transpose()

    # Display the skewness and kurtosis table
        print(skew_kurtosis)
        import matplotlib.pyplot as plt
    
        import seaborn as sns

Step 3: Generate a correlation heatmap for numeric features
        
        correlation_matrix = auto_mpg_df[numeric_columns].corr()
    
    # Set up the matplotlib figure
        plt.figure(figsize=(10, 8))

    # Draw the heatmap
        sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm", linewidths=.5)
        plt.title("Correlation Heatmap of Numeric Features in Auto MPG Dataset")
        plt.show()

Step 4: Generate scatter plots for various parameter pairs to visualize relationships

    # Plot scatter plots for selected feature pairs
        feature_pairs = [('weight', 'mpg'), ('horsepower', 'mpg'), ('displacement', 'mpg'), ('acceleration', 'mpg')]

        for x_feature, y_feature in feature_pairs:
        plt.figure(figsize=(8, 6))
        plt.scatter(auto_mpg_df[x_feature], auto_mpg_df[y_feature])
        plt.xlabel(x_feature.capitalize())
        plt.ylabel(y_feature.upper())
        plt.title(f"Scatter Plot: {x_feature.capitalize()} vs {y_feature.upper()}")
        plt.show()

Step 5: Replace categorical values in 'origin' with numerical labels for regions
    
    # Assuming 1 = America, 2 = Europe, 3 = Asia
        origin_mapping = {1: "America", 2: "Europe", 3: "Asia"}
        auto_mpg_df['origin'] = auto_mpg_df['origin'].map(origin_mapping)

    # Display the first few rows to confirm the mapping
        auto_mpg_df.head()

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML2-1.png)
![image](/assets/images/banners/ML2-2.png)
![image](/assets/images/banners/ML2-3.png)
![image](/assets/images/banners/ML2-4.png)
![image](/assets/images/banners/ML2-5.png)
![image](/assets/images/banners/ML2-6.png)
![image](/assets/images/banners/ML2-7.png)
![image](/assets/images/banners/ML2-8.png)

---
## Personal Reflection
---

Working on the exploratory data analysis (EDA) tutorial for the Auto-MPG dataset has been an enriching experience that deepened my understanding of data preprocessing and visualization. This process offered both challenges and valuable learning opportunities, particularly in handling real-world data imperfections and uncovering insights from raw datasets.

Handling Missing and Invalid Data
- The first step of identifying missing values and dealing with non-numeric entries in the horsepower column was a crucial learning moment. Initially, I was surprised to find that a numerical column could contain invalid entries, such as text or placeholders for missing data. Replacing these values with NaN and filling them with the mean was a straightforward yet powerful solution. This step reinforced my understanding of the importance of data cleaning as a foundational aspect of any analysis and taught me to always question the validity of raw data.

Skewness and Kurtosis
- Calculating skewness and kurtosis for numeric columns was another enlightening step. By doing so, I gained insights into the distribution of the dataset’s features, understanding which columns were heavily skewed or exhibited extreme tails. For instance, observing skewness in features like mpg and horsepower revealed underlying patterns in fuel efficiency trends, potentially linked to vehicle characteristics or historical factors. This exercise emphasized the importance of understanding data distributions before performing advanced modeling.

Visualization and Correlation Analysis
- Creating a correlation heatmap was particularly impactful. The visual representation of feature relationships allowed me to quickly identify strong correlations, such as the negative relationship between weight and mpg. This step not only highlighted the power of visualization in simplifying complex relationships but also reinforced the importance of selecting the right features for further analysis.

- Scatter plots provided a more granular perspective of these relationships. For example, plotting weight against mpg revealed a clear inverse trend, which could be intuitively explained by heavier cars being less fuel-efficient. These plots demonstrated the value of visual exploration in uncovering nuances that might be missed in numerical summaries alone.

Mapping Categorical Values
- Replacing categorical values in the origin column with meaningful labels (e.g., America, Europe, Asia) was a simple yet impactful step that improved the interpretability of the dataset. This process taught me the importance of transforming categorical data into forms that are both human-readable and useful for analysis. Moreover, it encouraged me to consider how different regions might influence vehicle characteristics, hinting at broader socio-economic and cultural factors.

Reflection on Personal Growth
- This tutorial has enhanced my skills in various aspects of EDA, from cleaning and preparing data to visualizing and interpreting results. Beyond technical skills, it has instilled a deeper appreciation for the iterative nature of data analysis. Each step built on the previous one, and I realized that thorough EDA is not just a preliminary task but a critical foundation for meaningful insights and accurate modeling.

- Additionally, I have grown more confident in navigating Python libraries like Pandas, Matplotlib, and Seaborn, which are essential tools for data analysis. This project also highlighted areas where I could improve, such as automating repetitive tasks and exploring more advanced visualization techniques.

Impact on Professional Development
- The skills honed during this project are directly applicable to real-world data science scenarios. Handling messy data, identifying patterns, and deriving actionable insights are integral to any data-driven role. Moreover, the systematic approach to EDA has reinforced my analytical thinking and problem-solving abilities, which are essential in tackling complex datasets in professional settings.

In conclusion, this EDA tutorial was not only a technical exercise but also a journey of discovery and growth. It has equipped me with practical skills and a structured mindset that will undoubtedly benefit me in future data science endeavors.
