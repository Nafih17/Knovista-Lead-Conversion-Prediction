# Lead Conversion Prediction Using Machine Learning

An individual machine learning project that analyses historical lead-management data and builds classification models to estimate the probability of lead conversion.

## Project overview

Businesses receive leads from different sources and campaigns. This project explores lead data, examines conversion patterns, and trains machine learning classifiers to estimate whether a lead will convert.

**Project type:** Individual project  
**Domain:** Machine Learning / Sales Analytics  
**Development environment:** Google Colab  
**Language:** Python

## Repository contents

```text
Knovista-Lead-Conversion-Prediction/
├── README.md
├── Knovista_project.ipynb
├── Knovista.pptx
├── requirements.txt
├── .gitignore
└── images/
    └── README.md
```

## Dataset

The project was developed using a company-provided lead-management dataset.

| Dataset characteristic | Value |
|---|---:|
| Records | 22,030 |
| Attributes | 15 |
| Converted leads | 314 |
| Non-converted leads | 21,716 |
| Duplicate rows detected | 0 |
| Overall conversion rate | 1.43% |

The original dataset contains personal and company information. **The raw dataset is intentionally not included in this public repository.** Do not upload the original CSV, customer names, phone numbers, email addresses, or other confidential company information. Only use or publish data if you have explicit permission from the data owner.

## Workflow

1. Load and inspect the lead dataset.
2. Check missing values and duplicate records.
3. Create a binary target from `lead_stage`:
   - `1` = Converted
   - `0` = Not converted
4. Parse the lead creation date and derive month, day of week, and hour.
5. Explore lead-stage distribution, source-level conversion, and campaign-level conversion.
6. Select input features.
7. Split the data into training and testing sets using an 80:20 split with stratification.
8. Apply preprocessing through a Scikit-learn `ColumnTransformer` and `Pipeline`.
9. Train Logistic Regression and Random Forest classifiers.
10. Generate a conversion probability for a sample lead.

## Features used

- `campaign_name`
- `source_type`
- `source_name`
- `assigned_to`
- `month`
- `day_of_week`
- `hour`

## Preprocessing

- `SimpleImputer` with most-frequent strategy for categorical features.
- `OneHotEncoder` for categorical features.
- `SimpleImputer` with median strategy for numerical features.
- `StandardScaler` for numerical features.
- `ColumnTransformer` and `Pipeline` to combine preprocessing and model training.

## Models

### Logistic Regression
A binary classification model trained with class weighting to account for the imbalanced target classes.

### Random Forest Classifier
An ensemble classifier configured with 300 trees, `min_samples_leaf=5`, `class_weight='balanced_subsample'`, and `random_state=42`.

## Exploratory findings

- Instagram contributed 14,051 leads and 256 conversions.
- Facebook Ads contributed 1,049 leads and 23 conversions.
- Walk-in leads showed a 4.76% observed conversion rate (1 conversion from 21 leads). This is a small sample and should be interpreted cautiously.

## Model evaluation status

The current notebook trains both classifiers and demonstrates a sample Random Forest probability prediction. It does **not yet calculate or report final test-set evaluation metrics** such as precision, recall, F1-score, confusion matrix, ROC-AUC, or PR-AUC. No model accuracy or best-model claim is made in this repository.

The sample prediction probability shown in the original project presentation is an individual prediction, not a model performance metric.

## How to run

1. Open `Knovista_project.ipynb` in Google Colab.
2. Obtain the company dataset only through an authorised source.
3. Upload the authorised CSV file to the Colab session with the filename `Unified_Leads.csv`.
4. Run the notebook cells from top to bottom.

The notebook expects the CSV at:

```python
/content/Unified_Leads.csv
```

## Requirements

Install the dependencies with:

```bash
pip install -r requirements.txt
```

## Limitations and future work

- The target classes are highly imbalanced.
- Test-set evaluation and threshold selection remain to be completed.
- The current sample prediction uses a 50% probability threshold.
- Future work can include model evaluation, hyperparameter tuning, explainability, and an interactive prediction application.

## Presentation

`Knovista.pptx` contains the project presentation.

## Privacy note

This repository contains a cleaned notebook with saved cell outputs removed. The sample campaign and assigned-executive values have been replaced with generic placeholders. Confirm that the notebook and presentation contain no other confidential information before making the repository public.
