# Capstone Project: Enterprise Account Matching & Entity Resolution Final Report

## Executive Summary

Organizations often store customer and account data across multiple systems, which leads to duplicate records, inconsistent relationships between parent and subsidiary companies, and fragmented customer views.

This project builds a machine learning solution to identify whether two enterprise account records represent the same company. By detecting duplicate and related accounts, the solution helps improve CRM data quality, reporting accuracy, and operational efficiency.


## Problem Statement

Duplicate account records in enterprise systems create several challenges:
- Inaccurate revenue reporting  
- Poor customer visibility  
- Inefficient sales and operations processes  

The goal of this project is to develop a data-driven approach to determine whether two account records refer to the same company or belong to the same corporate hierarchy.


## Data Overview

The dataset used (`Accounts.csv`) contains enterprise account records with fields such as:
- Company name  
- Address (street, city, state, postal code, country)  
- Industry  
- Source system  
- Global parent and subsidiary identifiers  

Because the dataset does not include labeled duplicate pairs, a **proxy labeled dataset** was created using:
- Matching parent IDs  
- Matching subsidiary IDs  
- Exact matches on normalized fields  


## Approach

The solution follows a structured machine learning workflow:

### 1. Data Cleaning
- Removed duplicate and empty records  
- Standardized text fields (lowercase, trimming)  
- Handled missing values  

### 2. Feature Engineering
- Name similarity (string matching)  
- Address similarity  
- Exact match indicators (city, state, postal code, country)  

### 3. Pair Dataset Creation
- Converted raw records into pairs of accounts  
- Assigned match/non-match labels using hierarchy logic  

### 4. Modeling
Three models were evaluated:
- Logistic Regression (baseline)
- Decision Tree
- Random Forest


## Results

- Random Forest performed best overall  
- Logistic Regression provided strong baseline performance  
- Decision Tree captured nonlinear patterns  

Key insights:
- Company name similarity is the strongest predictor  
- Address features improve model accuracy  
- The dataset is highly imbalanced, requiring careful metric selection  


## Evaluation

Since this is an imbalanced classification problem, the following metrics were used:

- Precision → minimize incorrect merges  
- Recall → identify duplicate accounts  
- F1 Score → balance precision and recall  
- ROC-AUC → overall model performance  

Random Forest achieved the best balance between precision and recall.


## Business Impact

This solution can be used to:
- Detect duplicate accounts  
- Improve CRM data quality  
- Enable accurate reporting and forecasting  
- Support better decision-making  

Rather than automatically merging records, the model can flag high-confidence matches for human review.


## Limitations

- Proxy labels may introduce noise  
- Not all duplicates are captured through hierarchy fields  
- Dataset lacks enriched identifiers (e.g., domain, external IDs)  


## Recommendations and Next Steps

- Use model to flag duplicate accounts  
- Validate results with business users  
- Collect labeled training data  
- Add richer features (domain, identifiers)  
- Improve model performance with advanced algorithms  
- Integrate into CRM workflows  


## Repository Contents

- `Final_Capstone_Entity_Resolution.ipynb` – full technical analysis  
- `Accounts.csv` – dataset  
- `README.md` – project summary  

---

## GitHub Repository

- https://github.com/nagendraprasads/ML-AI-Berkeley-Assignment-24.1 - GitHub repository link
- https://github.com/nagendraprasads/ML-AI-Berkeley-Assignment-24.1/blob/main/README.md - README link
- https://github.com/nagendraprasads/ML-AI-Berkeley-Assignment-24.1/blob/main/Final_Capstone_Entity_Resolution.ipynb - Jupyter Notebook link
