### Malicious URL Detection Project Summary

[cite_start]In this project, I developed and evaluated machine learning models to detect malicious URLs[cite: 10]. [cite_start]The goal was to differentiate between benign URLs and those used for phishing, malware, and defacement[cite: 100].

***

### Methods & Models

* [cite_start]**Feature Engineering**: I tested two approaches: (1) manually extracting structural features like URL length and character ratios [cite: 32, 34, 35, 36][cite_start], and (2) using a Bag-of-Words model with character-level 2-grams and 3-grams[cite: 46, 47].
* [cite_start]**Algorithms**: I compared several models, including **Logistic Regression**, **Linear SVM**, **Random Forest**, and **XGBoost** for supervised classification [cite: 57][cite_start], alongside a **One-Class SVM** for anomaly detection[cite: 12, 61].

***

### Key Results & Conclusion

* [cite_start]**Best Performance**: The supervised models trained with **tokenized n-gram features** were the most effective[cite: 205]. [cite_start]Linear SVM achieved an accuracy of 0.99 and an F1-score of 0.99[cite: 110, 214].
* [cite_start]**Feature Insights**: Tokenized features consistently outperformed manual ones for supervised learning[cite: 205]. [cite_start]For manual features, **URL length** and the **ratio of non-alphanumeric characters** were the most predictive[cite: 199].
* [cite_start]**Conclusion**: Supervised classification using detailed, character-level patterns is a highly effective strategy for identifying malicious URLs [cite: 226][cite_start], significantly outperforming anomaly detection [cite: 212] [cite_start]and models based on simpler, manually-engineered features[cite: 205].
