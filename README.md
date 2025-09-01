# Income Predictor

This project predicts whether an individual earns more than **$50k per year** based on census demographic and employment data. It uses the **UCI Adult Income dataset** and builds a **logistic regression classifier** in R, with steps for data cleaning, feature engineering, exploratory data analysis (EDA), and model evaluation.

---

## 📦 Requirements

- **R (≥ 4.0)**
- R packages:
  - `dplyr`
  - `ggplot2`
  - `Amelia` (for missing data visualization)

Install packages if needed:

```r
install.packages(c("dplyr", "ggplot2", "Amelia"))
```

---

## 📂 Dataset

- Place the CSV file (e.g., `adult_sal.csv`) in your working directory.
- Original file sometimes downloads as `adult_sal (1).csv` — rename for consistency.

---

## 🛠 Workflow

### 1. Setup & Data Import
- Set working directory
- Read the dataset into R
- Remove duplicate index column

### 2. Data Cleaning & Preprocessing
- **Factor reduction**:
  - Employer type:
    - `Never-worked` + `Without-pay` → `Unemployed`
    - `Self-emp-inc` + `Self-emp-not-inc` → `Self-emp`
    - `State-gov` + `Local-gov` → `SL-gov`
  - Marital status:
    - Reduced to `Married`, `Not-Married`, `Never-Married`
  - Country:
    - Grouped into continents (`Asia`, `North America`, `Europe`, `Latin and South America`, `Other`)
  - Education:
    - Grouped into `Below-HS`, `Associate`, or original categories
- Converted all character columns into factors
- Replaced `"?"` with `NA` and removed rows with missing data

### 3. Exploratory Data Analysis (EDA)
Created plots with **ggplot2** to visualize:
- Income vs. age (histogram & density)
- Hours worked per week
- Income distribution across:
  - Region
  - Employer type
  - Education levels

### 4. Model Building
- Train/test split (70/30)
- Logistic regression (`glm` with `binomial(logit)`)
- Used `step()` to remove non-significant predictors

### 5. Model Evaluation
- Predictions made on test set
- Confusion matrix generated
- Metrics computed:
  - **Accuracy**
  - **Precision**
  - **Recall**
  - **F1 score**

---

## 📊 Example Results

From one run (your results may vary):

- **Accuracy:** ~84.8%  
- **Recall:** ~92.7%  
- **Precision:** ~87.8%  
- **F1 Score:** ~90.2%  

---

## ✅ Notes

- The dataset is slightly imbalanced toward `<=50K`, so ROC/PR analysis or resampling may improve results.
- Stepwise regression (`step()`) is heuristic; for more robust results, consider regularization (`glmnet`) or tree-based methods.
- Visualizations show expected trends (higher education and certain job types correlate with higher income).

---

## 📌 How to Run

1. Clone/download this repo  
2. Open R/RStudio in project directory  
3. Run the code chunks in order (or source the script)  
4. View plots and metrics  

---  
