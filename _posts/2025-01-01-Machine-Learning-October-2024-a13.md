---
layout: post
title: UoE - Machine Learning October 2024 A - Model Performance Measurement
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Model Performance Measurement
---

### Model performance measurement
#### Confusion Matrix

        from sklearn.metrics import confusion_matrix
        tn, fp, fn, tp = confusion_matrix([0, 1, 0, 1], [1, 1, 1, 0]).ravel()
        (tn, fp, fn, tp)
--

        import matplotlib.pyplot as plt
        from sklearn.datasets import make_classification
        from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay
        from sklearn.model_selection import train_test_split
        from sklearn.svm import SVC
 --
 
        X, y = make_classification(random_state=0)
        X_train, X_test, y_train, y_test = train_test_split(X, y,
                                                        random_state=0)
    --
 
        clf = SVC(random_state=0)
        clf.fit(X_train, y_train)
        SVC(random_state=0)
        predictions = clf.predict(X_test)
        cm = confusion_matrix(y_test, predictions, labels=clf.classes_)
        disp = ConfusionMatrixDisplay(confusion_matrix=cm,
                                   display_labels=clf.classes_)
  --
      
        disp.plot()
        plt.show()

#### F1, Accuracy, Recall, AUC and Precision scores

        from sklearn.metrics import f1_score

        y_true = [0, 1, 2, 0, 1, 2]
        y_pred = [0, 2, 1, 0, 0, 1]
--

        print(f"Macro f1 score: {f1_score(y_true, y_pred, average='macro')}")
        print(f"Micro F1: {f1_score(y_true, y_pred, average='micro')}")
        print(f"Weighted Average F1: {f1_score(y_true, y_pred, average='weighted')}")
        print(f"F1 No Average: {f1_score(y_true, y_pred, average=None)}")
--

        y_true = [0, 0, 0, 0, 0, 0]
        y_pred = [0, 0, 0, 0, 0, 0]
        f1_score(y_true, y_pred, zero_division=1)
--

    # multilabel classification
        y_true = [[0, 0, 0], [1, 1, 1], [0, 1, 1]]
        y_pred = [[0, 0, 0], [1, 1, 1], [1, 1, 0]]
        print(f"F1 No Average: {f1_score(y_true, y_pred, average=None)}")
--

        from sklearn.metrics import accuracy_score
        y_pred = [0, 2, 1, 3]
        y_true = [0, 1, 2, 3]
        accuracy_score(y_true, y_pred)
--

        from sklearn.metrics import precision_score
        y_true = [0, 1, 2, 0, 1, 2]
        y_pred = [0, 2, 1, 0, 0, 1]
        precision_score(y_true, y_pred, average='macro')
--

        from sklearn.metrics import recall_score
        y_true = [0, 1, 2, 0, 1, 2]
        y_pred = [0, 2, 1, 0, 0, 1]
        recall_score(y_true, y_pred, average='macro')
--

        from sklearn.metrics import classification_report
        y_true = [0, 1, 2, 2, 2]
        y_pred = [0, 0, 2, 2, 1]
        target_names = ['class 0', 'class 1', 'class 2']
        print(classification_report(y_true, y_pred, target_names=target_names))
--

        from sklearn.datasets import load_breast_cancer
        from sklearn.linear_model import LogisticRegression
        from sklearn.metrics import roc_auc_score
        X, y = load_breast_cancer(return_X_y=True)
        clf = LogisticRegression(solver="liblinear", random_state=0).fit(X, y)
        roc_auc_score(y, clf.predict_proba(X)[:, 1])
--

    # multiclass case
        from sklearn.datasets import load_iris
        X, y = load_iris(return_X_y=True)
        clf = LogisticRegression(solver="liblinear").fit(X, y)
        roc_auc_score(y, clf.predict_proba(X), multi_class='ovr')
--

        import numpy as np
        import matplotlib.pyplot as plt
        from itertools import cycle
--

        from sklearn import svm, datasets
        from sklearn.metrics import roc_curve, auc
        from sklearn.model_selection import train_test_split
        from sklearn.preprocessing import label_binarize
        from sklearn.multiclass import OneVsRestClassifier
        from sklearn.metrics import roc_auc_score
--

    # Import some data to play with
        iris = datasets.load_iris()
        X = iris.data
        y = iris.target
--

    # Binarize the output
        y = label_binarize(y, classes=[0, 1, 2])
        n_classes = y.shape[1]
--

    # Add noisy features to make the problem harder
        random_state = np.random.RandomState(0)
        n_samples, n_features = X.shape
        X = np.c_[X, random_state.randn(n_samples, 200 * n_features)]
--

    # shuffle and split training and test sets
        X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.5, random_state=0)
--

    # Learn to predict each class against the other
        classifier = OneVsRestClassifier(
            svm.SVC(kernel="linear", probability=True, random_state=random_state)
        )
        y_score = classifier.fit(X_train, y_train).decision_function(X_test)
--

    # Compute ROC curve and ROC area for each class
        fpr = dict()
        tpr = dict()
        roc_auc = dict()
        for i in range(n_classes):
            fpr[i], tpr[i], _ = roc_curve(y_test[:, i], y_score[:, i])
            roc_auc[i] = auc(fpr[i], tpr[i])
--

    # Compute micro-average ROC curve and ROC area
        fpr["micro"], tpr["micro"], _ = roc_curve(y_test.ravel(), y_score.ravel())
        roc_auc["micro"] = auc(fpr["micro"], tpr["micro"])

        plt.figure()
        lw = 2
        plt.plot(
            fpr[2],
            tpr[2],
            color="darkorange",
            lw=lw,
            label="ROC curve (area = %0.2f)" % roc_auc[2],
        )
        plt.plot([0, 1], [0, 1], color="navy", lw=lw, linestyle="--")
        plt.xlim([0.0, 1.0])
        plt.ylim([0.0, 1.05])
        plt.xlabel("False Positive Rate")
        plt.ylabel("True Positive Rate")
        plt.title("Receiver operating characteristic example")
        plt.legend(loc="lower right")
        plt.show()
--

        from sklearn.metrics import log_loss
        log_loss(["spam", "ham", "ham", "spam"], [[.1, .9], [.9, .1], [.8, .2], [.35, .65]])

### Regression metrics
#### RMSE

        from sklearn.metrics import mean_squared_error
        y_true = [3, -0.5, 2, 7]
        y_pred = [2.5, 0.0, 2, 8]
        mean_squared_error(y_true, y_pred)

#### MAE

        from sklearn.metrics import mean_absolute_error
        y_true = [3, -0.5, 2, 7]
        y_pred = [2.5, 0.0, 2, 8]
        mean_absolute_error(y_true, y_pred)

#### r squared

        from sklearn.metrics import r2_score
        r2_score(y_true, y_pred)

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML12-1.png)
![image](/assets/images/banners/ML12-2.png)
![image](/assets/images/banners/ML12-3.png)
![image](/assets/images/banners/ML12-4.png)
![image](/assets/images/banners/ML12-5.png)
![image](/assets/images/banners/ML12-6.png)

---
## Personal Reflection
---

Working on model performance measurement provided me with a comprehensive understanding of various evaluation metrics used in machine learning for classification and regression problems. This experience reinforced the importance of interpreting model results beyond simple accuracy to ensure robust, fair, and meaningful insights from machine learning models.

Classification Metrics
- Confusion Matrix Understanding the confusion matrix was foundational to evaluating classification models. Breaking it down into True Positives (TP), True Negatives (TN), False Positives (FP), and False Negatives (FN) gave me clarity on how predictions align with actual labels. Visualizing the confusion matrix with tools like ConfusionMatrixDisplay provided an intuitive way to interpret model performance and identify imbalances in class predictions.

- The importance of this became clear when working with imbalanced datasets, where accuracy alone could be misleading. For instance, in a dataset with a high majority class, a high accuracy might still result in poor performance for the minority class. This realization highlighted the need for additional metrics.

- F1 Score, Precision, and Recall Exploring precision, recall, and F1 score helped me appreciate their role in different scenarios. Precision, which measures how many predicted positives are truly positive, is critical in applications where false positives are costly, such as spam detection. Recall, which measures how many actual positives are correctly predicted, is crucial in fields like healthcare, where missing a positive case could have severe consequences.

- The F1 score’s balance between precision and recall was particularly insightful. Its macro, micro, and weighted variants further demonstrated the nuances of evaluating models across multi-class and imbalanced datasets. The multilabel classification example underscored how these metrics adapt to different types of problems, making them versatile tools in model evaluation.

- ROC Curve and AUC The ROC curve and AUC scores were invaluable in understanding model performance across different thresholds. Visualizing the trade-off between true positive and false positive rates made it easier to compare models and select appropriate thresholds for decision-making. The AUC score provided a single metric to assess model performance, particularly useful for comparing models in binary and multiclass classification scenarios.

- Classification Report The classification report was a great tool for summarizing key metrics for each class. It made it easy to spot classes where the model underperformed and highlighted areas for improvement. This aligns with real-world scenarios where actionable insights are critical for refining models.

Regression Metrics
- Mean Squared Error (MSE) and Root Mean Squared Error (RMSE) The MSE and RMSE metrics helped me understand the magnitude of errors in regression models. RMSE, with its same unit as the target variable, was particularly intuitive for interpreting model errors. These metrics highlighted the sensitivity to outliers, emphasizing the need for robust evaluation methods in noisy datasets.

- Mean Absolute Error (MAE) MAE, being less sensitive to outliers compared to MSE, offered a different perspective on model errors. It reinforced the importance of using multiple metrics to gain a comprehensive view of model performance, especially in scenarios where outliers are significant.

- R² Score The R² score was a useful metric to measure how much of the variance in the target variable is explained by the model. Its intuitive interpretation, ranging from 0 to 1, made it easier to communicate model effectiveness to non-technical stakeholders. However, it also taught me to be cautious, as R² can sometimes be misleading when dealing with non-linear relationships.

Challenges and Problem-Solving
- One of the challenges I faced was selecting the appropriate metrics for specific use cases. Initially, I gravitated toward accuracy as the primary metric, but I soon - realized its limitations, especially in imbalanced datasets. This taught me the importance of understanding the context of the problem and choosing metrics that align with the business or application goals.

- Another challenge was interpreting the ROC curve and AUC for multiclass problems. Understanding how "One-vs-Rest" (OVR) approaches work and interpreting micro-average and macro-average ROC curves required a deeper dive into the concepts. However, visualizing these curves made the concepts much clearer and easier to understand.

Key Insights
- Metrics Selection Matters Different metrics capture different aspects of model performance. For example, while accuracy might suffice for balanced datasets, metrics like F1 score, precision, and recall are better suited for imbalanced datasets. Understanding when to use which metric is critical for meaningful evaluations.

- Visualization is Key Visualizing metrics like the confusion matrix, ROC curves, and cost over iterations helped me understand model behavior more intuitively. These tools are invaluable for diagnosing issues and communicating results effectively to both technical and non-technical audiences.

- Metrics Beyond Numbers While metrics provide quantitative insights, their interpretation must align with the real-world impact of predictions. For instance, in healthcare, false negatives can be more critical than false positives, shaping the choice of metrics and model thresholds.

Professional Growth
- This project significantly improved my ability to evaluate machine learning models comprehensively. I gained practical experience with tools and techniques like confusion matrices, classification reports, and ROC curves, which are essential for real-world applications.

- Additionally, this experience reinforced my analytical skills, teaching me to think critically about what each metric represents and how it aligns with the problem at hand. These skills will be invaluable as I tackle more complex machine learning projects in the future.

Moving Forward
In the future, I plan to:
- Explore Advanced Metrics: Delve deeper into evaluation metrics like Matthews Correlation Coefficient (MCC), Cohen’s Kappa, and log loss to handle more nuanced problems.
- Apply to Real-World Data: Use these metrics on real-world datasets to better understand their practical implications and limitations.
- Threshold Tuning: Experiment with threshold tuning to optimize precision and recall for specific applications, such as fraud detection or medical diagnosis.

Conclusion
- This experience emphasized the importance of evaluating machine learning models beyond surface-level metrics. By exploring a wide range of classification and regression metrics, I gained a deeper appreciation for their role in building reliable and impactful models. These learnings have strengthened my confidence in interpreting model performance and making data-driven decisions.
