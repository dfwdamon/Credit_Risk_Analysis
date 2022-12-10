# Credit_Risk_Analysis

## Overview
This project uses Python and machine learning models to predict credit risk.  Credit riks is an inherently unbalanced classification problem, as good loans easily outnubmer risky loans. Different techniques are used to train and evaluate models with unbalanced classes.  An evaluation of performance of the models is done to make a recommendation on whether to implement theim for predicting credit risk.  

The Techniques:
- Oversample the data using the **RandomOverSampler** and **SMOTE** algorithms.
- Undersample the data using the **ClusterCentroids** algorithm.
- Use a combination approach of over and undersampling using the **SMOTEENN** algorithm.
- Compare two machine learning classifier models that reduce bias: **BalancedRandomForestClassifier** & **EasyEnsembleClassifier**.

## Results (Sampling)

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all six machine learning models. Use screenshots of your outputs to support your results.

### OverSampled

  - Naive Random Oversampling results: This produced an accuracy score of 62%.  Note the classification_report_imbalanced displays disparity when it comes to the precision and recall (Sensitivity) and impacts the f1 score.  This shows the model is more accurate then it may actually be.  The model seems to not predicting the  true difference between high and low risk credit scores.
  
<p align="center">  
<img src="https://github.com/dfwdamon/Credit_Risk_Analysis/blob/main/balancedrf.png" />
  <br>  </br>
</p>

  - SMOTE Oversampling results: This resampled data produced a 62% accuracy score.  The SMOTE model produced a higher reacall score (0.79) for "low_risk" than the Random OverSampling (0.77) and a higher f1 score.  Each method is subject to oversampling effects (random generated data not part of original dataset), yet SMOTE appears to reduce bias when generating data from the minority class from the dataset.

<p align="center">
<img src="https://github.com/dfwdamon/Credit_Risk_Analysis/blob/main/SMOTE.png"/>
    <br>  </br>
</p>

- ### UnderSampled
  - UnderSampling with Cluster Centroids Algorithm results: This method is the inverse of OverSampling, and downscales of large class to match the minority class. The accuracy is 62% but appears there is more bias looking at the classification results.  Recall percentages for High_Risk is 59% and Low_Risk is 42% indicating the minority class forced the dataset into containing majority of high risk scores.  This is a false sense of accuracy as the information seesm to be degraded. 

<p align="center">
<img src="https://github.com/dfwdamon/Credit_Risk_Analysis/blob/main/undersampling.png"/>
    <br>  </br>
</p>

- ### Combination (Over and Under) Sampling
  - SMOTEENN algorithm: SMOTEENN combines the SMOTE and Edited Nearest Neighbors (ENN) algorithms.  The results is an accuracy score of 64.% and the low risk recall value is  low at (0.57).  The f1 score of (0.72) indicates the data is more accurate, and the result is much improved to other model results.
 
<p align="center">
<img src="https://github.com/dfwdamon/Credit_Risk_Analysis/blob/main/combination.png"/>
   <br>  </br>
</p>

- ### Balanced Random Forest Classifier 
- The balanced accuracy score result is 78% with an f1 score that rises to (0.95).  This method of grouping data has similarities to Random OverSampling since we are overfitting the data to deal with class imbalance.  

<p align="center">
<img src="https://github.com/dfwdamon/Credit_Risk_Analysis/blob/main/balancedrf.png"/>
   <br>  </br>
</p>

- ### Easy Ensemble AdaBoost Classifier:
The Easy EnsembleAdaBoost classifier results in an accuracy score of 78% and f1 score of even higher (0.97) than the Balanced Random Foreset Classifier.  It should be noted the low risk precision is 1.00 and oversampling effects here should be considered in how the algorithm is applied to the dataset. 

<p align="center">
<img src="https://github.com/dfwdamon/Credit_Risk_Analysis/blob/main/easy_ensemble.png"/>
   <br>  </br>
</p>

## Summary
The four models we undersampled, oversampled and applied a combination to determine which model is best at predicting the high risk loans. The fifth and sixth models resampled the data using ensemble classifiers to predict if loans are high or low risk. The first four models had accuracy score that was not as high as the ensemble classifiers, and the recall in the oversampling/undersampling/mixed models is also low. 

The SMOTE and SMOTEENN seem to mitigate the imbalances of the class identifiers and result in better f1 scoring, but each have 
effects of over and undersampling.  Balanced recall and precision help raise f1 scores for accuracy measurement. 

It is recommended to implement the EasyEnsemble Classifiers with AdaBoosting due to the higher f1 score, and the balance of precision of recall from this dataset, and the process of removing similiar errors through iterations does not eliminate error.  It should be noted that the accuracy of the dataset should be verified in part to ensure invalid or fraudulent data is not included in the set, and to minimize the end result of using these machine learning classifiers for determining real world decision making of credit risk.  A system of monitoring the inputs of future loan data could help to ensure the application of this model continues to be valid in assessing loan prediction risk as other factors and risk levels could shift and present negative outcomes. 