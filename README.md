# machine_learning_credit_risk
## Overview 

This analysis will assess credit risk using data from LendingClub; a peer-to-peer lending services company using a variety of machine learning models. When assessing which machine learning models to use, it is important to understand the data and how it can affect the model's evaluation metrics. In this case the data is imbalanced, which if not addressed, can lead to misleading precision, recall, and f1 scores.  

In order to address the issue of imbalanced data the following balancing techniques will be implemented and evaluated: 

- Naïve Random Oversampling 

- Synthetic Minority Oversampling Technique (SMOTE) 

- Cluster Centroid Undersampling  

- Combination Sampling (SMOTEENN) 

- Balanced Random Forest Sampling 

- AdaBoost (trained on different balanced bootstrap samples) 

 

## Resources 

- Data Source: LoanStats_2019Q1.csv 

- Software: Python 3.7.6, Jupyter Lab 1.2.6, Scikit-Learn 0.23.0, Imbalanced-Learn 0.7.0 

 

## Summary 

### Logistic Regression Model 

To resolve the issue of class imbalance, the following techniques were used in collaboration with Scikit-Learn's logistic regression model: Naïve Random Oversampling, SMOTE, Cluster Centroid Undersampling, and SMOTEENN. Additionally, Scikit-Learn's logistic regression model supplies five solver algorithms: lbfgs, liblinear, newton-cg, sag, and saga, which were used in collaboration with each sampling technique. For the purposes of this analysis, only the values of the most successful solver algorithm were included for each sampling technique. The model evaluation metrics for the other solver algorithms can be found in the attached Jupyter notebook.  

- Naïve Random Oversampling (newton-cg): 

  - Balanced Accuracy Score:  0.75 

  - Precision:  0.02 

  - Recall: 0.71 

  - Specificity:  0.80 

  - F1: 0.04 

- Synthetic Minority Oversampling Technique (liblinear) 

  - Balanced Accuracy Score:  0.66 

  - Precision: 0.01 

  - Recall: 0.62 

  - Specificity: 0.71 

  - F1: 0.02 

- Cluster Centroid Undersampling (newton-cg) 

  - Balanced Accuracy Score: 0.61 

  - Precision:  0.01 

  - Recall: 0.81 

  - Specificity:  0.42 

  - F1: 0.02 

- SMOTEENN (lbfgs) 

  - Balanced Accuracy Score: 0.64 

  - Precision:  0.01 

  - Recall: 0.73 

  - Specificity:  0.55 

  - F1: 0.02 

###  Ensemble Model 

- Balanced Random Forest Sampling 

  - Balanced Accuracy Score: 0.77 

  - Precision:  0.03 

  - Recall: 0.66 

  - Specificity:  0.88 

  - F1: 0.06 

- AdaBoost (Easy Ensemble Classifier) 

  - Balanced Accuracy Score: 0.91 

  - Precision:  0.07 

  - Recall: 0.88 

  - Specificity:  0.93 

  - F1: 0.14 

### Analysis 

A model that successfully predicts credit risk will need to have a high recall score as it provides the metric for type II errors (false negatives), which in the case of this model, is the number of high-risk applicants that would be identified as low-risk in error. In this use case type I errors (false positives) are not as important since identifying a low-risk customer as high-risk does not have the same negative business implications. This trade-off must be taken into consideration on a case by case basis in order to ensure the sensitivity gained from an increase in recall does not outweigh the extra workload it causes for the business to manually analyze the false positives.  Furthermore, for the purposes of this analysis the balanced accuracy score will not be taken into consideration since it indicates how well the model predicted type I and type II errors for both low and high-risk applicants, which may lead to a model that predicts one far better than the other. 

AdaBoost Easy Ensemble Classifier outperformed the other models in all metrics, most notably in precision and recall, and is the recommended machine learning model for predicting credit risk.  
