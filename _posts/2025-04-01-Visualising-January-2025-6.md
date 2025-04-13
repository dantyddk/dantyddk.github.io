---
layout: post
title: UoE - Visualising Data January 2025 - Programming Exercise
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, assignment, Module E-Portfolio Learning Activities]
---
---
## Predicting Customer Response in Telemarketing Campaigns: A Data-Driven Approach
---
### Introduction

Telemarketing is vital for customer acquisition in banking but often faces inefficiencies due to poor targeting. Predictive analytics can enhance accuracy and reduce costs (Moro et al., 2014). This report applies the CRISP-DM framework (Chapman et al., 2000) to a Portuguese bank’s data, using machine learning to boost conversion rates and campaign efficiency

![image](/assets/images/banners/V4-1.jpg)

### PART 1: EXPLORATORY DATA ANALYSIS

#### 1.	BACKGROUND
The dataset from a Portuguese bank (2008–2013) includes cleaned records from the UCI Machine Learning Repository and aims to predict term deposit subscriptions using demographic, financial, and economic data to improve targeting and campaign efficiency.

#### 2.	DATA INTRODUCTION
The dataset consists of 4,100 observations with 21 columns, including both categorical and numerical features categorized into three primary groups. 
-	Client-related attributes: age, job, martital, k (education), default, housing, loan.
-	Marketing interaction features: contact, month, day_of_week, duration, campaign, pdays, previous, poutcome.
-	External economic indicators: emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed
-	The target variable 'y' is binary, indicating whether a customer subscribed to a long-term deposit (yes/no)

![image](/assets/images/banners/V4-2.png)
![image](/assets/images/banners/V4-3.png)

#### 3.	CONDUCT EXPORATORY DATA ANALYSIS (EDA)

##### 3.1. DATA PREPROCESSING
-	There are no missing values in the dataset.
-	The column labelled 'k' does not match any expected variables from the dataset description. This might correspond to the 'education' variable.

![image](/assets/images/banners/V4-4.png)
![image](/assets/images/banners/V4-5.png)

##### 3.2. EXPLORATORY ANALYSIS METHODS

![image](/assets/images/banners/V4-6.png)

A CRISP-DM-based workflow guided the process from feature exploration to model preparation. Visual tools like histograms, boxplots, and heatmaps were used to extract insights and assess variable importance.

##### 3.3. NUMERICAL VARIABLES

###### 3.3.1. Summary statistics, Distribution and Outliers
-	Age: Average is 40.1 years; most clients are aged 30–50. Distribution is balanced, making age a reliable modelling feature. The age distribution does not show extreme outliers.
-	Call Duration: Highly variable (mean ~257s); some calls lasted 0s which could indicate failed or terminated calls. Some extreme values indicate very long calls, possibly outliers.
-	Campaign Contact: Average of 2.5 calls per client; some contacted 10+ times, suggesting over-contacting risks and customer fatigue. There are cases where clients were contacted 10+ times, which are significant outliers.
-	Days Since Last Contact: Many clients were never contacted before.
-	Previous Contacts: Mostly 0, but some clients had up to 6+ previous contacts, which could be key in predicting the likelihood of success.
-	Economic Indicators: Metrics like employment variation and Euribor rate show variation but no major outliers; they may impact client decisions.
-	Overall Implications:
    -	Target Audience: Middle-aged professionals (30-50 years old)
    -	Call Strategy: Optimize call duration and avoid excessive follow-ups
    -	Economic Factors: Monitor employment variation and consumer confidence to adjust messaging
    -	Predictive Potential: Call duration and prior contact history may be strong indicators of success

![image](/assets/images/banners/V4-7.png)
![image](/assets/images/banners/V4-8.png)
![image](/assets/images/banners/V4-9.png)
![image](/assets/images/banners/V4-10.png)
![image](/assets/images/banners/V4-11.png)
![image](/assets/images/banners/V4-12.png)
![image](/assets/images/banners/V4-13.png)
![image](/assets/images/banners/V4-14.png)
![image](/assets/images/banners/V4-15.png)
![image](/assets/images/banners/V4-16.png)
![image](/assets/images/banners/V4-17.png)
![image](/assets/images/banners/V4-18.png)
![image](/assets/images/banners/V4-19.png)

###### 3.3.2. CORRELATION ANALYSIS
-	Strong Positives:
    -	Euribor 3-month Rate & Number of Employees (0.94): Indicates that as the Euribor rate increases, employment levels rise.
    -	Employment Variation Rate & Euribor 3-month Rate (0.72): Employment variation aligns with interest rate fluctuations.
-	Negatives:
    -	Euribor 3-month Rate & Consumer Confidence Index (-0.64): Higher Euribor rates coincide with lower consumer confidence, possibly due to higher borrowing costs.
    -	Employment Variation Rate & Consumer Confidence Index 
(-0.54): Higher employment variation (economic instability) corresponds with lower consumer confidence.
-	Weak/No Significant:
    -	Pdays & Previous Contacts: Previous campaign contacts do not strongly impact the number of days since last contact.
    -	Campaign has low correlation with all variables, meaning call frequency alone may not determine success.
-	Key Takeaways:
    -	Euribor rate and employment metrics are highly correlated.
    -	Consumer confidence is negatively impacted by Euribor rates and employment variation.
    -	The number of campaign calls does not strongly predict other numerical features.
      
![image](/assets/images/banners/V4-20.png)
![image](/assets/images/banners/V4-21.png)

##### 3.4. CATEGORICAL VARIABLES
-	Job Type: Most clients work in admin, blue-collar, or technician roles. However, higher subscription rates are seen among management, students, and retirees, while blue-collar and service workers show lower interest. Highlighting job type as a key predictor.
-	Marital Status: The majority are married, followed by single and divorced. Single clients are more likely to subscribe, possibly due to fewer financial commitments.
-	Education Level: Most clients hold university or high school degrees, with a notable portion having only basic education. Higher-educated individuals show better subscription rates, suggesting education level impacts financial decision-making.
-	Credit Default History: Almost all clients have no defaults, though many have unknown status, posing challenges for risk assessment. Clients without defaults are more likely to subscribe.
-	Housing Loan / Personal Loan Ownership: A slight majority have housing loans, while fewer have personal loans. Those without loans are more likely to invest, indicating financial flexibility boosts subscription likelihood.
-	Contact Method: Mobile phones are the primary contact channel and are more successful than landlines, supporting mobile-first outreach strategies.
-	Month of Contact: Campaigns peaked in May, July, and August, but conversions were higher in March, September, October, and December—suggesting a misalignment between effort and outcome.
-	Day of Week Contacted: Slightly more calls on Mondays and Thursdays, which may align with higher customer responsiveness.
-	Previous Campaigns: Most clients were first-time contacts. Those with successful past interactions showed a much higher subscription likelihood.
-	Subscription Outcome (Target Variable - y): Only 11% of clients subscribed, indicating significant class imbalance and the need for improved targeting.
-	Overall Implications:
    -	Higher-educated professionals (admin, technician) with stable financial backgrounds.
    -	Prioritize mobile outreach, especially on Mondays and Thursdays.
    -	Align campaigns with months of higher success (March, Sept, Dec).
    -	Address class imbalance and optimize strategies for high-effort/low-return periods like May and June.
 
![image](/assets/images/banners/V4-22.png)
![image](/assets/images/banners/V4-23.png)
![image](/assets/images/banners/V4-24.png)
![image](/assets/images/banners/V4-25.png)
![image](/assets/images/banners/V4-26.png)
![image](/assets/images/banners/V4-27.png)
![image](/assets/images/banners/V4-28.png)
![image](/assets/images/banners/V4-29.png)
![image](/assets/images/banners/V4-30.png)
![image](/assets/images/banners/V4-31.png)
![image](/assets/images/banners/V4-32.png)
![image](/assets/images/banners/V4-33.png)
![image](/assets/images/banners/V4-35.png)
![image](/assets/images/banners/V4-36.png)

### PART 2: STATISTICAL MODELING

#### 1. MODEL SELECTION AND JUSTIFICATION
To determine the most effective predictive model, three di
fferent machine learning models were considered:
-	Linear Regression: Commonly used for continuous outcomes, this model was not suitable for our binary target variable (y: yes/no).
-	Logistic Regression: Suitable for classification but limited by its linear decision boundary, which may not capture complex patterns.
-	Decision Tree-Based Models: Chosen for their ability to handle non-linear relationships and mixed data types. Two tree-based models were evaluated:
    -	Random Forest: Uses multiple decision trees to improve accuracy and reduce overfitting
    -	XGBoost (Extreme Gradient Boosting): A fast, powerful algorithm effective for imbalanced data and capturing complex interactions
After comparing performance metrics, XGBoost achieved higher accuracy than Random Forest (Table 2), making it the preferred model for implementation.

![image](/assets/images/banners/V4-37.png)

#### 2. INFORMED DESICION-MAKING WITH THE MODEL
The trained model helps bank telemarketers identify potential customers who are more likely to subscribe to term deposits. This allows:
-	Prioritization of high-probability customers.
-	Reduced cost and effort in cold calling.
-	Enhanced efficiency in campaign execution.

#### 3. DATASET PARTITIONING
The dataset was divided into training and validation sets to assess model:
-	Training Set (70%): Used to train the model
-	Validation Set (15%): Used to tune hyperparameters
-	Test Set (15%): Used to evaluate final model performance

![image](/assets/images/banners/V4-38.png)
![image](/assets/images/banners/V4-39.png)

#### 4. TRAINING PROCESS

![image](/assets/images/banners/V4-40.png)

#### 5. TRAINING AND VALIDATION ACCURACY AND LOSS
If the curves show consistent improvement in both training and validation metrics, the model is learning effectively. If the validation loss flattens while the training loss continues to decrease, it is an indicator to consider Early Stopping to prevent overfitting. (Goodfellow, I., Bengio, Y., & Courville, A., 2016).

![image](/assets/images/banners/V4-41.png)
![image](/assets/images/banners/V4-42.png)
![image](/assets/images/banners/V4-43.png)
![image](/assets/images/banners/V4-44.png)

#### 6. MODEL EVALUATION
To measure the effectiveness of the model, we computed key classification metrics:
-	Confusion Matrix: Shows True Positives, True Negatives, False Positives, and False Negatives.
-	Accuracy: Measures the proportion of correct predictions.
-	Precision & Recall: Assess the trade-off between false positives and false negatives.
-	F1-score: Harmonic mean of precision and recall.

##### 6.1. Model Performance Interpretation
-	Accuracy: 94.52% of the predictions were correct, indicating a highly reliable model. 
-	Confusion Matrix Insights: 
    -	True Positives (525): Correctly predicted customers who subscribed.
    -	True Negatives (510): Correctly predicted customers who did not subscribe.
    -	False Positives (38): Incorrectly predicted that a customer would subscribe when they did not.
    -	False Negatives (22): Incorrectly predicted that a customer would not subscribe when they actually did. It is crucial, as these represent missed opportunities to engage genuinely interested customers

![image](/assets/images/banners/V4-45.png)
![image](/assets/images/banners/V4-46.png)

##### 6.2. Classification Report Insights
-	Precision (96% - No,  93% - Yes): Good at minimizing false positives. 
-	Recall (93% - No, 96% - Yes): Better at capturing positive cases 
-	F1-Score (~95%): Reflects balanced performance in precision and recall.

![image](/assets/images/banners/V4-47.png)
![image](/assets/images/banners/V4-48.png)

#### 7. BUSINESS IMPLICATIONS
- High recall for subscriptions (96%) means most potential customers are being correctly identified, leading to better marketing efficiency.
- False positives (38 cases) are relatively low, meaning unnecessary calls to uninterested customers are minimized.
- The model can be further optimized with hyperparameter tuning to improve precision without reducing recall.

#### 8. RECOMMENDATION
To enhance model performance and robustness, the following strategies are suggested:
-	Hyperparameter Tuning: Adjust parameters like learning rate, max depth, and estimators using Grid or Randomized Search.
-	Feature Engineering: Create new features (e.g., interaction terms) and apply feature selection to eliminate less useful variables.
-	Class Imbalance Handling: Use techniques like SMOTE to balance the dataset if class distribution is skewed.
-	Regularization & Early Stopping: Apply L1/L2 regularization to prevent overfitting and use early stopping to halt training when validation metrics decline.
-	Ensemble Learning: Combine XGBoost with models like Random Forest or LightGBM to boost predictive accuracy.

### CONCLUSION
This study used machine learning to improve telemarketing for a Portuguese bank. The XGBoost model, with 94.52% accuracy, effectively identified likely subscribers based on factors like past campaign outcomes, call duration, and economic indicators.
These insights help reduce costs, limit unnecessary calls, and improve campaign efficiency. Highlighting the value of predictive analytics in optimizing marketing efforts.
 
### REFERENCES
-	Chapman, P., Clinton, J., Kerber, R., Khabaza, T., Reinartz, T., Shearer, C. and Wirth, R., 2000. <em>CRISP-DM 1.0: Step-by-step data mining guide</em>. SPSS Inc.
-	Chen, T. and Guestrin, C., 2016. XGBoost: A scalable tree boosting system. In Proceedings of the 22nd ACM SIGKDD <em>International Conference on Knowledge Discovery and Data Mining</em>, pp.785-794.
-	Goodfellow, I., Bengio, Y. and Courville, A., 2016. <em>Deep Learning</em>. MIT Press.
-	Moro, S., Cortez, P. and Rita, P., 2014. A data-driven approach to predict the success of bank telemarketing. <em>Decision Support Systems</em>, 62, pp.22–31.

APPENDIX
-	All analyses, tables, columns, and charts above were performed using <a href="https://dantyddk.github.io/el-activities/2025/01/01/Machine-Learning-October-2024-1.html" target="_blank">Python on Google Colab</a><br>

---
## Artefacts
---

![image](/assets/images/banners/V4-49.png)
