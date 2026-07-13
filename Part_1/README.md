## Part1 - Data Acquisition, Cleaning, and Exploratory Analysis 
  The steps of this parts given below:
  
**Load the necessary libraries.**
**Load the dataset.**
**Null value analysis**
In the given dataset there is no null values in the numeric feature but if there will be some null values in numeric feature. It will be filled with fillna(df[col].median()).Because the **mean** is highly sensitive to outliers, using it for imputation would have artificially inflated the missing values, introducing systematic bias into our dataset. **median** is a robust measure of central tendency. As shown in the visualization below, the median represents the true center of the distribution much more accurately for skewed data, ensuring our downstream machine learning models remain unskewed by extreme anomalies.



