### Malicious URL Detection Project Summary

In this project, I developed and evaluated machine learning models to detect malicious URLs. The goal was to differentiate between benign URLs and those used for phishing, malware, and defacement.

***

### Methods & Models

* **Feature Engineering**: I tested two approaches: (1) manually extracting structural features like URL length and character ratios, and (2) using a Bag-of-Words model with character-level 2-grams and 3-grams.
* **Models**: I compared several models, including **Logistic Regression**, **Linear SVM**, **Random Forest**, and **XGBoost** for supervised classification, alongside a **One-Class SVM** for anomaly detection.

***

### Results & Conclusion

* **Best Performance**: The supervised models trained with **tokenized n-gram features** were the most effective. Linear SVM achieved an accuracy of 0.99 and an F1-score of 0.99.
* **Results**: Tokenized features consistently outperformed manual ones for supervised learning. For manual features, **URL length** and the **ratio of non-alphanumeric characters** were the most predictive.
* **Conclusion**: Supervised classification using n-grams tokenization is  highly effective for identifying malicious URLs, significantly outperforming anomaly detection and models based on simpler, manually-engineered features.
