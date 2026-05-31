# Data Preprocessing

This directory contains the notebooks and intermediate datasets used to prepare the CIC-DDoS2019 data for model training and evaluation.

## Directory Structure

```text
Data_Preprocessing/
│
├── EDA.ipynb
├── Preprocessed.ipynb
│
├── cleaned_data/
├── imbalanced_data/
└── preprocessed_data/
```

## Notebooks

### 1. EDA.ipynb

This notebook performs the initial exploratory data analysis (EDA) and data cleaning process.

The main tasks include:

* Loading the selected CIC-DDoS2019 attack datasets.
* Inspecting class distributions.
* Detecting missing and infinite values.
* Removing invalid observations.
* Removing non-informative and constant features.
* Verifying label consistency.
* Analyzing feature distributions and correlations.

The output of this notebook is the **`cleaned_data/`** directory, which contains the cleaned versions of the four selected datasets stored as separate CSV files.

---

### 2. Preprocessed.ipynb

This notebook performs dataset integration, splitting, and preparation for machine learning experiments.

The notebook generates two different dataset configurations:

#### Imbalanced Configuration

The original class distribution is preserved.

The four cleaned datasets are combined into a single binary classification dataset where:

* `0 = BENIGN`
* `1 = ATTACK`

The combined dataset is then stratified and divided into:

* Training set
* Validation set
* Test set

The resulting files are stored in the **`imbalanced_data/`** directory.

---

#### Balanced Configuration

After the train/validation/test split is completed, random undersampling is applied exclusively to the training and validation subsets.

This process balances the number of benign and attack samples while preserving the original class distribution of the test set.

The resulting files are stored in the **`preprocessed_data/`** directory and include:

* `train.csv`
* `val.csv`
* `test.csv`

The test set remains unchanged to ensure evaluation under realistic network traffic conditions.

---

## Generated Directories

### cleaned_data/

Contains the cleaned versions of the four selected CIC-DDoS2019 attack datasets after EDA and preprocessing.

### imbalanced_data/

Contains the combined dataset split into training, validation, and testing subsets while preserving the original class distribution.

### preprocessed_data/

Contains the balanced training and validation subsets generated through random undersampling, together with the original imbalanced test set used for model evaluation.

```
```
