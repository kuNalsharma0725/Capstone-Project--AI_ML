## Part2 - Supervised Machine Learning Model — Build, Train, and Evaluate 
  The steps of this part are given below:

* **Load the necessary libraries**
* **Load cleaned_data.csv**
* **Drop the irrelevant column 'student_id':** Not useful for Machine Learning.
* **Splitting:** Feature matrix: X,  Regression label: y_reg,  Classification label: y_clf
    * **y_reg:** exam_score is the continuous numeric column for predict the exam score of each students on the basis of features.
    * **y_clf:** extracurricular_participation is the binary colums which contains 'Yes' and 'No' values is used to predict a student has taken part in the extracurricular activity or not.
* **Encode categorical columns:**
     *  **Label encoding:** y_clf
     *  **Orndinal encoding:** diet_quality, parental_education_level, internet_quality
     *  **One-Hot encoding:** gender, part_time_job
   
    Label encoding maps each category to an arbitrary sequential number. This introduces a false ordinal relationship because machine learning algorithms interpret these numbers as having a natural, mathematical order and distance, falsely assuming.One-hot encoding completely avoids this problem by splitting the categorical column into multiple binary columns (columns containing only 0 or 1). Each category gets its own dedicated column, turning the feature into a set of independent, equal presence/absence switches.
* **Leak-free train-test split and scaling:** Fitting a scaler on the full dataset constitutes data leakage because it exposes information from the unseen test set to the model during the training process.
  
  ### Regression model — Linear Regression
  * Train the model
  * Predict the values
  * Compute and report: MSE and  R² score
  * Model's coefficients:
     * Large Positive Coefficient: This indicates a strong direct relationship. A one-unit increase in the scaled feature is associated with an increase in the predicted value equal to the exact size of that coefficient. Here, a scaled feature has a coefficient of +14.16, then increasing that scaled feature by exactly 1.0 unit adds 14.16 units to the final prediction.
     * Large Negative Coefficient: This indicates a strong inverse relationship. A one-unit increase in the scaled feature is associated with a decrease in the predicted value equal to the size of that coefficient.
  *Apply Ridge Regression: Ridge Regression introduces a penalty term proportional to the squared size of the coefficients (L2 regularization) to prevent overfitting. This penalty shrinks the coefficients toward zero, producing a smoother, more stable coefficient profile—especially when features are highly correlated.

 ### Classification model — Logistic Regression
 * Value_counts of y_clf_train
 * Train the model
 * Predict class labels
 * Compute and report the matrix
 * Display confusion matrix
 * Plot roc curve
 * Formula:
      * Precision = TP/ TP + FP
      * Recall = TP/ TP + FN
 * Metric Importance:
      * Recall : If False Negatives (FN) are more costly than False Positives. A False Negative means the model completely missed a positive case. For example, in medical diagnostics or fraud detection, missing a critical case is dangerous or highly expensive, so you want to maximize Recall to catch as many true positives as possible.
      * Precision : If False Positives (FP) are more costly. A False Positive means a false alarm. For instance, in spam filtering or legal sentencing predictions, falsely labeling an innocent email as spam or an innocent person as guilty causes immediate disruption, so you want the model to be highly precise when it does flag something as positive.
     * Meaning of the AUC Value:The AUC (Area Under the ROC Curve) value measures the model's overall ability to distinguish, or separate, the two classes across all possible classification thresholds.
* Decision-threshold sensitivity:
       * Precision = TP/ TP + FP
       * Recall = TP/ TP + FN
* threshold that maximises F1-score:
* Recall is more important for this classification task because the  goal is to identify every single student who is involved in extracurriculars.
* Threshold Tuning: To Optimize for Recall lower the threshold. To Optimize for Precision higher the threshold.

* **Regularization experiment on Logistic Regression:**In logistic regression, the parameter C controls the inverse regularization strength, meaning it determines the balance between maximizing the model's training accuracy and keeping the model weights small to prevent overfitting.
* **Bootstrap confidence interval for AUC difference:**
*  **Save and download the scaling dataset**













