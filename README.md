# Machine Learning-Based Solar Power Generation Forecasting

A college engineering project forecasting solar power generation using machine learning regression techniques.
Three team members each work on one dedicated real-world solar dataset with three regression algorithms.

---

## 📌 Project Overview

Solar energy is an intermittent and weather-dependent renewable energy source. Accurately predicting the power output of solar photovoltaic (PV) systems is crucial for grid stability, energy trading, and operational planning.

In this project, we conduct a structured empirical study:
- **3 Datasets**: Each team member has one dedicated solar dataset (`member1`, `member2`, `member3`).
- **3 Algorithms per Member**: Each member trains and evaluates 3 regression models on their dataset.
- **9 Total Experiments**: 3 members × 3 models = 9 model–dataset experiments.

### Team Division

| Member | Dataset | Assigned Models |
| :--- | :--- | :--- |
| **Member 1** | Dataset 1 — Plant 1 (`AC_POWER`, kW, 15-min) | Linear Regression · Decision Tree Regressor · Random Forest Regressor |
| **Member 2** | Dataset 2 — PV_Data (`Total PV Power`, W, Hourly) | Gradient Boosting Regressor · XGBoost Regressor · Support Vector Regression (SVR) |
| **Member 3** | Dataset 3 — PV_secondRelease (`Generated power`, W, 5-min) | K-Nearest Neighbors · Ridge Regression · Extra Trees Regressor |

---

## 📁 Directory Structure

```text
Solar-Power-Forecasting/
│
├── data/                       # Contains all raw and processed dataset files
│   ├── member1/                # Dataset 1 — Plant 1 solar generation data
│   ├── member2/                # Dataset 2 — PV_Data rooftop PV data
│   └── member3/                # Dataset 3 — PV_secondRelease high-frequency data
│
├── src/                        # Python source code
│   ├── __init__.py             # Marks 'src' as a Python package
│   ├── config.py               # Central configuration file for paths and parameters
│   ├── preprocess.py           # Data loading and preprocessing pipelines
│   ├── train.py                # Full 27-experiment training pipeline (all models x all datasets)
│   ├── generate_team_results.py # Filters results to 9 team-division experiments,
│   │                           #   regenerates tables, graphs, and reports
│   ├── evaluate.py             # Original evaluation suite (27-experiment scope)
│   └── app.py                  # Streamlit dashboard
│
├── models/                     # Saved trained model files (.joblib)
│
├── results/                    # All experimental outputs and deliverables
│   ├── graphs/                 # High-resolution comparison charts (PNG)
│   ├── tables/                 # Performance metric tables (CSV)
│   │   ├── experiment_results.csv          # All 27 experiments (preserved)
│   │   ├── team_division_results.csv       # 9 team-assigned experiments
│   │   ├── member1_model_comparison.csv    # Member 1's 3 models ranked
│   │   ├── member2_model_comparison.csv    # Member 2's 3 models ranked
│   │   └── member3_model_comparison.csv    # Member 3's 3 models ranked
│   └── predictions/            # Exported CSVs of predicted solar power values
│
├── .gitignore                  # Tells Git which files to ignore
├── requirements.txt            # Required Python libraries
└── README.md                   # Project documentation
```

---

## 🔍 Folder and File Descriptions

| Folder / File | What it is | Why it is used |
| :--- | :--- | :--- |
| `data/member1/` | Folder for Dataset #1 | Stores the first team member's solar dataset. |
| `data/member2/` | Folder for Dataset #2 | Stores the second team member's solar dataset. |
| `data/member3/` | Folder for Dataset #3 | Stores the third team member's solar dataset. |
| `src/` | Source Code Folder | Houses all Python scripts (data loading, preprocessing, model definitions, evaluation). |
| `src/config.py` | Configuration Script | Keeps all file paths and experiment settings in one place so scripts never have broken links. |
| `models/` | Trained Models Folder | Stores the finalized machine learning models as binary files (e.g., `.joblib`) so they can be reloaded without retraining. |
| `results/graphs/` | Visual Results | Stores all generated charts (actual vs. predicted line plots, error distributions, bar charts). |
| `results/tables/` | Summary Tables | Stores comparison sheets (CSV/Excel) summarizing MAE, MSE, RMSE, and $R^2$ across all 27 experiments. |
| `results/predictions/` | Output Values | Stores forecasted generation numbers side-by-side with ground-truth test data. |
| `requirements.txt` | Dependency List | Lists all external Python libraries needed to run the project. |
| `README.md` | Guide Book | Provides full documentation and instructions for team members and project evaluators. |

---

## 📊 The 9 Team-Division Experiments

### Member 1 — Dataset 1 (Plant 1, `AC_POWER`)

| # | Algorithm | Description |
| :---: | :--- | :--- |
| 1 | **Linear Regression** | Ordinary least squares — linear baseline. |
| 2 | **Decision Tree Regressor** | Non-linear single tree splitting on weather thresholds. |
| 3 | **Random Forest Regressor** | Bagging ensemble of 100 trees averaging predictions. |

### Member 2 — Dataset 2 (PV_Data, `Total PV Power`)

| # | Algorithm | Description |
| :---: | :--- | :--- |
| 4 | **Gradient Boosting Regressor** | Sequential boosting correcting previous tree residuals. |
| 5 | **XGBoost Regressor** | Optimized gradient boosting with L1/L2 regularization. |
| 6 | **Support Vector Regression (SVR)** | Kernel-based margin regressor in transformed feature space. |

### Member 3 — Dataset 3 (PV_secondRelease, `Generated power`)

| # | Algorithm | Description |
| :---: | :--- | :--- |
| 7 | **K-Nearest Neighbors Regressor** | Instance-based regressor using nearest weather-state clusters. |
| 8 | **Ridge Regression** | L2-regularized linear model penalizing large weights. |
| 9 | **Extra Trees Regressor** | Extremely randomized trees — variance-reducing regularizer. |

Each model is evaluated using 4 standard metrics:
1. **MAE** (Mean Absolute Error)
2. **MSE** (Mean Squared Error)
3. **RMSE** (Root Mean Squared Error — in native physical units)
4. **R² Score** (Coefficient of Determination, 1.0 = perfect fit)

---

## 📥 Where to Place Your CSV Datasets

When you have your 3 CSV files ready, place them in the following paths:

1. **Dataset 1** &rarr; `d:\Antigravity IDE\Solar-Power-Forecasting\data\member1\`
2. **Dataset 2** &rarr; `d:\Antigravity IDE\Solar-Power-Forecasting\data\member2\`
3. **Dataset 3** &rarr; `d:\Antigravity IDE\Solar-Power-Forecasting\data\member3\`

> ⚠️ **Safety Rule**: Keep your original CSV files saved safely in a personal backup folder (e.g. `Downloads`, `Documents`, or Google Drive). Never modify your raw original files directly. The Python scripts will load the files in read-only mode and create cleaned copies if preprocessing is needed.

---

## 🚀 Getting Started (Step-by-Step for Windows)

### 1. Create a Python Virtual Environment (Recommended)
Open PowerShell in the project directory (`d:\Antigravity IDE\Solar-Power-Forecasting`) and run:
```powershell
# Using the installed Python interpreter
D:\python.exe -m venv venv
```

### 2. Activate the Virtual Environment
```powershell
.\venv\Scripts\Activate.ps1
```
*(If PowerShell shows a script execution error, run: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`)*

### 3. Install Required Packages
```powershell
pip install -r requirements.txt
```

### 4. Generate Team Division Results & Graphs
After training has been run at least once (`src/train.py`), generate the 9-experiment team-division
tables, graphs, and reports:
```powershell
D:\python.exe src/generate_team_results.py
```
This regenerates:
- `results/tables/member{1,2,3}_model_comparison.csv` — 3-model ranked tables
- `results/tables/team_division_results.csv` — 9-row master table
- `results/graphs/member{1,2,3}_rmse_comparison.png` — RMSE bar charts
- `results/graphs/all_datasets_r2_comparison.png` — R² comparison
- `results/graphs/actual_vs_predicted_best_models.png` — time-series curves
- `results/experiment_results.md` and `results/final_evaluation_report.md`

### 5. Launch the Dashboard
```powershell
D:\python.exe -m streamlit run src/app.py
```
