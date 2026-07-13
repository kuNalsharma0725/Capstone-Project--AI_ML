## Part3 - Advanced Modeling — Ensembles, Tuning, and Full ML Pipeline
  The steps of this part are given below:

  * **Load the necessary libraries**
  *  **Load the scaled dataset**
  *  **Splitting**
  *  **Decision Tree baseline:**
       * Train the model with no hyperparameter
       * Predict traim and test outcome
       * Report train accuracy and test accuracy: Train accuracy is 1.0 and test accuracy is 0.585
       * Yes, this decision tree is overfitting. Model perform exceptionally well on training data but poorly on test data, it indicates that the model has "memorized" the noise and specific patterns of the training set rather than learning the underlying trends that generalize to new, unseen data.
            Decision trees are considered high-variance because they are extremely sensitive to the specific data points in the training set. At every node, the tree makes the best possible local choice to minimize error (or maximize information gain). It does this without looking ahead to see if that choice will cause problems later.
  * **Controlled Decision Tree:**

     * Train controlled tree with hyperparameters(max_depth=5, min_samples_split=10)
     * Predict train and test outcomes
     * Report train accuracy and test accuracy: Train accuracy is 0.7 and test accuracy is 0.695
     * Role of max depth:This defines the maximum number of levels the tree is allowed to grow from the root to the leaf. It reduces the high varience.
     * Role of min sample split:This defines the minimum number of samples a node must contain in order to be considered for further splitting.It stops the tree from creating branches. It also reduces the high varience.

  * **Decision tree with criterion='gini':**

    * Train the model with hyperparameter(max_depth=5, criterion='gini')
    * Predict train and test outcomes
    * Report train accuracy and test accuracy: Train accuracy is 0.7125 and test accuracy is 0.69
    * formula for gini impurity: (1 - Σ pi²)
    * When a node has a Gini impurity of 0, it means that the node is perfectly pure.In the context of classification, this indicates that 100% of the samples in that specific node belong to the exact same class.
   
  * **Decision tree with criterion='entropy':**

    * Train the model with hyperparameter(max_depth=5, criterion='entropy')
    * Predict train and test outcomes
    * Report train accuracy and test accuracy: Train accuracy is 0.70375 and test accuracy is 0.67
    * formula for gini impurity: (-Σ pi log2(pi))

  * **Random forest:**

       * Train the model with hyperparameter(n_estimators=100, max_depth=10)
       * Predict train and test outcomes
       * Report train accuracy and test accuracy: Train accuracy is 0.94625 and test accuracy is 0.69
       * Report roc_auc score: Train accuracy is 0.9166666666666667 and test accuracy is 0.4928571428571429
       * Random Forest feature importance provides a "global" view of which variables matter most, while linear regression coefficients provide a specific "weight" for each variable.
       * agging (Bootstrap Aggregating) reduces variance by training multiple deep decision trees on different, random subsets of the data and features, which prevents any single tree from being overly influenced by specific noise or outliers in the training set. By using bootstrap sampling (sampling with replacement), each tree is exposed to a slightly different perspective of the data, while selecting only a random subset of  √n features at each split decorrelates the trees, ensuring they don't all make the exact same mistakes.

  * **Gradient Boosting:**

       * Train the model with hyperparameter(n_estimators=100, learning_rate=0.1, max_depth=3)
       * Predict train and test outcomes
       * Report train accuracy and test accuracy: Train accuracy is 0.82875 and test accuracy is 0.64
       * Report roc_auc score: Train accuracy is 0.737542549 and test accuracy is 0.4809523809

    * ** Feature ablation study:** Whether removing those features was the right move depends entirely on the AUC performance delta observed during your validation.
   
  * **Second Random forest:**

       * Train the model with hyperparameter(n_estimators=100, max_depth=100)
       * Predict train and test outcomes
       * Report train accuracy and test accuracy: Train accuracy is 0.9225 and test accuracy is 0.685
       * Report roc_auc score: Train accuracy is 0.0.87984496 and test accuracy is 0.4940477

 * **Cross-validated comparison:**  Cross-validation provides a more reliable estimate of performance because it eliminates the "luck of the draw" inherent in a single train-test split.Cross-validation solves this by Rotating the Test Set, Reducing Variance in Evaluation, Maximizing Data Usage.
     
 *  **Hyperparameter tuning with GridSearchCV:**

      Total number of model configurations evaluated during this hyperparameter tuning = 5 folds * 18 candidates = 90

      The Trade-of:
    
    *  Grid Search: Exhaustively tests every single combination in your defined grid. Precision is high. Best used when  have a large search space or limited time/compute resources.
    *  Randomized Search: Exhaustively tests every single combination in your defined grid. Precision is probalistic. Best used when have a small number of parameters and want the absolute best results.

  * **Serialize the best model**
    
    
