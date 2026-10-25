# Titanic Survival Prediction using Machine Learning

## Project objective

This beginner-friendly classification project explores the provided Titanic passenger dataset and compares Logistic Regression, Random Forest, and Gradient Boosting models for predicting `Survived`. It uses a stratified holdout set and cross-validation on the training set, and generates a model comparison CSV, visualizations, and a PDF report from actual notebook execution.

The supplied CSV has 891 rows and 12 columns. It contains the expected binary `Survived` target (602 not-survived and 289 survived), 177 missing `Age` values, 664 missing `Cabin` values, and no exact duplicate rows. The notebook performs additional checks rather than assuming these observations will always hold.

## Project structure

```text
Titanic_ML_Project/
├── titanic.csv                         # Original input data; never modified
├── titanic_survival_prediction.ipynb   # Complete analysis, training, evaluation, and report
├── requirements.txt                    # Python dependencies
├── README.md                           # This guide
├── model_comparison.csv                # Generated evaluation results
├── summary_report.pdf                  # Generated project report
└── outputs/                            # Generated plots
```

`model_comparison.csv`, `summary_report.pdf`, and `outputs/` are generated when the notebook is run. The CSV dataset is only read.

## Python setup

Use Python 3.10 or newer. From a terminal opened in this project folder, create and activate a virtual environment, then install the dependencies:

```powershell
py -3 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

If PowerShell blocks activation, either allow activation for the current user or run the environment's Python directly:

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

In VS Code, select the `.venv` Python interpreter and install/select its Jupyter kernel if prompted.

## Run the project

1. Open `titanic_survival_prediction.ipynb` in VS Code.
2. Confirm the notebook kernel uses the environment above.
3. Ensure `titanic.csv` remains in this folder.
4. Choose **Run All**. The notebook reads the CSV, performs checks and analysis, fits and evaluates all three models, and writes the generated deliverables.
5. Review `model_comparison.csv`, `summary_report.pdf`, and the plots in `outputs/`.

Alternatively, run the notebook from this folder in a terminal:

```powershell
python -m jupyter nbconvert --to notebook --execute titanic_survival_prediction.ipynb --inplace
```

The notebook selects a model using mean five-fold cross-validation F1 score (ROC-AUC breaks ties); test-set scores are reported as the held-out evaluation, not used to select the model.

## Notes on interpretation

The notebook excludes passenger identifiers, names, ticket labels, and the mostly-missing cabin field from predictors. Imputation, one-hot encoding, scaling, and zero-variance filtering are fit inside each training fold/model pipeline. IQR outliers are reported, not automatically removed, because unusual ages or family sizes can be valid passenger observations. Model scores describe this supplied dataset and split; they are not a guarantee of real-world performance.
