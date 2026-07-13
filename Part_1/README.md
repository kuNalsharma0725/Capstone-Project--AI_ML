## Part1 - Data Acquisition, Cleaning, and Exploratory Analysis 
  The steps of this parts are given below:
  
*  **Load the necessary libraries.**
*  **Load the dataset.**
*  **Null value analysis:**
In the given dataset there is no null values in the numeric feature but if there was some null values in numeric feature. It was filled with fillna(df[col].median()).Because the **mean** is highly sensitive to outliers, using it for imputation would have artificially inflated the missing values, introducing systematic bias into our dataset. **median** is a robust measure of central tendency. As shown in the visualization below, the median represents the true center of the distribution much more accurately for skewed data, ensuring our downstream machine learning models remain unskewed by extreme anomalies.

   But in this dataset there is some null values in the column **extracurricular_participation**, which is a categorical column. According to the need of the dataset, it is filled with **df['parental_education_level'] = df['parental_education_level'].fillna('Unknown').**
  *  **Duplicate detection and removal:**
    There is no duplicates in the dataset.
*  **Data type correction**
*  **Descriptive statistics and skewness:**
  Skewness describes the asymmetry of a data distribution. In a **positively skewed column**, the distribution has a long tail extending toward higher values, which pulls the mean to the **right** the median. In a **negatively skewed column**, the tail extends toward lower values, dragging the mean to the **left** the median.

   **Consequence of imputing missing values with the mean:** Because the mean is highly sensitive to these extreme tails, using it to impute missing values introduces systematic bias: in a positively skewed distribution, mean imputation will artificially inflate the missing data with unrepresentatively high values, while in a negatively skewed distribution, it will replace missing data with values that are disproportionately low.
* **Outlier detection with IQR:** Remove the outliers rows because these extreme values from disproportionately pulling the mean, inflating the standard deviation, or forcing predictive models to overfit to rare anomalies rather than learning the broader, underlying trends of the dataset.
* **Visualizations**
     * A line plot: Between study_hour_per_day and row index
     * A bar chart: study_hours_per_day(num) vs gender(cat)
     * A histogram : attendance_percentage(most skewed num)
     * A scatter plot: study_hours_per_day vs exam_score(both num)
     * A box plot: study_hours_per_day(num) vs gender(cat)
  * **Correlation heat map:** Correlation does not equal causation. Just because two variables move together does not mean one causes the other; instead, a confounding third variable might be pulling the strings behind the scenes.
   For example, if data shows a strong positive correlation between attendence_percentage and exam_score, it would be incorrect to assume only attence percentage is neccesary for exam score. Instead, a third variable explains it.
*  **Imputation strategy comparison:** Based on the direction of skewness, the median was chosen for imputation for both columns.The median resists these extreme tails, providing a much more accurate and fair representation of the central tendency.
*  **Spearman rank correlation:** 1. sleep_hourse vs. age :relationship is monotonic but non-linear
                                  2. study_hours_per_day vs age: approximately linear

   Relying on the wrong metric can cause us to accidentally drop highly predictive features. If a feature has a powerful non-linear relationship with our target variable, Pearson might flag it as "weak" ($r \approx 0$), while Spearman will correctly flag it as a critical asset ($\rho \approx 1.0$). Matching the metric to the distribution ensures a more accurate, optimized feature subset.
* **Grouped aggregation:**
    * Higest mean: Other
    * Higest standard deviation: female
    * Yes, a high within-group standard deviation is a significant concern for a predictive model using that categorical feature.
    * Ratio of the highest group mean to the lowest group mean : 361:351  NO, this ratio is not enough to suggest the categorical feature carries predictive signal.Because a ratio near 1 means that the highest group average and the lowest group average are virtually identical. Because the target's outcome doesn't change regardless of which category a data point belongs to, this categorical feature does not carry a predictive signal and can likely be excluded from your model.
*  **Save the clean dataset:** For the next part
  
