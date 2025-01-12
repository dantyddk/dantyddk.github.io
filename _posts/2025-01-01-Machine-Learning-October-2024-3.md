---
layout: post
title: UoE - Machine Learning October 2024 A - Correlation and Regression
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Correlation and Regression
---

### Code Spinet

     # calculate the Pearson's correlation between two variables
        from numpy import mean
        from numpy import std
        from numpy import cov
        from numpy.random import randn
        from numpy.random import seed
        from matplotlib import pyplot as plt
        import seaborn as sns
        from sklearn.metrics import r2_score
        import numpy
        import matplotlib.pyplot as plt
        from scipy import stats
        import pandas
        from sklearn import linear_model
        from scipy.stats import pearsonr
     
     # Seed random number generator
        seed(1)

     # Prepare data
        data1 = 100 * randn(1000) + 100
        data2 = data1 + (10 * randn(1000) + 50)

     # Calculate covariance matrix
        covariance = cov(data1, data2)

     # Calculate Pearson's correlation
        corr, _ = pearsonr(data1, data2)

     # Plot
        plt.scatter(data1, data2)
        plt.show()

     # Summarize
        print('data1: mean=%.3f stdv=%.3f' % (mean(data1), std(data1)))
        print('data2: mean=%.3f stdv=%.3f' % (mean(data2), std(data2)))
        print('Covariance: %.3f' % covariance[0][1])
        print('Pearsons correlation: %.3f' % corr)
-.
      
     # Create the arrays that represent the values of the x and y axis

        x = [8, 10, 2, 5, 6, 14, 3, 9, 11, 12, 4, 7, 6]
        y = [89, 76, 77, 78, 81, 96, 113, 77, 84, 88, 97, 75, 96]

     # Execute a method that returns some important key values of Linear Regression
        slope, intercept, r, p, std_err = stats.linregress(x, y)

      # Measure the correlation
        corr, _ = stats.pearsonr(x, y)
        print('Pearsons correlation: %.3f' % corr)

     # Create a function that uses the slope and intercept values to return a new value.
     # This new value represents where on the y-axis the corresponding x value will be placed
        def myfunc(x):
            return slope * x + intercept

     # Run each value of the x array through the function. This will result in a new array with new values for the y-axis
        mymodel = list(map(myfunc, x))

     # Draw the original scatter plot & the line of linear regression
        plt.scatter(x, y)
        plt.plot(x, mymodel)
        plt.show()
-.

        df = pandas.read_csv("/content/cars.csv")

        X = df[['Weight', 'Volume']]
        y = df['CO2']

        regr = linear_model.LinearRegression()
        regr.fit(X, y)

     # predict the CO2 emission of a car where the weight is 2300kg, and the volume is 1300cm3:
        predictedCO2 = regr.predict([[2300, 1300]])
        print(predictedCO2)
-.
        
        print(regr.coef_)
-.
        
        predictedCO2 = regr.predict([[3300, 1300]])
        print(predictedCO2)
-.

        x = [11,12,13,15,16,17,18,19,20,22,23,24,25,26,28,29,31,32]
        y = [100,90,80,60,60,55,60,65,70,70,75,76,78,79,90,99,99,100]

     # NumPy has a method that lets us make a polynomial model
        mymodel = numpy.poly1d(numpy.polyfit(x, y, 3))

     # Specify how the line will display, we start at position 1, and end at position 22
        myline = numpy.linspace(1, 22, 100)

        plt.scatter(x, y)
        plt.plot(myline, mymodel(myline))
        plt.show()
-.
        
        x = [11,12,13,15,16,17,18,19,20,22,23,24,25,26,28,29,31,32]
        y = [100,90,80,60,60,55,60,65,70,70,75,76,78,79,90,99,99,100]
        mymodel = numpy.poly1d(numpy.polyfit(x, y, 3))
        print(r2_score(y, mymodel(x)))
-.
        
        x = [11,12,13,15,16,17,18,19,20,22,23,24,25,26,28,29,31,32]
        y = [100,90,80,60,60,55,60,65,70,70,75,76,78,79,90,99,99,100]
        mymodel = numpy.poly1d(numpy.polyfit(x, y, 3))
        speed = mymodel(17)
        print(speed)
---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML3-1.png)
![image](/assets/images/banners/ML3-2.png)
![image](/assets/images/banners/ML3-3.png)
![image](/assets/images/banners/ML3-4.png)
![image](/assets/images/banners/ML3-5.png)

---
## Personal Reflection
---

Working through the exercises on correlation and regression was an insightful experience that deepened my understanding of these essential statistical concepts. These techniques are not only theoretical but also have practical applications in data analysis and predictive modeling, which made this exercise both engaging and valuable for my personal and professional development.

Understanding Correlation
- The process of calculating Pearson’s correlation coefficient and covariance helped me grasp the foundational concepts of how variables relate to one another. For example, seeing the strong positive correlation between the two generated datasets in the first example clarified how correlation captures the strength and direction of linear relationships. The hands-on calculation reinforced that correlation does not imply causation, a critical point to keep in mind when interpreting real-world data.

- Visualizing the relationships through scatter plots was particularly enlightening. It demonstrated the importance of combining statistical measures with visual tools to better understand data patterns. This dual approach ensured I could validate numerical findings and detect potential anomalies that numbers alone might not reveal.

Applying Linear Regression
- Linear regression was another cornerstone of this exercise. Building a regression model to predict outcomes, such as CO₂ emissions based on weight and volume, illustrated how this method can be applied to real-world problems. The process of fitting a line to data points and interpreting coefficients made the concept of regression tangible. Specifically, understanding how changes in predictor variables influence the dependent variable provided a powerful framework for prediction and decision-making.

- Creating scatter plots with regression lines gave me a visual appreciation of how well the model fit the data. It emphasized the importance of understanding residuals and ensuring that the model assumptions (e.g., linearity, homoscedasticity) hold true for accurate predictions.

Experimenting with Polynomial Regression
- Exploring polynomial regression expanded my perspective on modeling nonlinear relationships. Observing how a cubic function could better fit certain datasets highlighted the limitations of linear models for complex patterns. The use of numpy.polyfit to create a polynomial model, followed by r2_score to evaluate its accuracy, underscored the importance of balancing model complexity with interpretability.

- This part of the exercise was a reminder of the dangers of overfitting. While a higher-degree polynomial might fit the training data better, it could fail to generalize to new data. This realization reinforced the importance of cross-validation and careful selection of model parameters.

Insights and Challenges
- One of the challenges I faced was ensuring that I interpreted the results correctly. For instance, the coefficient of determination (R²) required careful consideration to avoid over-relying on it as a sole measure of model performance. This exercise taught me the value of combining multiple evaluation metrics to build robust models.

- Another challenge was handling multivariate regression when predicting CO₂ emissions. Understanding how each independent variable contributes to the outcome (through coefficients) required a deeper exploration of the underlying data relationships. However, overcoming these challenges helped me grow more confident in analyzing complex datasets.

Impact on Professional Development
- This exercise strengthened my data analysis and visualization skills, which are critical for tackling real-world problems. The ability to calculate and interpret correlations, fit regression models, and evaluate their performance is highly applicable in various fields, from business to healthcare to engineering. Additionally, the hands-on coding experience in Python further solidified my programming skills and familiarity with key libraries like numpy, pandas, and matplotlib.

- Beyond technical skills, this activity encouraged me to think critically about data and its inherent limitations. It reminded me to remain cautious about drawing conclusions from models, especially when working with limited or biased datasets.

Moving Forward
- This experience has inspired me to further explore advanced regression techniques, such as logistic regression and regularization methods, to tackle more complex datasets. Additionally, I plan to practice applying these techniques to real-world scenarios, as this will deepen my understanding and enhance my ability to deliver meaningful insights in professional settings.

In conclusion, the correlation and regression exercises were an excellent opportunity to bridge theoretical knowledge with practical applications. They have equipped me with essential tools and a stronger analytical mindset, both of which will be invaluable in my ongoing journey in data science.
