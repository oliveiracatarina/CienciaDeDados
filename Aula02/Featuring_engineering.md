# **Aula 02- Featuring Engineering**

Feature Engineering is a critical process in Machine Learning that involves transforming raw data into meaningful and effective input features for models. Its primary goal is to enhance model performance and accuracy by making data more suitable for the algorithms being used. This process is recognized as one of the most time-consuming yet impactful aspects of data science, as model performance heavily depends on well-crafted features.

# Core Aspects Of Feature Engineering

## **What is Feature Engineering?**

Feature engineering is the art and science of preparing the right data for Machine Learning models. It includes:

* Extracting useful features by deriving new attributes from existing ones.  
* Transforming features to improve their distribution or relationship with the target variable.  
* Encoding categorical data by converting non-numerical data into numerical formats.  
* Detecting and handling outliers to ensure data quality and model robustness.

## **Target Transformation**

Modifying the response (target) variable to improve model performance, especially by correcting skewed distributions and making residuals closer to normal. Common transformations include:

* Logarithmic transformation to stabilize variance and reduce the impact of outliers.

| y′=log(y+1) |
| :---: |

* Square root transformation to reduce skewness.  
   These transformations can significantly improve model fit on skewed or long-tailed datasets.

| y′=sqrty+1 |
| :---: |

## **Feature Extraction and Missing Data Handling** 

Creating new, more informative representations from raw data often involves managing missing values through imputation. Instead of removing missing data, imputation methods such as filling numerical missing values with medians or categorical missing values with the most frequent category preserve data integrity.

* **Imputation (Handling Missing Data):** Addressing absent values in the dataset, which can arise from human error, system interruptions, or privacy concerns. Imputation is generally preferred over simply removing data.  
* **Numerical Imputation:** Assigning zero, NaN, default values, or, more robustly, column medians (which are less affected by outliers than averages).  
* **Categorical Imputation:** Replacing missing values with the most frequent category, or introducing an "Other" category if no dominant value exists.

## **Outlier Detection**

Outliers can be errors or meaningful rare events. Detecting and managing them is crucial. Common detection methods include:

* **Global Outliers:** A single data point drastically different from the entire dataset (e.g., a fraudulent transaction).  
  * **Contextual Outliers:** A data point that is anomalous only within a specific context (e.g., unusually high temperature in winter).  
  * **Collective Outliers:** A group of data points that collectively deviate from typical patterns (e.g., a denial-of-service attack in network traffic).

**Methods for detecting outliers**:

* **Boxplot:** A visual tool that displays quartiles and highlights extreme values as individual points beyond the "whiskers."

| Python Example: |
| :---- |
| `import seaborn as sns; sns.boxplot(x=data['column'])` |

  * **Explanation:** [Boxplot Explanation](https://www.google.com/search?q=https://www.statology.org/boxplot-explanation/)  
  * **Scatter Plot:** Displays the relationship between two variables, where outliers appear as isolated points far from the main data cluster.

| Python Example: |
| :---- |
| `import matplotlib.pyplot as plt; plt.scatter(data['X'], data['Y']); plt.show()` |

  * **Z-Score:** Measures how many standard deviations a data point is from the mean. Values typically beyond a certain threshold (e.g., |Z| \> 3\) are considered outliers.  
  * **Formula:** *Z=fracX−musigma* (where X is data point, mu is mean, sigma is standard deviation).  
  * **Guide:** [Z-Score Guide](https://www.statisticshowto.com/probability-and-statistics/z-score/)  
  * **Interquartile Range (IQR):** Detects outliers using quartile-based boundaries. Values falling outside \[Q1−1.5IQR,Q3+1.5IQR\] are considered outliers, where IQR=Q3−Q1.

| Python Example: |
| :---- |
| `Q1 = data['column'].quantile(0.25); Q3 = data['column'].quantile(0.75); IQR = Q3 - Q1; outliers = data[(data['column'] < (Q1 - 1.5 * IQR)) | (data['column'] > (Q3 + 1.5 * IQR))]` |

## **Feature Scaling**

 Many algorithms require features to be scaled so no attribute dominates because of its numerical range. Two common scaling methods are:

* Normalization (Min-Max scaling) which rescales features to a 0–1 range.  
* Standardization (Z-score normalization) which centers features to mean zero and standard deviation one.

## **Feature Encoding**

Categorical variables must be converted to numerical format. Techniques include:

* Label encoding for ordinal categories.  
* One-hot encoding for nominal categories to avoid implying an order.  
* Target mean encoding that uses the mean of the response variable per category, which can be powerful but requires caution to avoid data leakage.

# ADDITIONAL IMPORTANT CONCEPTS

## **Feature Selection**

Selecting the most relevant features improves model performance and reduces overfitting. Methods include filter, wrapper, and embedded techniques. This step reduces noise, speeds training, and enhances interpretability.

## **Interaction Features**

Creating features by combining existing ones (such as products or ratios) can capture complex relationships in data, especially useful for linear models.

* **Temporal and Domain-Specific Features**  
   In time-series or domain-specific datasets, extracting time components (day, month, hour), lag features, or rolling window statistics enhances the model’s ability to understand patterns. Domain knowledge often guides this feature creation.

* **Automated Feature Engineering Tools**  
   Libraries such as Featuretools or TSFresh can automate complex feature extraction, especially in datasets with time series or relational data, saving time and uncovering hidden patterns.

* **Feature Engineering Pipelines**  
   Performing feature engineering within ML pipelines (e.g., using scikit-learn’s Pipeline) is best practice to prevent data leakage and ensure reproducibility and maintainability of workflows.

# FINAL THOUGHTS ON FEATURE ENGINEERING

Feature engineering is an iterative and cyclical process essential to building high-performing Machine Learning models. Effective feature engineering includes:

* Transforming target variables for better distributions.

* Detecting and handling outliers properly.

* Scaling features to consistent ranges.

* Applying appropriate encoding for categorical data.

* Selecting and creating features that reveal underlying data patterns.

* Using domain knowledge and automation tools wisely.

* Integrating all steps into pipelines for reliability and ease of use.

