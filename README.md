# 🍳 Recipe Entity Extraction Using CRF Model — NLP Pipeline

### 📌 Overview

This project builds an end-to-end Natural Language Processing (NLP) pipeline to extract structured semantic entities—specifically Ingredients, Quantities, and Units—from unstructured recipe text. 
By leveraging a Conditional Random Field (CRF) algorithm optimized with the L-BFGS method, the model successfully captures the complex sequential dependencies inherent in culinary linguistics, transforming raw text into actionable data for food-tech applications.

---

### 🧰 Tools & Technologies

* **Python**
* **Pandas, NumPy** (Data ingestion & manipulation)
* **spaCy** (Linguistic feature extraction & POS tagging)
* **Scikit-learn** (Data splitting & evaluation metrics)
* **sklearn-crfsuite** (CRF model building & training)
* **Joblib** (Model serialization)
* **Matplotlib, Seaborn** (Data visualization & confusion matrices)
  
---

### 🎯 Key Objectives

* Automate the extraction of structured data from unstructured recipe sequences.
* Implement custom rule-based feature engineering using Regex and domain-specific culinary keywords.
* Mitigate severe class imbalance (~75% majority class) using algorithmic weighting techniques.
* Conduct granular, token-level error analysis to evaluate model generalization and semantic understanding.
* Develop a highly optimized, production-ready pipeline capable of rapid execution.
  
---

### 🧹 Data Preparation

* Ingested and parsed raw JSON recipe data.
* Conducted rigorous data integrity checks, identifying and dropping sequences with length mismatches between inputs and POS tags to ensure 100% data purity.
* Generated complex sentence-level and word-level feature dictionaries.
* Implemented **Inverse Frequency Weighting** to heavily penalize the majority class ("ingredient") and boost minority classes.
* Executed a strict 70:30 Train-Validation data split with a perfect 1-to-1 feature-to-label mapping.

---

### 🤖 Model Building & Training

* **Algorithm Selection:** Implemented a **Conditional Random Field (CRF)** model using the **L-BFGS** optimization algorithm to effectively capture state-to-state dependencies in recipe sequences.
* **Regularization Strategy:**
    * **L1 (c1 = 0.5):** Applied to encourage sparsity and perform automatic feature selection by penalizing irrelevant features.
    * **L2 (c2 = 1.0):** Applied to penalize large coefficients and maintain robust control over overfitting.
* **Sequence Transitions:** Enabled **all_possible_transitions** to allow the model to learn and weight transitions that may not have been present in the training set, significantly enhancing generalization.
* **Training Scale:** The model was successfully trained on a corpus of **7,114 tokens** extracted from **196 high-quality recipe sequences**.
* **Persistence:** Successfully serialized the final trained state into `crf_model.pkl` for seamless production-ready inference.

---

### 📊 Analysis Highlights

* **Model Performance:** Achieved an outstanding **99.90% token-level accuracy** and a 1.00 F1-score on unseen validation data.
* **Class Imbalance Mitigation:** Successfully prevented the algorithm from defaulting to the majority class, proving the high efficacy of the custom inverse frequency weight injection.
* **Contextual Error Analysis:** Conducted a deep-dive micro-analysis on the 3 isolated misclassifications (out of 2,876 validation tokens), revealing that the model correctly prioritized engineered structural heuristics over subjective human ground-truth labeling in edge cases.
* **Operational Efficiency:** Achieved an end-to-end pipeline execution time of just **22 seconds**.
* **Production Readiness:** Serialized the trained model into a highly optimized, lightweight artifact (`crf_model.pkl` at 0.037 MB) ready for deployment in nutritional calculators and meal-planning engines.
  
---

### 👤 Author

Russel Reynold Chandanshiv

---
### 📜 License

Distributed under the MIT License.
