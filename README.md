# Diabetes Prediction Model Comparison

An academic machine learning comparison on a diabetes classification dataset. The notebook covers exploratory analysis, cleaning, a stratified train/validation/test split, preprocessing, optional PCA, model tuning, and evaluation on a held-out test set.

**Team:** Nour Waleed, Hagar Ali, Mohamed Sameh, Ahmed Khalid, and Abdelrahman Emad. The report in `docs/` is a copy of the team submission with student ID numbers removed for this public repository.

## Results recorded in the notebook

After removing 3,854 exact duplicate rows and 18 rows in the rare `Other` gender category, the notebook uses **96,128 rows**. The positive class represents **8.82%** of the cleaned dataset. The stratified split is **60% training, 20% validation, and 20% test**.

The final model is selected by **validation balanced accuracy**: XGBoost without PCA scored **0.9085** on validation. Its subsequent evaluation on the held-out test set reported:

| Test metric | Value |
| --- | ---: |
| Balanced accuracy | 0.8957 |
| Recall / sensitivity | 0.8662 |
| Precision | 0.5284 |
| F1 | 0.6564 |
| Accuracy | 0.9200 |

These are results saved in the supplied notebook. They have **not** been independently rerun here. The confusion matrix in that test output is `TN=16,219`, `FP=1,311`, `FN=227`, `TP=1,469`.

## Models and methods

The notebook compares logistic regression, multilayer perceptron, linear and RBF SVM, Gaussian Naive Bayes, random forest, gradient boosting, AdaBoost, and XGBoost. It explores PCA versus the full processed feature set and uses grid search or particle swarm optimization for selected models. Numeric features are scaled, categorical features are one-hot encoded, and the target imbalance is assessed using balanced accuracy, recall, precision, F1, and confusion matrices.

## Run locally

1. Obtain `diabetes_prediction_dataset.csv` from the [Diabetes Prediction Dataset on Kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset) and place it beside the notebook in the repository root. The dataset is not redistributed here; check the original publisher's usage terms.
2. Create a Python environment and install the dependencies:

   ```bash
   python -m venv .venv
   # Activate .venv for your operating system, then:
   pip install -r requirements.txt
   jupyter notebook diabetes_model_comparison.ipynb
   ```

Running every cell can take substantial time because the notebook searches several model grids and draws many plots. The notebook was originally saved with outputs so readers can inspect the reported experiments before rerunning it.

## Files

| File | Purpose |
| --- | --- |
| `diabetes_model_comparison.ipynb` | Complete team analysis and model experiments |
| `docs/Project-Report.docx` | Team report with student ID numbers removed |
| `requirements.txt` | Python dependencies |

**Scope:** This is a course project, not a validated clinical screening or diagnostic tool. Its performance on this dataset does not establish safety or accuracy for real patients. Removing the rare `Other` category also limits what the evaluation says about that group.
