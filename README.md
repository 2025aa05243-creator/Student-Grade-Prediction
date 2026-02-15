Student Grade Prediction App

Student Grade Prediction App is a Streamlit web app to train and compare multiple ML models for predicting student grade categories, and to evaluate them on a held out test set.
1.	Problem statement:
The models are solving a supervised classification problem: predicting a student’s grade category (GradeClass) from their academic, demographic, and behavioral features.  This is a multi class classification task where the input is a set of student features and the output is a discrete grade class
Given historical data about students (such as study time, attendance, past grades, and socio demographic factors), the goal is to predict the final grade category for each student

2.	Dataset: Student Performance dataset
Kaggle source: https://www.kaggle.com/datasets/bhuvaneshwarisa/student-performance-dataset
This dataset is taken from Kaggle, which contains anonymized academic and demographic information about students, along with their final GPA and a derived grade category (GradeClass).  The features include variables such as study time per week, absences, parental education, extracurricular involvement, and support indicators, making it suitable for educational analytics and grade classification tasks.

3.	Features and target columns
The following columns are used as features (inputs) to the models: -
The following columns from `Student_performance_data.xlsx` are used as features: - 

1.	Age
2.	Gender
3.	Ethnicity
4.	ParentalEducation
5.	StudyTimeWeekly
6.	Absences
7.	Tutoring
8.	ParentalSupport
9.	Extracurricular
10.	Sports
11.	Music
12.	Volunteering
13.	GPA

Dropped colimn: `StudentID` exists in the raw dataset but is treated as a pure identifier and is excluded from the feature set before training and prediction. 
Target column (label) - GradeClass – categorical grade used as the prediction target.

4.	Models:
1.	Logistic Regression
2.	Decision Tree
3.	KNN
4.	Naive Bayes
5.	Random Forest
6.	XGBoost
(Each model is trained in notebook and saved as joblib)


ML Model Name	Accuracy	AUC	Precision	Recall	F1	MCC
Logistic Regression	0.801670146	0.889592765	0.791938606	0.801670146	0.791798196	0.700532674
Decision Tree	0.868475992	0.869953192	0.867985807	0.868475992	0.865187298	0.804650162
kNN	0.636743215	0.778435629	0.613137533	0.636743215	0.618363113	0.44394798
Naive Bayes	0.753653445	0.88855704	0.785709233	0.753653445	0.74879553	0.641697392
Random Forest	0.910229645	0.908752588	0.913105217	0.910229645	0.90266591	0.865439199
Logistic Regression	0.801670146	0.889592765	0.791938606	0.801670146	0.791798196	0.700532674


5.	Observations on the performance of each model

Model	Observations
Logistic Regression	Achieves good overall performance with Accuracy ≈ 0.80 and AUC ≈ 0.89, indicating a well-fitted linear decision boundary.
	Precision, Recall and F1 are all ≈ 0.79–0.80, showing balanced behaviour without strong bias toward any class.

Decision Tree	Performs better than Logistic Regression, with higher Accuracy ≈ 0.87 and similar AUC ≈ 0.87, capturing nonlinear patterns in the data.
	Precision, Recall and F1 are ≈ 0.86, but as a single tree it may overfit more than ensemble methods despite strong metrics on this test set.

kNN	Shows the weakest performance: Accuracy ≈ 0.64 and AUC ≈ 0.78, meaning many instances are misclassified.
	Lower Precision, Recall and F1 (≈ 0.62–0.64) suggest that the distance-based neighbourhood assumption is not well suited to this dataset.

Naive Bayes	Reaches moderate Accuracy ≈ 0.75 with relatively high AUC ≈ 0.89, doing better than kNN but worse than tree-based ensembles.
	Precision, Recall and F1 around 0.75 indicate reasonable performance despite the naive feature-independence assumption.

Random Forest (Ensemble)	Delivers the best results among the non-boosting models, with Accuracy ≈ 0.91 and AUC ≈ 0.91, showing strong generalization on tabular data.
	Precision, Recall and F1 are ≈ 0.90, confirming stable and robust performance with low error rates across classes.

XGBoost (Ensemble)	Achieves Accuracy ≈ 0.92 and AUC ≈ 0.91, slightly edging out Random Forest and giving the highest MCC (≈ 0.88), making it the top-performing model overall on this dataset.
	Very high Precision, Recall and F1 (≈ 0.91–0.92) indicate that gradient-boosted trees capture complex patterns while maintaining excellent balance between false positives and false negatives.


6.	Students Performance Classification – Streamlit App
Overview
This Streamlit application provides an interactive interface for predicting and evaluating student performance classifications using multiple pre-trained machine learning models.
Users can upload a CSV file containing test data and optionally include the GradeClass column for evaluation against ground truth labels.
The app computes detailed metrics such as accuracy, F1-score, precision, recall, AUC, and displays confusion matrices as well as per-class performance reports.

What app does:
•	Automatic feature alignment and scaling
•	Prediction generation for uploaded datasets
•	Evaluation of classification metrics if true labels are available
•	Visualization of confusion matrix and classification report
•	Metrics per class and per model report

<img width="468" height="637" alt="image" src="https://github.com/user-attachments/assets/c3c08e12-fa07-4d73-9eb0-9b238393d29c" />
