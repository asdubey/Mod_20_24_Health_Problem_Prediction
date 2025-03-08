# <img src = images/diab-small.png width="10%"/> Predicting the Diabetes 

<center>
    <img src = images/diabetes-3.png />
</center>

### Project Title

Capstone Project at UC Berkeley: PC-MLAI

**Author** : Ashutosh Dubey

**Research Question**: How can we accurately predict the type and subclass of diabetes in adults based on the information collected on eating habits, medical information and lifestyle questions?

## Executive summary


## Context

### Problem Statement

**Overview**: 

Diabetes is a chronic (long-lasting) health condition that affects how your body takes in food sugar i.e. glucose. This sugar after consumption enters the bloodstream and then gets into the cells that use it for energy. Insulin is the hormone released by pancreas that lets this blood sugar into the cells.

With diabetes, your body doesn't make enough insulin or can't use it as well as it should. Because of this too much blood sugar remains in the bloodstream. Over time, that can cause serious health problems, such as heart disease, vision loss, and kidney disease. There are three main types of diabetes: type 1, type 2, and gestational diabetes (diabetes while pregnant)
- Type 1 diabetes is thought to be caused by an autoimmune reaction, in which the body stops making insulin. Cause and prevention is not known and the only cure is to keep taking insulin. This mostly occurs in children and young adults.
- Type 2 diabetes is when the body doesn't use the insulin properly and can not keep the blood sugar at normal level. This is generally diagnosed in adults as they develop over years, but is an increasing trend found in children and young adults now.
- Gestational diabetes is diabetes developed in pregnant women who never had diabetes. This goes away after pregnancy but increases the risk of Type 2 for the mother. For children born also it is a higher risk of obesity and Type 2 diabetes later in life.

In the US about every 1 in 3 adults has pre-diabetes, and among this population about 8 to 10% aren't aware that they are pre-diabetic. With pre-diabetes the sugar is not high enough to classify as Type 2 diabetes but does raise the risk of heart-attack and stroke

<center>
    <img src = images/DiabetesInTheUS_Thumbnail.jpg width="1500px" height="300px"/>
</center>

- About 38 million adults have diabetes, and 1 in 5 of them don't know they have it.
- Diabetes is the No. 1 cause of kidney failure, lower-limb amputations, and adult blindness.

***Prediabetes and Type 2 diabetes can be prevented with dietary and lifestyle changes.*** Currently it is not know how to prevent Type 1 diabetes.

We need to learn what lifestyle or dietary habits have more impact on if someone will get diabetes or not. How to guide people to choose better lifestyle for **prevention of diabetes**.

#### Rationale
Following are some of the strong reasons why we need to make accurate prediction, and also provide feedback on improvement of surveys, if there are gaps. As this disease is being diagnosed more and more in children and young adults, identifying the lifestyle changes to be more healthy is very important.

- About 38 million adults have diabetes, and 1 in 5 of them don't know they have it.
- Diabetes is the No. 1 cause of kidney failure, lower-limb amputations, and adult blindness.
- Diabetes is the eighth leading cause of death.


#### Research Question

Goal of this project is to analyse the survey conducted by CDC and verify if it can accurately predict if a person has diabetes or not. What factors influence if a person has diabetes? The information learnt can be helpful in promoting programs to reduce diabetes. This analysis will also help optimize the survey program itself for better participation. This can be done by removing the questions which are not providing much meaningful information to the predictions. Which will help shorten the survey and can potentially improve participation number of surveys. Various supervised learning techniques to be tested and choose the best that fits among - K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines.

To solve this problem and provide answers to our main question we are going to use the widely known CRISP-DM framework.

### CRISP-DM Framework
<center>
    <img src = images/crisp.png style="border-radius: 8px; width: 50%;"/>
</center>

The CRISP-DM framework i.e. Cross-Industry Standard Process for Data Mining, is widely user framework for structuring data science and ML . It helps by providing the a systematic approach for solving data driven problems. More details can be found h a brief overview of CRISP-DM [here](https://mo-pcco.s3.us-east-1.amazonaws.com/BH-PCMLAI/module_11/readings_starter.zip). 



#### Data Sources

The dataset is from [Kaggle - Diabetes Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset?select=diabetes_012_health_indicators_BRFSS2015.csv). This dataset contains healthcare statistics and lifestyle survey information about people in general along with their diagnosis of diabetes(the original dataset is from [CDC](https://www.cdc.gov/brfss/annual_data/annual_2015.html))


What data will you use to answer you question?

#### Methodology
What methods are you using to answer the question?

We will use the True Positive Rate (TPR), False Positive Rate (FPR), and the Area Under the ROC Curve (AUC-ROC) to evaluate the validity of each model. The TPR and FPR will be derived from the confusion matrix of our classifiers.

SSince we expect the dataset to be imbalanced, these metrics will be more informative than accuracy. In our case, the number of people who actually have diabetes is expected to be much smaller in comparison to those who do not have disease. Relying on accuracy will result in higher score of the model but may still perform poorly in predicting the disease.

The ROC curve plots TPR (y-axis) vs. FPR (x-axis), providing a visual representation of the classifier’s performance. AUC (Area Under the Curve) is a robust metric for evaluating binary classification problems, as it quantifies the model’s ability to distinguish between classes.

#### Results

### Summary
This analysis for done in two phases. In first phase all the features which were recorded as part of survey were included. In second phase of the analysis many attribute which were irrelevant were removed.
After dropping the certain features I was able to train the set on the complete data set. But overall scores were not much different.

**Logistic Regression:**
The logistic regression offres a best AUC score of 94.8%. Accuracy is much lower when compared to decision tree. Training time was more than double of DT. 

**KNN:**
The KNN algorithm took the longest to train. The accuracy was 84% and AUC also around 94.1% which is lowest comapred to DT and LR. C

**SVM:**
The SVM had to be performed on a subset of 10,000 datapoint and required extremely long fit time. For a subset of 10% of the data the gridsearch and fit time long time. For the impracticality of such a model in real time and lack of meaningful result, model is not optimal.

**Decision Tree:**
The decision tree offered a very similar AUC compared to the logistic regression close to 94.4%. Accuracy is also very close to LR and similar F1 score. Overall it took the least time with the highest AUC score.

**Choice of the Model:**
- Logistic Regression with AUC of 94.8% and best F1 at 0.83.
- Training time is manageable more than the Dtree but better when compared to KNN or SVM.

**Future:**
These models an be further explored with different feature selections.

- Exploring further parameters for the top two models (logistic regression and decision trees). Particularly logistic regression because of manageable time to train with highest score.

### Scores
<center>
<table>
<tr>
   <td>  All Features </td>
   <td> Selective Features </td>
</tr>
<tr>
   <td>  <img src = images/all_feature_score.png style="width: 100%;"/> </td>
   <td> <img src = images/less_feature_score.png style="width: 100%;"/> </td>
</tr>
</table>
</center>


#### Next steps

There is an opportunity to further optimise the model identified. Given the problem statement we are trying to address we should further optimise the features and also try other models e.g. Neural networks to get more accurate prediction and scores.
I would also like to extend this project to do more research focused on children and young adults. This segment of diabetes patients are most vulnerable but can be handled easily with lifestyle changes. Also, designing surveys which can capture the parameters which affect children more.

#### Outline of project

data/diabetes_012_health_indicators_BRFSS2015.csv: Contains dataset used in the analysis.
deployment/: Contains models ready for deployment or to be used in apps.
notebooks/predicting-diabetes-all-features.ipynb: Jupyter notebook with code for data analysis and modeling.
notebooks/predicting-diabetes-important-features.ipynb: Jupyter notebook with code for data analysis and modeling with reduce feature set.
README.md: Summary of findings and link to notebook

- [Notebook with all features](./notebook/predicting-diabetes-all-features.ipynb)
- [Notebook with selective features](./notebook/predicting-diabetes-important-features.ipynb)

