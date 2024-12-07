# Predicting Client Term Deposit Subscription Using Demographic Profiles, and Financial Situation
This project aims to predict whether clients will subscribe to a term deposit based on data from direct marketing campaigns conducted by a Portuguese banking institution. The model leverages demographic, financial, and campaign-related information to identify clients most likely to respond positively, enhancing targeted marketing efforts.

## Project Overview
This project uses a dataset from a Portuguese bank’s direct marketing campaigns, which were conducted via phone calls from 2008 to 2010. The dataset includes details on client demographics, financial situation, and various aspects of their interactions with marketing campaigns. The goal is to classify clients who are likely to subscribe to a term deposit (target variable y), helping banks to optimize resource allocation and improve campaign success rates.

## Dataset Characteristics

- Source: https://archive.ics.uci.edu/dataset/222/bank+marketing

- Instances: 45,211

- Features: 16 (Categorical and Numerical)

- Associated Task: Classification

- No Missing Values

## Key Variables
+ **Demographic Data:**

  age: Age of the client

  job: Job type (e.g., admin, blue-collar, technician)

  marital: Marital status (e.g., married, single)

  education: Education level (e.g., secondary, tertiary)

  default: Credit default status

+ **Financial Data:**

  balance: Average yearly balance in euros

  housing: Housing loan status

  loan: Personal loan status

+ **Campaign Information:**

  contact: Type of contact communication (e.g., cellular, telephone)

  duration: Duration of the last contact in seconds

  campaign: Number of contacts in the current campaign

  pdays: Days since last contact in a previous campaign

  previous: Number of contacts before this campaign

  poutcome: Outcome of the previous campaign (e.g., success, failure)

+ **The target variable y indicates whether the client subscribed to a term deposit (yes or no).**

## Project Steps

**Data Exploration:** Understand and visualize the dataset, examining distributions and correlations among features.

**Data Preprocessing:** Clean data by encoding categorical variables, normalizing numerical features, and addressing any inconsistencies.

**Feature Engineering and Selection:** Identify relevant features and engineer new ones to improve model accuracy.

**Modeling:** Develop classification models to predict term deposit subscription.

**Evaluation:** Assess model performance using metrics like Accuracy, Precision, Recall, F1 Score, and AUC-ROC.

**Insights:** Analyze feature importance to provide actionable insights into factors that drive client subscriptions, with a focus on optimizing marketing efforts.

## Project Structure

- data/: Contains raw and processed datasets.

- experiments/: Tracks and documents experimental results and variations, including different configurations, hyperparameters, and performance metrics.

  Usage: Useful for managing various model versions and tuning iterations, making it easy to revert to prior setups or replicate results.
  
- models/: Contains trained models and their associated metadata.

  Files Included: Serialized models (e.g., .pkl files if using Python’s pickle or joblib libraries) for easy reloading and further analysis.

  Model performance summaries, validation scores, and logs to keep track of each model’s success metrics.
  
- reports/: Contains generated reports summarizing analysis, findings, and model performance.

  Files Included: HTML, PDF, or markdown files with visualizations and key results.

  Presentation materials or summaries that can be shared with stakeholders or non-technical audiences.

- src/ : Project source code where all scripts and functions are stored.

  Contents: Scripts for data preprocessing, feature engineering, and transformations.

  Modeling scripts that include model training, evaluation, and predictions.

  Utility functions for repetitive tasks, such as data loading, cleaning, and evaluation metric calculations.
  
- README.md : This file provides an overview of the project, objectives, structure, requirements, and setup instructions.

  Instructions for setup and running the code, including how to replicate results or extend the project.

- .gitignore : Specifies files and directories for Git to ignore, ensuring sensitive or large files aren’t accidentally committed.

## Team Responsibilities

This project involves collaboration among team members, each focusing on specific tasks to ensure successful execution. Below is a breakdown of responsibilities:

| Team Member | Responsibilities                                                                                       | Video Link                           |
|-------------|--------------------------------------------------------------------------------------------------------|--------------------------------------|
| **Jakub**   | **Outlier Detection and Handling:** <br> Identify and manage outliers in the dataset to ensure data quality. <br> **Organization & Project Management:** <br> Manage group deliverables, set norms, and lead stand-ups. | [Watch Video](https://shorturl.at/g7uxc)          |
| **Lareina** | **Data Type Conversion:** <br> Convert categorical variables to numerical codes for analysis. <br> **Standardization of Variables:** <br> Scale the variables to ensure uniformity across features. | [Watch Video](https://youtu.be/kZXraUA9e5A)       |
| **Yihan**   | **Univariate Analysis:** <br> Create histograms, box plots, and bar charts to visualize individual variables. | [Watch Video](https://www.youtube.com/watch?v=YoMtu1BdmhQ)         |
| **Yasmine** | **Multivariate Analysis:** <br> Explore interactions between variables through correlation, trend analysis, and visualization. <br> **Feature Selection:** <br> Select relevant features that will be used to predict the target variable. | [Watch Video](#yasmine-video)       |
| **Amina**   | **Data Splitting:** <br> Split the dataset into training and testing sets for model evaluation. <br> **Model Evaluation:** <br> Implement the KNN algorithm and another model, create the confusion matrix to calculate precision and recall. | [Watch Video](https://youtu.be/5QmS_MCIUdE)         |






# Experiment Overview and Business Decision-Making Goal

This experiment aimed to develop a machine learning classifier to predict whether clients would subscribe to a term deposit based on historical marketing and client data. Two models were tested—**KNN** and **XGBoost**—with XGBoost showing superior performance, particularly in recall (90%), making it highly effective for identifying potential subscribers.

## **Business Goal**  
The ultimate objective of this analysis is **to optimize marketing campaigns by accurately targeting clients most likely to subscribe**. By leveraging a high-recall model, the business can:

### 1. **Maximize Client Outreach**
Ensure that nearly all potential subscribers are identified and contacted, increasing the likelihood of campaign success.

### 2. **Resource Allocation**
Use insights from feature importance (e.g., call duration, account balance) to prioritize high-value clients, reducing wasted effort on unlikely subscribers.

### 3. **Enhance Campaign Effectiveness**
Adjust strategies to focus on impactful periods (e.g., campaigns in May) and improve engagement tactics during calls (e.g., extending call duration).


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

### Outcome
- Dataset reduced to 41,186 rows after removing outliers.
- Improved dataset reliability for subsequent analysis.


## Convert categorical variables to numerical

### Goal
Converting categorical variables to numerical values ensures compatibility with machine learning algorithms, improves model performance, enhances interpretability, and facilitates more efficient data storage and processing. 

### Methodology
**One-Hot Encoded**: This Encoding method fits becasue the data set showing small to medium cardinality and has nominal categorical variables where categories do not have a meaningful order.


## Scale the variables

### Goal
Scaling variables ensures that all features are on a comparable scale, improving model performance, reducing bias, enhancing interpretability, and maintaining numerical stability.

### Methodology
**StandardScaler**: Using StandardScaler ensures that the numerical features in the DataFrame are standardized to a common scale. This normalization can significantly enhance model performanceand and ensure that features with different units do not bias the model. It will also give better support for algorithms like k-nearest neighbors (KNN), k-means clustering which rely on distance metrics, scaled features ensure that no single feature dominates the distance calculations.

## Univariate Analysis 

### Goal
To understand the distribution and characteristics of key features and their relationship to the target variable (term deposit subscription), providing insights for feature selection.

### Methodology
**Histograms**: Used histograms to examine the distribution of continuous variables (e.g., age, balance, call duration) to uncover patterns and skewness. This method is crucial in machine learning preprocessing, as understanding the distribution of data helps with feature engineering and selecting appropriate models, especially for algorithms sensitive to data distribution (e.g., decision trees, logistic regression).

**Boxplots**: Applied boxplots to detect outliers and visualize feature spread. Identifying outliers is essential for improving model performance, as extreme values can distort predictions, particularly in distance-based models like K-Nearest Neighbors (KNN) or Support Vector Machines (SVM).

### Key Observations
- **Call Duration**: Longer call durations are highly correlated with higher subscription rates, indicating deeper client engagement is key.
- **Balance**: Clients with higher balances show a significantly higher likelihood of subscribing, suggesting financial stability is a strong predictor.
- **Campaign Contacts**: Most successful subscriptions happen after the first contact, with diminishing returns for follow-up calls, highlighting the importance of effective initial outreach.


## Bivariate and Multivariate Analysis

### Goal
Analyze the relationships between two or more variables to determinethe association and strength of association of variables through coorelation and visualizations, providing insights for feature selection. 

### Methodology
**Correlation Matrix**: Created a correlation matrix to determine which variables had a significant relationship with eachother. This method was important to identify variables with strong association for analysis. 

**Bar Charts**: Used bar charts for bivariate analysis to visualize the relationship between two variables. This method was important when analyzing variables for comparison over time or by volume to determine which combination of variables had the strongest association. 

**Scatter Plots**: Used scatter plots for multivariate analysis to visualize the relationship between two or more variables. This method was important for showcasing the relationship between two variables over time to identify patterns within the data. 

### Key Observations
- **Job Types**: Positive coorelation between certain job types and term deposit subscription. Through visualization, students, retirees and those who are unemployed were shown as most likely to subscribe to term deposits. 
- **Marital Status**: Positive coorelation between being single and term deposit subscription. Through visualization, single clients were shown as more likely to subscribe to term deposits than married or divorced clients.  
- **Balance, Age and Subscription Rate**: Clients between the ages of 20-70 with a balance of 0 to 10,000 were most likely to subscribe to term deposits. 
- **Summary**: From the insights, we can suggest that these categories of clients are more likely to take on the risk of term deposits and future marketing campaigns targeted towards these groups may be successful in increasing subscription rates. 

---

## **Key Feature Insights**
Below is the SHAP feature importance plot, showing the most influential factors in predicting client subscriptions:

![SHAP Feature Importance](reports/Feature_importance.png)

### Observations:
- **Duration**: Longer call durations strongly correlate with higher subscription likelihood.  
- **Month (May)**: Campaigns conducted in May tend to have higher success rates.  
- **Balance**: Clients with higher balances are more likely to subscribe.  
- **Housing Loans**: Clients without housing loans are more likely to respond positively.

## **Decision-Making Impact**
This model empowers data-driven decisions to:
- Increase the **return on investment (ROI)** for marketing campaigns.  
- Focus resources on **high-potential leads**, minimizing costs associated with false positives.  
- Continuously refine strategies using actionable insights from the data (e.g., targeting clients without housing loans or with higher balances).  

By integrating this model into the marketing pipeline, the business can effectively:
- Increase subscription rates.  
- Enhance client satisfaction.  
- Improve overall campaign efficiency.

