# Quantitative Risk Analytics & NLP Pipeline
**India Shelter Finance Corporation**

## Executive Summary
This repository contains the end-to-end analytical architectures, predictive machine learning models, and NLP pipelines developed during my Quantitative Analytics Internship. The core objective of these modules is to transform unstructured, high-volume financial data into deterministic, low-latency underwriting insights for automated risk assessment.

---

## System Architecture & Core Modules

### 1. Automated Counterparty & Entity Extraction (Hybrid NLP)
Raw banking statements are notoriously non-grammatical and packed with transaction IDs and banking jargon. Standard black-box NLP fails due to lack of contextual boundaries. To solve the "Vague Narration" problem, I engineered a **Deterministic Hybrid Tiered Pipeline**:
* **Tier 1 (Structural Regex Parsing):** Targets the transaction "skeleton" by leveraging strict regex patterns tailored to banking gateways (UPI, IMPS, POS) to isolate entities between specific delimiters.
* **Tier 2 (High-Value Whitelist):** Deploys a weighted dictionary of high-impact merchants (e.g., Zomato, LIC) to guarantee 100% accuracy on critical discretionary spending categories.
* **Tier 3 (Fallback Logic):** Sanitizes non-standard transactions by algorithmically stripping numerical IDs and common banking jargon, isolating the remaining alphabetical string as the counterparty.
* **Business Impact:** Automates Payer/Payee mapping and instantly segments "Core Income" from "Discretionary Spend," actively accelerating **FOIR (Fixed Obligation to Income Ratio)** calculations in milliseconds.

### 2. Transaction Analytics & Multi-Dimensional Classification
A comprehensive preprocessing and clustering pipeline designed to extract underwriting insights from raw banking narrations. 
* **Methodology:** Implemented TF-IDF vectorization and unsupervised K-Means clustering to logically group unstructured cash flows.
* **Feature Engineering:** Classifies multi-dimensional vectors including Payment Channels, Cash Flow Behavior, Debt/EMI Obligations, and Wealth Indicators. 
* **Business Impact:** Serves as the foundational proof-of-concept for automated customer-level aggregation, income estimation, and predictive credit-risk assessment.

### 3. Predictive Classification Engine (Term-Deposits)
A binary classification model engineered to predict term-deposit subscriptions from 32,950+ historical banking records.
* **Data Sanitization:** Explicitly neutralized duration-based feature data to prevent mathematical data leakage. 
* **Imbalance Resolution:** Mitigated a severe **89:11 class imbalance** by deploying SMOTE (Synthetic Minority Over-sampling Technique).
* **Performance:** Evaluated multiple architectures (Logistic Regression, Random Forest, XGBoost). The optimized tree-based models (XGBoost/RF) achieved an outstanding **94% F1-Score** (up from 70% baseline) with highly balanced precision-recall matrices across both subscriber classes.

---

## Technical Stack
* **Languages:** Python
* **Machine Learning:** XGBoost, Scikit-Learn, Random Forest, SMOTE (Imbalanced-learn)
* **NLP & Text Processing:** Regex, TF-IDF, K-Means Clustering
* **Data Manipulation:** NumPy, Pandas

---
*Note: Sensitive corporate datasets and proprietary customer identifiers have been strictly excluded or anonymized from this repository to comply with India Shelter Finance Corporation's data privacy and security protocols.*
