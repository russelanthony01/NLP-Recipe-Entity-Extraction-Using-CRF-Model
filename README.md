# 🍳 Recipe Entity Extraction Using CRF Model — NLP Pipeline

### 📌 Overview

This project builds an end-to-end Natural Language Processing (NLP) pipeline to extract structured semantic entities—specifically Ingredients, Quantities, and Units—from unstructured recipe text. 
By leveraging a Conditional Random Field (CRF) algorithm optimized with the L-BFGS method, the model successfully captures the complex sequential dependencies inherent in culinary linguistics, transforming raw text into actionable data for food-tech applications.

### 🧰 Tools & Technologies

* **Python**
* **Pandas, NumPy** (Data ingestion & manipulation)
* **spaCy** (Linguistic feature extraction & POS tagging)
* **sklearn-crfsuite** (CRF model building & training)
* **Joblib** (Model serialization)
* **Matplotlib, Seaborn** (Data visualization & confusion matrices)

### 🎯 Key Objectives

* Automate the extraction of structured data from unstructured recipe sequences.
* Implement custom rule-based feature engineering using Regex and domain-specific culinary keywords.
* Mitigate severe class imbalance (~75% majority class) using algorithmic weighting techniques.
* Conduct granular, token-level error analysis to evaluate model generalization and semantic understanding.
* Develop a highly optimized, production-ready pipeline capable of rapid execution.

### 🧹 Data Preparation

* Ingested and parsed raw JSON recipe data.
* Conducted rigorous data integrity checks, identifying and dropping sequences with length mismatches between inputs and POS tags to ensure 100% data purity.
* Generated complex sentence-level and word-level feature dictionaries.
* Implemented **Inverse Frequency Weighting** to heavily penalize the majority class ("ingredient") and boost minority classes.
* Executed a strict 70:30 Train-Validation data split with a perfect 1-to-1 feature-to-label mapping.

### 📊 Analysis Highlights

* **Model Performance:** Achieved an outstanding **99.90% token-level accuracy** and a 1.00 F1-score on unseen validation data.
* **Class Imbalance Mitigation:** Successfully prevented the algorithm from defaulting to the majority class, proving the high efficacy of the custom inverse frequency weight injection.
* **Contextual Error Analysis:** Conducted a deep-dive micro-analysis on the 3 isolated misclassifications (out of 2,876 validation tokens), revealing that the model correctly prioritized engineered structural heuristics over subjective human ground-truth labeling in edge cases.
* **Operational Efficiency:** Achieved an end-to-end pipeline execution time of just **24 seconds**.
* **Production Readiness:** Serialized the trained model into a highly optimized, lightweight artifact (`crf_model.pkl` at 0.037 MB) ready for deployment in nutritional calculators and meal-planning engines.

### 👤 Author

Russel Anthony Reynold Chandanshiv

### 📜 License

Distributed under the MIT License.
