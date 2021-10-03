## Executive Summary 

It was reported that in 2011 more than 3.3 million patients were readmitted in the US within 30 days of being discharged, and they were associated with about $41 billion in hospital costs. The need for readmission indicates that inadequate care was provided to the patient at the time of first admission. The readmission rate has become an important metric measuring the overall quality of a hospital.

Diabetes is well known to be consuming an increasingly large percentage of national health care expenditures and effort. The growing pervasiveness of diabetes, therefore, makes it increasingly important for medical practitioners to be able to treat diabetes effectively. Diabetes affects nearly every specialty and subspecialty of medical practice; even physicians who are not primary care providers need to be aware of potential complications and comorbidities caused by diabetes. Timely identification of patients facing a high risk of readmission can enable medical practitioners to perform additional examinations and possibly prevent future readmissions. 

According to the American Diabetes Association (ADA), the economic impact of diabetes is significant. In 2007, it was estimated that the direct economic cost of diabetes for the people who have the disease in the United States was estimated to be $116 billion. When one considers the indirect costs of diabetes, such as loss of productivity, disability, and early mortality, the cost is even higher, approaching $174 billion in 2007.

In this project, the data I obtained represents 100,000+ unique inpatient diabetes encounters over 10 years (1999–2008) of clinical care at 130 hospitals and integrated delivery networks in the United States. Using this data, I build a machine learning binary classification model to predict diabetes patients with a high risk of readmission. Note that higher sensitivity (recall) is more desirable for medical practitioners because it is more crucial to correctly identify "high risk" patients who are likely to be readmitted than identifying "low risk" patients.

Optimizing for sensitivity, performed best with a Identification of readmission was consistently lower in all three  believe the limited features of 



1. Begin with an executive summary:
   - What is your goal?
   - What are your metrics?
   - What were your findings?
   - What risks/limitations/assumptions affect these findings?
   

Measurement of HbA1c Hyperglycemia( High Blood Sugar) , a buildup of glucose in a person's bloodstream at dangerously high levels due to a person's body not being able to produce enough insulin.


## Background

Diabetes, is a 

The dataset I obtained, initially had 50 features, as binary classification problem, I was interested in the instance of readmission of a patient after their initial "encounter" (medical visit), based on varying features such as age, gender, primary diagnosis, time spent at the hospital during the initial encounter, etc. 

Through cleaning and EDA 

2. Walk through your model step by step, starting with EDA
   - What are your variables of interest?
   - What outliers did you remove?
   - What types of data imputation did you perform? 

No imputation dropping of the following features:
   - Weight
   - Payer code
   - Medical specialty 
   
   
## Problem Statement 

Do note that the raw data contained over 100 features, more than twice the number of features I available in the data set I obtained. So with that in mind, my analysis aimed to determine the following:
1. What factors are the strongest indicator of hospital readmission for a diabetic patient?
2. How well can I predict hospital readmission with "limited" features in this dataset? 


# Dataset 

The dataset represents 10 years (1999-2008) of clinical care at 130 US hospitals and integrated delivery networks throughout the United States: Midwest (18 hospitals), Northeast (58), South (28), and West (16). It includes over 50 features representing patient and hospital outcomes. Information was extracted from the database for encounters that satisfied the following criteria:

* It is an inpatient encounter (a hospital admission).
* It is a diabetic encounter, that is, one during which any kind of diabetes was entered to the system as a diagnosis.
* The length of stay was at least 1 day and at most 14 days.
* Laboratory tests were performed during the encounter.
* Medications were administered during the encounter.
* The data contains such attributes as patient number, race, gender, age, admission type, time in hospital, medical specialty of admitting physician, number of lab test performed, HbA1c test result, diagnosis, number of medications, diabetic medications, number of outpatient, inpatient, and emergency visits in the year before the hospitalization, etc. For a full list of attributes and their descriptions, [click here](https://www.hindawi.com/journals/bmri/2014/781670/tab1/)


## Modeling and Evaluation 

Three classification models were used: Regression, K-Nearest Neighbors, Random Forest. A baseline score of () was established. Then I leveraged GridSearchCV to identify the best scores and parameters possible for our models. The results are consolidated in the table below. 
 
 ## Modeling and Evaluation 

Three classification models were used: Regression, K-Nearest Neighbors, Random Forest. A baseline score of () was established. Then I leveraged GridSearchCV to identify the best scores and parameters possible for our models. The results are consolidated in the table below. 
 
 |No.||Model||R2 Training Score||R2 Testing Score||Accuracy||Recall/Sensitivity Score||Comments|
 |---||-----||-----------------||----------------||--------||------------------------||--------|
 |1||Logistic Regression||0.6184||0.6180||0.6181||0.4336||Higher than baseline but not very high results|
 |2||KNN||0.7202||0.5586||0.5632||0.4336| 0.4731||Expected that the testing score would be higher than testing score, since KNN models commonly over-fit. Accuracy score lower than baseline score of 0.4680|
 |3||Random Forest||0.9999||0.6218||0.6181||0.5151||Same accuracy scores as the logistic regression model.|
 |4||Logistic w/ Important Features||0.6090||0.6093||0.6083||-||All my scores compared to the initial model decrease|
 |5||KNN w/ Important Features||0.7170||0.5642||0.5603||-|| Slight in improvent in accuracy score compared to the initial KNN model|
 |6||Random Forest w/ Important Features||0.9998||0.5973||0.5930||-||Decrease in accuracy score compared to the original random forest model.|
 |7||Logistic Regression w/ PCA||-||-||-||0.5512||Out all the logistic model variations, this produced the lowest accuracy score|
 |8||KNN w/ PCA||-||-||-||0.5195||Although not the lowest accuracy score out all the KNN model variations, the score did decrease in compariosn to the  KNN model with limited features.|
 |9||Random Forest w/PCA||-||-||-||0.5166||Although not the lowest accuracy score out all the random forest model variations, the score did decrease in comparison to the random forest model with limited features.|
 |10||Logistic Regression w/Grid Search||0.6089||0.6093||0.6087||0.3866||
 |11||KNN w/ Grid Search||0.7708||-||-||0.5195||
 |12||Random Forest w/PCA||-||-||-||0.5166||

 
    
 ## Findings and Conclusions


Source: UCI Machine Learning Repository, https://archive.ics.uci.edu/ml/datasets/Diabetes+130-US+hospitals+for+years+1999-2008
Diabetes: Magnitude and Mechanisms Michael J. Fowler, MD
Clinical Diabetes 2010 Jan; 28(1): 42-46.
