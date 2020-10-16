# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
**In 1-2 sentences, explain the problem statement: e.g "This dataset contains data about... we seek to predict..."**
This dataset contains data about bank marketing,  the classification goal is to predict if the client will subscribe a bank term deposit (Yes/no)
**In 1-2 sentences, explain the solution: e.g. "The best performing model was a ..."**
The best performing algorithm using Auto ml was a LightGBMClassifier
## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
the pipeline starts with data ingestion from azure blob storage with azure dataset factory module, the data is then cleaned using a custom function, and then splitted into train and test set, and fed to the classifier, the hyperparameters of the Logistic Regression method is tuned using hyperdrive with a defined search space, the classifer with best combination of hyperparametrs has been saved.
**What are the benefits of the parameter sampler you chose?**
I chose random parameter sampler, it is much faster than grid sampler but very close to grid sampler in terms of accuracy
**What are the benefits of the early stopping policy you chose?**

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**
the best model by auto ml is a LightGBMClassifier with hyper-parameters as follows:
boosting_type='gbdt', class_weight=None,
colsample_bytree=1.0,
importance_type='split', learning_rate=0.1,
max_depth=-1, min_child_samples=20,
min_child_weight=0.001, min_split_gain=0.0,
n_estimators=100, n_jobs=1, num_leaves=31,
objective=None, random_state=None,
reg_alpha=0.0, reg_lambda=0.0, silent=True,
subsample=1.0, subsample_for_bin=200000,
subsample_freq=0, verbose=-10
## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**
Surprisingly, the accuracy using both models are very similar 91.51 (auto ml) and Logistic Regression (91.08) but auto ml is very easier to configure and use, there was a difference in the architecture, the difference is architecture can be attributed to the fact that auto ml searches for the best models as well as best hyper params for that model where as hyperdrive does not search for best model, it only optmizes the hyperparameters for the model under consideration

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
for hyperdrive we may fit a non-linear or tree based model to see the performance improvement, auto ml is already optimized
## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**
![](https://github.com/juberrahman/nd00333_AZMLND_Optimizing_a_Pipeline_in_Azure-Starter_Files/blob/master/Capture.PNG)
