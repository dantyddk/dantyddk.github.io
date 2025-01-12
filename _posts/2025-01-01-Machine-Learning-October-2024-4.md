---
layout: post
title: UoE - Machine Learning October 2024 A - Linear Regression with Scikit-Learn
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Linear Regression with Scikit-Learn
---

### Pre-Processing

    # Importing necessary libraries
        import pandas as pd
        import matplotlib.pyplot as plt
        from sklearn.linear_model import LinearRegression
        from sklearn.model_selection import train_test_split
        from sklearn.metrics import mean_squared_error, r2_score
        from scipy.stats import pearsonr

    # Load datasets
        population_path = "/content/Unit04 Global_Population.csv"
        gdp_path = "/content/Unit04 Global_GDP.csv"

        global_population_data = pd.read_csv(population_path)
        global_gdp_data = pd.read_csv(gdp_path)

### Task A: Correlation
Pre-process the data – mean population of each country and mean per capita GDP (from 2001 to 2021) by making some arrangements for the missing values (HINT: You will need to use the datasets Global_GDP.csv and Global_Population.csv). Investigate any correlation between the mean population of each country and the mean per capita GDP (from 2001 to 2021). Very briefly, interpret the generated plot. Evaluate the Pearson Correlation Coefficient.

    # Select years 2001 to 2020
        adjusted_years = [str(year) for year in range(2001, 2021)]
    
    # Convert relevant columns to numeric for mean calculation
        global_population_data[adjusted_years] = global_population_data[adjusted_years].apply(pd.to_numeric, errors='coerce')
        global_gdp_data[adjusted_years] = global_gdp_data[adjusted_years].apply(pd.to_numeric, errors='coerce')
    
    # Compute mean population and GDP for the adjusted years
        global_population_data['Mean_Population'] = global_population_data[adjusted_years].mean(axis=1, skipna=True)
        global_gdp_data['Mean_GDP'] = global_gdp_data[adjusted_years].mean(axis=1, skipna=True)

    # Merge datasets on Country Name and Country Code
        merged_data = pd.merge(
            global_population_data[['Country Name', 'Country Code', 'Mean_Population']],
            global_gdp_data[['Country Name', 'Country Code', 'Mean_GDP']],
            on=['Country Name', 'Country Code'],
            how='inner'
        )

    # Calculate mean per capita GDP
        merged_data['Mean_Per_Capita_GDP'] = merged_data['Mean_GDP'] / merged_data['Mean_Population']

    # Clean data by removing rows with missing values
        cleaned_data = merged_data.dropna(subset=['Mean_Population', 'Mean_Per_Capita_GDP'])

    # Correlation Analysis
        x_population = cleaned_data['Mean_Population']
        y_per_capita_gdp = cleaned_data['Mean_Per_Capita_GDP']

    # Scatter plot
        plt.figure(figsize=(10, 6))
        plt.scatter(x_population, y_per_capita_gdp, alpha=0.6, edgecolors='k')
        plt.title('Correlation between Mean Population and Mean Per Capita GDP (2001-2020)')
        plt.xlabel('Mean Population (2001-2020)')
        plt.ylabel('Mean Per Capita GDP (2001-2020)')
        plt.grid(alpha=0.3)
        plt.show()

    # Pearson Correlation Coefficient
        correlation_coefficient, p_value = pearsonr(x_population, y_per_capita_gdp)
        print(f"Pearson Correlation Coefficient: {correlation_coefficient}")
        print(f"P-value: {p_value}")
**Preprocessing Steps**:

- Data Selection: Used data from Global_Population.csv and Global_GDP.csv for years 2001 to 2020 (data for 2021 is unavailable in GDP data).

- Handling Missing Values: Applied mean imputation to handle missing data and computed:

- Mean Population: The average population of each country between 2001 and 2020.

- Mean GDP: The average GDP of each country between 2001 and 2020.

- Mean Per Capita GDP: Calculated as Mean GDP / Mean Population. Correlation

**Analysis**:

- Scatter Plot: Visualized the relationship between the mean population and mean per capita GDP.

- Pearson Correlation Coefficient: Found a weak negative correlation (𝑟 = − 0.0996, 𝑝 = 0.1113). This indicates no significant linear relationship between mean population and mean per capita GDP.

### Task B: Regression
Perform linear regression, where the independent variable is the mean population of each country (from 2001 to 2021) and dependent variable is mean per capita GDP (from 2001 to 2021). Be prepared to discuss your agreed results during the seminar session.

    # Prepare data for regression
        X = cleaned_data[['Mean_Population']]
        y = cleaned_data['Mean_Per_Capita_GDP']

    # Split data into training and testing sets
        X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
    
    # Create and train linear regression model
        model = LinearRegression()
        model.fit(X_train, y_train)

    # Make predictions
        y_pred = model.predict(X_test)

    # Evaluate model
        mse = mean_squared_error(y_test, y_pred)
        r2 = r2_score(y_test, y_pred)
        slope = model.coef_[0]
        intercept = model.intercept_

        print(f"Mean Squared Error: {mse}")
        print(f"R² Score: {r2}")
        print(f"Slope (Coefficient): {slope}")
        print(f"Intercept: {intercept}")

    # Regression Visualization
        plt.figure(figsize=(10, 6))
        plt.scatter(X_test, y_test, color='blue', label='Actual values', alpha=0.6, edgecolors='k')
        plt.plot(X_test, y_pred, color='red', linewidth=2, label='Regression line')
        plt.title('Linear Regression: Mean Population vs Mean Per Capita GDP')
        plt.xlabel('Mean Population (2001-2020)')
        plt.ylabel('Mean Per Capita GDP (2001-2020)')
        plt.legend()
        plt.grid(alpha=0.3)
        plt.show()

**Linear Regression Analysis**:

- Independent Variable: Mean population (2001–2020).

- Dependent Variable: Mean per capita GDP (2001–2020).

**Model Evaluation**:

- Mean Squared Error (MSE): 406,871,388.72

- R² Score: 0.009 (indicating a poor fit; only 0.9% of variance in per capita GDP is explained by population).

- Slope (Coefficient): −2.33×10 −6 (suggesting a negligible decrease in per capita GDP with population increase).

- Intercept: 15,164.06 (baseline per capita GDP when population is zero).

**Interpretation**: The regression analysis shows that the population size has almost no predictive power for per capita GDP, with the relationship being weak and insignificant.

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML4-1.png)
![image](/assets/images/banners/ML4-2.png)
![image](/assets/images/banners/ML4-3.png)
![image](/assets/images/banners/ML4-4.png)
![image](/assets/images/banners/ML4-5.png)
![image](/assets/images/banners/ML4-6.png)

---
## Personal Reflection
---

Engaging with the Linear Regression exercise using Scikit-Learn allowed me to deepen my understanding of predictive modeling, particularly in applying machine learning techniques to real-world data. The process of working with the population and GDP datasets presented valuable lessons about data preprocessing, correlation analysis, and regression modeling.

Data Preprocessing
- The preprocessing phase highlighted the importance of cleaning and preparing data before analysis. Handling missing values through mean imputation for both population and GDP datasets was an essential step, ensuring that the analysis was robust and reliable. Calculating mean population and per capita GDP over a 20-year span required thoughtful aggregation and handling of missing data, reinforcing the necessity of a meticulous approach in dealing with real-world datasets.

- The merging of datasets and computation of new metrics, such as per capita GDP, underscored how small transformations can significantly improve the quality and interpretability of data. This step also demonstrated how critical it is to align data from different sources to draw meaningful insights.

Correlation Analysis
- The correlation analysis revealed a weak negative relationship (𝑟 = −0.0996) between mean population and mean per capita GDP. This result surprised me, as I had intuitively expected a stronger connection, given that countries with larger populations often have diverse economic structures. However, the weak correlation emphasized that economic prosperity (measured by per capita GDP) is influenced by far more complex factors than population alone, such as resource distribution, governance, and infrastructure.

- Creating scatter plots to visualize this relationship was particularly insightful. The visualization allowed me to better understand the lack of a clear pattern between population size and economic performance, reinforcing the importance of using both numerical and graphical analyses to draw accurate conclusions.

Linear Regression Modeling
- Performing linear regression with Scikit-Learn was an engaging experience. Splitting the dataset into training and testing subsets highlighted the significance of ensuring that models generalize well to unseen data. The resulting model, however, had a very low R² score (0.009), indicating that population size alone explained less than 1% of the variation in per capita GDP. This confirmed that the relationship between these two variables is minimal and not significant in predicting economic performance.

- The visualization of the regression line on the scatter plot helped solidify my understanding of how linear regression models work. Observing the nearly flat slope of the regression line emphasized the weak relationship, providing a visual complement to the numerical results.

Challenges and Insights
- One challenge I faced was managing the complexity of the datasets, particularly ensuring that data types were compatible for computation and analysis. Another challenge was interpreting the results in a meaningful way. Initially, I was disappointed by the weak correlation and poor regression fit, but I later realized that these findings themselves are valuable insights. Not every analysis yields strong relationships, and recognizing weak or insignificant findings is an essential part of data science.

- This exercise also reinforced the importance of critical thinking when interpreting results. The weak correlation and poor regression fit indicated that other variables, such as infrastructure, education, and technological advancement, might be more influential factors in determining per capita GDP. This realization broadened my perspective on economic data analysis.

Professional Development
- This activity has significantly enhanced my technical skills in using Scikit-Learn for regression analysis, particularly in applying machine learning models to structured datasets. It also strengthened my ability to evaluate model performance using metrics like R² and mean squared error, which are critical for assessing the reliability and utility of predictive models.

- Beyond technical skills, this exercise improved my analytical mindset. I learned to appreciate the nuances of working with real-world data, including its limitations and the complexity of relationships between variables. These skills are directly applicable to professional roles in data analysis and machine learning.

Future Applications
- This experience has motivated me to explore more complex regression techniques, such as multiple regression with additional predictors and non-linear models, to better capture intricate relationships. I am also keen to delve deeper into feature engineering and selection to identify variables that have a stronger influence on outcomes like per capita GDP.

In conclusion, the Linear Regression exercise with Scikit-Learn was an invaluable learning experience. It provided practical insights into data preprocessing, correlation analysis, and predictive modeling while reinforcing the importance of critical evaluation and interpretation of results. These lessons will serve as a strong foundation for future projects in machine learning and data science.
