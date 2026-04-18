# Predictive Modeling of Antibody Thermostability

## Overview

This project explores the prediction of monoclonal antibody (mAb) thermostability using machine learning models trained on amino acid sequences. Specifically, it investigates how well different feature representations and model architectures can predict melting temperature (**Tm**), a critical metric for antibody developability.

Thermal stability is a major factor in antibody manufacturing and storage. Poor stability can lead to aggregation and failure in later development stages. This project aims to identify computational approaches that enable accurate early-stage screening of antibody candidates.

---

## Objectives

* Predict antibody melting temperature (**Tm**) from amino acid sequences
* Compare multiple feature extraction techniques
* Evaluate and rank machine learning models based on performance
* Identify the most informative representation for antibody stability

---

## Dataset

* **Source:** Ginkgo GDPa1 dataset
* **Content:** Paired antibody sequences:

  * Variable Heavy Chain (**VH**)
  * Variable Light Chain (**VL**)
* **Target Variable:** Melting temperature (**Tm**) measured via nanoDSF

---

## Methodology

### 1. Data Preprocessing

* Removed missing and duplicate sequences
* Performed statistical analysis on Tm values
* Applied **Interquartile Range (IQR)** method for outlier removal

---

### 2. Feature Engineering

#### A. Physicochemical Features

Computed using peptide analysis tools:

* Molecular weight
* Isoelectric point (pI)
* Hydrophobicity (Kyte-Doolittle scale)
* Aliphatic index
* Amino acid composition and ratios
* Charge, polarity, and residue group distributions

These features provide a coarse-grained summary of protein properties.

---

#### B. Protein Language Model Embeddings

**ProtT5-XL-U50**

* Captures sequence “grammar”
* High-dimensional embeddings
* Limited structural awareness

**ESM-2 (150M parameters)**

* Captures evolutionary and structural information
* Trained on UniRef50 dataset
* Strong performance for protein folding and stability tasks

**AntiBERTy**

* Antibody-specific language model
* Extremely high dimensional (~126k features)
* Not used in final models due to computational constraints

---

### 3. Models Evaluated

#### Tree-Based Models

* Random Forest
* Extra Trees
* XGBoost

#### Linear Models

* Ridge Regression
* Lasso Regression
* ElasticNet

#### Distance-Based Models

* Support Vector Regression (SVR)
* K-Nearest Neighbors (KNN)

#### Neural Network

* Dense layers with:

  * Batch Normalization
  * Dropout

---

### 4. Evaluation Metrics

* **R² Score** (primary metric)

* Mean Absolute Error (MAE)

* Root Mean Squared Error (RMSE)

* Cross-validation used for model selection

* Final evaluation performed on a held-out test set

---

## Results

| Feature Type      | Best Model    | Performance (R²) |
| ----------------- | ------------- | ---------------- |
| Physicochemical   | XGBoost       | ~0.06            |
| ProtT5 Embeddings | Random Forest | Low correlation  |
| ESM-2 Embeddings  | Lasso         | ~0.999           |

### Key Findings

* Physicochemical features alone are insufficient to predict Tm
* ProtT5 embeddings did not capture relevant structural signals
* **ESM-2 embeddings achieved near-perfect predictions**

---

## Interpretation

The dramatic improvement using ESM-2 suggests that:

* Antibody thermostability depends on **complex residue interactions**, not just bulk properties
* Evolutionary and structural patterns are critical
* Transformer-based protein models capture these relationships effectively

---

## Limitations

* AntiBERTy embeddings were too large for efficient modeling
* Risk of overfitting with extremely high R² values
* Limited dataset size may affect generalizability

---

## Future Work

* Apply **Principal Component Analysis (PCA)** for dimensionality reduction
* Re-evaluate AntiBERTy embeddings after compression
* Expand dataset for better generalization
* Explore deep learning architectures (e.g., CNNs, transformers)
* Validate results on external antibody datasets

---

## Conclusion

This study demonstrates a clear shift in antibody developability assessment:

* Traditional physicochemical descriptors are insufficient
* Protein language models significantly improve predictive performance
* **ESM-2 embeddings provide a powerful, scalable solution** for early-stage antibody screening

This approach can reduce reliance on experimental testing and help minimize late-stage drug development failures.

---

## Technologies Used

* Python
* Scikit-learn
* TensorFlow
* XGBoost
* Protein Language Models (ProtT5, ESM-2, AntiBERTy)

---

## Author

Janet Bonareri

