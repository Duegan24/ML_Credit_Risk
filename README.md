# ML_Credit_Risk

## Background and Results

### Purpose
This project was focused on taking a example dataset that included information that was required to perform loan approval and the level of credit risk associated with the loan.  This dataset was analyzed using a logistic regression model from sklearn.

A key aspect of the dataset is that the number of high risk versus low risk loan application was not balanced.  Out of a total number of 68,817 only 347 were considered high risk.  This imbalance in the training data set would prove challenging for a regression model to get high precision, recall, and feature score.

## Resources
- Data Source: LoanStats_2019Q1.csv, 

- Software:  Python 3.7.7, Jupyter Notebook 6.0.3
    - Python Modules: numpy, pandas, sklearn, imblearn


### Technical Analysis

To evaluate how changing the method for resampling could result in better precision, recall, and feature scores, a number of methods were evaluated.  The various methods were Naive Random Oversampling, SMOTE Oversampling, Undersampling, Combination (Over and Under) Sampling (SMOTEENN).

To understand the importance of each score, I will give a definition of each:
-  Balance Accuracy: is the sum of the true positive ratio and true negative ratio divided by zero; giving the probability that the correct target was selected
-  Precision:  is the fraction of relevant instances among the retrieved instances; count of true positives divided by the sum of true positives and false positives
-  Recall (aka sensitivity): is the fraction of the total amount of relevant instances that were actually retrieved; count of the true positives divided by sum of true positives and false negatives
-  F-Score:  is a combination of the precision and the recall, providing a single score; it is the fraction of 2 times product of precision and recall divided by the sum of precision and recall.

Using the first method of sampling, Naive Random Oversampling, as an example, after performing the analysis it can be observed that for the low risk loans the model had a balanced accuracy score of 0.64, a precision of 1, a recall of 0.63, and a F1 score of 0.77.  These are reasonable results; however, when we look at the high risk loans the model performed much more poorly.  In the high risk loan case, the model had a precision of 0.01, a recall of 0.65, and a f1 score of 0.02.  

To evaluate the effectiveness of the various resampling methods the results for the high risk loans were compared.

| Resampling Method | Balance Accuracy | Precision | Recall | F1 |
| --- | --- | --- | --- | --- |
| Naive Random Oversampling | 0.64 | 0.01 | 0.65 | 0.02 |
| SMOTE Oversampling | 0.66 | 0.01 | 0.63 | 0.02 |
| Undersampling | 0.57 | 0.01 | 0.57 | 0.02 |
| Combination Sampling | 0.64 | 0.01 | 0.72 | 0.02 |

It is important to understand that even small incremental improvements at this step can be helpful in later evaluations.  So, while the incremental difference between the various sampling methods is small it is still important to select the best one.  Based on the evaluation of the options I believe that the Combination method provided the best results with a much better recall rate than the rest of the methods.  I recommend that the Combination method be used move forward with this type of analysis. 

