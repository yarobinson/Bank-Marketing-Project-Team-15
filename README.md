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

| Team Member | Responsibilities                                                                                       |
|-------------|--------------------------------------------------------------------------------------------------------|
| **Jakub**   | **Outlier Detection and Handling:** <br> Identify and manage outliers in the dataset to ensure data quality. <br> **Organization & Project Management:** <br> Manage group deliverables, set norms, and lead stand-ups . |
| **Lareina** | **Data Type Conversion:** <br> Convert categorical variables to numerical codes for analysis. <br> **Standardization of Variables:** <br> Scale the variables to ensure uniformity across features. |
| **Yihan**   | **Univariate Analysis:** <br> Create histograms, box plots, and bar charts to visualize individual variables. |
| **Yasmine** | **Multivariate Analysis:** <br> Explore interactions between variables through correlation, trend analysis, and visualization. <br> **Feature Selection:** <br> Select relevant features that will be used to predict the target variable. |
| **Amina**   | **Data Splitting:** <br> Split the dataset into training and testing sets for model evaluation. <br> **Model Evaluation :** <br> Implement the KNN algorithm and assess its performance. If the accuracy is high, create the confusion matrix to calculate precision and recall. |
| **Team**    | **Model Evaluation:** <br> If the model performs well, we can conclude the project. If not, we will explore other machine learning models. |


