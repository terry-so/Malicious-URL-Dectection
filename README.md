# Malicious URL Detection using Machine Learning

This project explores and compares various machine learning models and feature engineering techniques for the detection of malicious URLs. The goal is to distinguish between benign URLs and those associated with defacement, phishing, and malware.

## Table of Contents
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Methodology](#methodology)
    - [Feature Engineering](#feature-engineering)
    - [Modeling](#modeling)
- [Results](#results)
    - [Model Performance](#model-performance)
    - [Feature Importance](#feature-importance)
- [Conclusion](#conclusion)

## Problem Statement
[cite_start]Malicious URLs are a significant cybersecurity threat, used to conduct scams, steal user information, and distribute malware. [cite: 4, 5] [cite_start]This project aims to analyze the features that distinguish malicious URLs from benign ones and to evaluate the effectiveness of different detection methods. [cite: 10] The primary objectives were to:
1.  [cite_start]Investigate two feature engineering approaches: manual feature extraction and character-level n-gram tokenization. [cite: 11]
2.  [cite_start]Compare the performance of supervised classification models (Logistic Regression, Linear SVM, Random Forest, XGBoost) against an anomaly detection model (One-Class SVM). [cite: 12]

## Dataset
[cite_start]The dataset used for this project was sourced from Kaggle and contains 651,000 URLs. [cite: 15, 24] It is comprised of four categories:
* [cite_start]**Benign URLs:** ~428,000 [cite: 15]
* [cite_start]**Defacement URLs:** ~96,000 [cite: 15]
* [cite_start]**Phishing URLs:** ~94,000 [cite: 15]
* [cite_start]**Malware URLs:** ~32,000 [cite: 15]

[cite_start]Each entry in the dataset includes the URL string and its corresponding type. [cite: 16]

| URL Type | Definition |
| :--- | :--- |
| Benign | [cite_start]A URL that belongs to a safe website with no malicious intent. [cite: 18] |
| Defacement | [cite_start]A URL that leads to a webpage that has been altered by an attacker. [cite: 18] |
| Phishing | [cite_start]A URL for a fraudulent website designed to deceive users into revealing sensitive information. [cite: 18] |
| Malware | [cite_start]A URL that hosts malware intended to infect a user's device. [cite: 18] |

## Methodology

### Feature Engineering
Two distinct feature engineering techniques were employed to represent the URLs for the machine learning models:

1.  [cite_start]**Manual Feature Extraction:** This method involved creating features based on the structural and lexical properties of the URLs. [cite: 32] The features extracted include:
    * [cite_start]URL length [cite: 34]
    * [cite_start]Ratio of letters, digits, and non-alphanumeric characters [cite: 35, 36, 37]
    * [cite_start]Counts of special characters such as '.', '-', '_', '/', '?', and '%' [cite: 38, 39, 40, 41, 42, 43]
    * [cite_start]Presence of keywords like 'http', 'https', 'html', and 'php' [cite: 44]

2.  [cite_start]**Tokenized Bag-of-Words (N-grams):** This approach involved tokenizing the URL strings into character-level 2-grams and 3-grams. [cite: 47] [cite_start]This allows the models to capture patterns in the URL structure without manual feature design. [cite: 47] [cite_start]Each URL is then represented as a sparse vector based on the frequency of these n-grams. [cite: 50]

### Modeling
The project evaluated and compared both supervised classification and anomaly detection paradigms.

**Supervised Classification**
[cite_start]Models were trained on a labeled dataset of both benign and malicious URLs. [cite: 56] The following algorithms were used:
* [cite_start]**Logistic Regression** [cite: 57]
* [cite_start]**Linear SVM with SGD** [cite: 57]
* [cite_start]**Random Forest** [cite: 57]
* [cite_start]**XGBoost** [cite: 57]

**Anomaly Detection**
[cite_start]This approach involved training a model solely on benign URLs to learn the characteristics of "normal" web addresses. [cite: 59] [cite_start]Any URL that deviates from this learned pattern is flagged as an anomaly (malicious). [cite: 60]
* [cite_start]**One-Class SVM** [cite: 61]

[cite_start]Hyperparameter tuning was conducted for all models using 5-fold cross-validation with grid search for linear models and One-Class SVM, and Optuna for Random Forest and XGBoost. [cite: 64, 66]

## Results

### Model Performance
The performance of the models was evaluated based on accuracy, precision, recall, and F1-score. A summary of the results is presented below.

| Model | Feature Engineering | Accuracy | F1-Score |
| :--- | :--- | :---: | :---: |
| **Linear SVM** | Manual | [cite_start]0.84 [cite: 214] | [cite_start]0.80 [cite: 214] |
| | Tokenized | [cite_start]**0.99** [cite: 214] | [cite_start]**0.99** [cite: 214] |
| **Logistic Regression** | Manual | [cite_start]0.85 [cite: 214] | [cite_start]0.82 [cite: 214] |
| | Tokenized | [cite_start]0.98 [cite: 214] | [cite_start]0.98 [cite: 214] |
| **Random Forest** | Manual | [cite_start]0.95 [cite: 214] | [cite_start]0.94 [cite: 214] |
| | Tokenized | [cite_start]0.98 [cite: 214] | [cite_start]0.98 [cite: 214] |
| **XGBoost** | Manual | [cite_start]0.95 [cite: 214] | [cite_start]0.94 [cite: 214] |
| | Tokenized | [cite_start]0.98 [cite: 214] | [cite_start]0.98 [cite: 214] |
| **One-Class SVM** | Manual | [cite_start]0.78 [cite: 214] | [cite_start]0.79 [cite: 214] |
| | Tokenized | [cite_start]0.66 [cite: 214] | [cite_start]0.66 [cite: 214] |

**Key Findings:**
* [cite_start]Tokenized n-gram features consistently outperformed manually extracted features across all supervised models. [cite: 205]
* [cite_start]Supervised learning models significantly outperformed the One-Class SVM anomaly detection approach. [cite: 212]
* [cite_start]When using manual features, tree-based models like Random Forest and XGBoost performed better than linear models. [cite: 206]
* [cite_start]With tokenized n-grams, linear models demonstrated exceptional performance, slightly surpassing the tree-based models. [cite: 207]

### Feature Importance
An analysis of the XGBoost model trained on manual features revealed the most influential characteristics for detecting malicious URLs.

![Top 10 Feature Importances](ISYE_6740_Project_page-008-0.png)

The most significant features were:
1.  [cite_start]URL length [cite: 199]
2.  [cite_start]Ratio of non-alphanumeric characters [cite: 199]
3.  [cite_start]Ratio of letters [cite: 199]
4.  [cite_start]Ratio of digits [cite: 200]
5.  [cite_start]Count of slashes [cite: 200]

## Conclusion
[cite_start]This project demonstrates that supervised machine learning models, particularly when trained on character-level n-gram features, are highly effective for detecting malicious URLs. [cite: 226] [cite_start]The Linear SVM and XGBoost models trained with tokenized features achieved the best performance. [cite: 226] [cite_start]While manual feature extraction offers greater interpretability, it is less predictive than tokenization. [cite: 227] [cite_start]Anomaly detection with One-Class SVM proved to be less effective than supervised methods for this task. [cite: 228]

[cite_start]Future work could explore deep learning models, such as CNNs or RNNs, to automatically learn features from the raw URL strings, potentially improving detection accuracy further. [cite: 221]
