# Bank Marketing-Team 15
This repository contains a machine learning project aimed at predicting customer behavior during sales calls.

---

# Data Quality

## Data Preprocessing

### Goal
The preprocessing step focused on preparing the raw dataset for further analysis by:
- Removing irrelevant columns with high levels of "unknown" values.
- Filtering out rows with missing or invalid data.
- Ensuring appropriate data types for numerical and categorical variables.

### Steps
1. Imported the dataset using **pandas** and explored its structure (e.g., column names, data types, missing values).
2. Assessed categorical variables with "unknown" values and removed rows or columns as needed.
3. Generated descriptive statistics for numerical variables to identify potential outliers.

Example insights:
- **Average Age**: 41 years
- **Average Balance**: €1362, with significant variability.
- **Potential Outliers**: Extreme values in `balance`, `duration`, and `campaign`.


## Data Cleanup

### Goal
The cleanup process ensured the dataset was free from "unknown" or irrelevant values and ready for model training.

### Steps
1. Removed rows or columns based on thresholds for missing or "unknown" values.
2. Saved the cleaned dataset for further use.

### Code
```python
columns_to_clean = ['job', 'education']
for column in columns_to_clean:
    if column in df.columns and df[column].dtype == 'object':
        df = df[df[column] != 'unknown']
```
### Outcome
 - Cleaned dataset with significant reductions in missing values.
 - Removed irrelevant columns, such as poutcome and contact.

## Outlier Detection

### Methodology
Used **Isolation Forest**, an unsupervised machine learning algorithm, to detect and remove outliers. This approach was chosen for its robustness in handling multidimensional data and flexibility with non-normal distributions.

### Steps
1. Identified numerical columns for outlier detection.
2. Fitted the Isolation Forest model with a contamination rate of 5%.
3. Removed data points identified as outliers.

### Code
```python
from sklearn.ensemble import IsolationForest
model = IsolationForest(contamination=0.05, random_state=42)
df_clean['outlier'] = model.predict(df_clean.select_dtypes(include=[np.number]))
df_cleaned = df_clean[df_clean['outlier'] == False]
```

### Outcome
- Dataset reduced to 41,186 rows after removing outliers.
- Improved dataset reliability for subsequent analysis.

---
