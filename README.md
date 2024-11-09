# Assignment 2 Report

**Author**: Juan Sebastian Rodriguez Reyes  
**Contact**: c0915840@mylambton.ca  

## 1. Dataset Description

This dataset aims to predict student placement status based on educational, professional, and test scores, with `status` being the target variable. Key columns include:

- **ssc_p**: Secondary Education percentage (10th Grade).
- **hsc_p**: Higher Secondary Education percentage (12th Grade).
- **degree_p**: Degree percentage.
- **workex**: Work experience status (Yes/No).
- **etest_p**: Employability test percentage.
- **specialisation**: MBA specialization (e.g., Marketing & HR, Marketing & Finance).
- **status**: Target variable indicating job placement status (e.g., Placed, Not Placed).

## 2. Data Preprocessing Steps

To ensure model compatibility and performance, the following preprocessing steps were applied:

- **Categorical Encoding**: Categorical features were encoded numerically for compatibility. Columns with two categories were label-encoded, while columns with three categories used one-hot encoding.
- **Data Splitting**: Data was split into 70% training and 30% testing. The split was applied before filling missing values, and SMOTE was implemented on the training dataset only to avoid data leakage.
- **Handling Missing Values**: Missing values occurred in the `salary` column. Target imputation was applied using average salaries per degree category in the training set.
- **Balancing the Data**: SMOTE was applied to the training data due to class imbalance, ensuring equal record counts per target category.

## 3. Model Selection and Rationale

The following models were selected for evaluation:

- **Logistic Regression**: Chosen for its simplicity and interpretability in binary classification.
- **Random Forest**: Used for its robustness to overfitting and ability to capture non-linear patterns.
- **Support Vector Machine (SVM)**: Effective in high-dimensional spaces for creating optimal decision boundaries.
- **XGBoost**: Known for handling complex relationships via gradient boosting.
- **Voting Classifier**: An ensemble combining the above models to improve prediction accuracy by reducing individual model biases.

Every model was evaluated with GridSearchCV to select the model with the best hyperparameters.

## 4. Evaluation Metrics

Each model and the Voting Classifier were evaluated using:

- **Accuracy**: Measures the overall correctness of predictions.
- **Precision**: Evaluates the proportion of correct positive identifications.
- **Recall**: Determines the model's ability to identify all relevant instances.
- **F1 Score**: Harmonic mean of precision and recall, balancing both metrics.

These metrics provide a comprehensive evaluation of model performance, balancing sensitivity and specificity. The results are summarized below for each model:


| Model                  | Accuracy | Precision | Recall | F1 Score |
|------------------------|----------|-----------|--------|----------|
| Logistic Regression    |    0.8   |    0.84   |  0.86  |   0.85   |
| Support Vector Machines|    0.82  |    0.85   |  0.89  |   0.87   |
| Random Forest          |    0.89  |    0.88   |  0.98  |   0.92   |
| XGBoost                |    0.94  |    0.93   |  0.97  |   0.96   |
| Voting Classifier      |    0.88  |    0.93   |  0.87  |   0.91   |

Considering the class imbalance, F1 Score was prioritized for comparison among models.


## 6. Conclusion

After comparing the models, **XGBoost** emerged as the top performer based on accuracy, F1 score, and balanced precision-recall values, capturing underlying patterns effectively. It also demonstrated the lowest signs of overfitting, with close metric gaps between training and testing datasets. While the Voting Classifier provided good performance, the lower accuracy of Logistic Regression and SVM slightly reduced overall effectiveness, making **XGBoost** the most suitable model for this classification problem.
