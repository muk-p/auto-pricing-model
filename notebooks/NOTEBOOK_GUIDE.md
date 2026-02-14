# Notebook Structure Guide

This analysis has been broken down into 5 focused, manageable notebooks, each with a single primary purpose:

## 📋 Notebook Overview

### 1. **01_data_loading_cleaning.ipynb**
**Purpose**: Data preparation and cleaning
- Load raw insurance data from CSV
- Perform initial data exploration and validation
- Apply data cleaning rules (remove invalid records)
- Calculate core metrics (claim frequency)
- Create feature engineering groups (driver age, vehicle age)
- Save cleaned and processed dataset for downstream analysis

**Outputs**:
- `../data/processed/freMTPL2freq_processed.csv` - Cleaned dataset with engineered features

---

### 2. **02_exploratory_analysis.ipynb**
**Purpose**: Visual exploration and pattern discovery
- Load processed data
- Create frequency distribution visualizations (4 main charts)
- Generate advanced insights visualizations (vehicle power, regions, heatmaps)
- Identify key risk patterns and relationships
- Produce summary statistics by demographic groups

**Outputs**:
- `../results/01_EDA_Frequency_Distributions.png` - Main frequency distributions
- `../results/02_EDA_Key_Insights.png` - Advanced insights visualizations

---

### 3. **03_glm_modeling.ipynb**
**Purpose**: Statistical model development
- Load processed data
- Prepare features for GLM (create dummy variables for categorical features)
- Fit Poisson GLM with exposure offset
- Extract and display model coefficients and statistics
- Generate predictions on full dataset
- Calculate performance metrics vs baseline

**Outputs**:
- `../data/processed/predictions_output.csv` - Model predictions and residuals
- `../results/03_GLM_Model_Summary.txt` - Detailed model summary statistics

---

### 4. **04_model_evaluation.ipynb**
**Purpose**: Model diagnostics and performance assessment
- Load model predictions
- Perform comprehensive residual diagnostics
  - Residuals vs fitted values plot
  - Q-Q plot for normality
  - Distribution of residuals
  - Homoscedasticity assessment
- Conduct lift chart analysis for model ranking power
- Compare predictions vs actual frequencies
- Generate diagnostic summary statistics

**Outputs**:
- `../results/04_Lift_Analysis_Performance.png` - Lift curves and prediction scatter
- `../results/05_Model_Diagnostics_Residuals.png` - 4-panel diagnostic plots

---

### 5. **05_final_report.ipynb**
**Purpose**: Executive summary and business recommendations
- Load all analysis results and artifacts
- Generate comprehensive summary report
- Consolidate dataset statistics
- Display model performance metrics
- Summarize lift chart insights
- Provide actionable business recommendations
- List all generated output files

**Outputs**:
- Console output: Executive summary report

---

## 🔄 Recommended Execution Flow

```
01_data_loading_cleaning
        ↓
02_exploratory_analysis
        ↓
03_glm_modeling
        ↓
04_model_evaluation
        ↓
05_final_report
```

Each notebook depends on outputs from previous steps. Run them in sequential order.

## 📊 Key Variables Passed Between Notebooks

| Variable | Created | Used | Format |
|----------|---------|------|--------|
| `freMTPL2freq_processed.csv` | 01 | 02, 03, 04, 05 | CSV File |
| `predictions_output.csv` | 03 | 04, 05 | CSV File |
| `03_GLM_Model_Summary.txt` | 03 | 05 | Text File |
| Visualization PNGs | 02, 04 | Referenced in 05 | PNG Images |

## 🎯 Key Features of This Structure

✅ **Modularity** - Each notebook has a single, clear purpose
✅ **Reusability** - Notebooks can be re-run independently after initial setup
✅ **Clarity** - Easier to understand the role of each analysis step
✅ **Maintainability** - Focused notebooks are easier to debug and update
✅ **Documentation** - Clear section headers and print statements throughout
✅ **Reproducibility** - All outputs are saved to files for traceability

## 📁 File Structure

```
auto-pricing-model/
├── notebooks/
│   ├── 01_data_loading_cleaning.ipynb
│   ├── 02_exploratory_analysis.ipynb
│   ├── 03_glm_modeling.ipynb
│   ├── 04_model_evaluation.ipynb
│   ├── 05_final_report.ipynb
│   └── NOTEBOOK_GUIDE.md (this file)
├── data/
│   ├── raw/
│   │   └── freMTPL2freq.csv
│   └── processed/
│       ├── processed.csv
│       └── predictions_output.csv
└── results/
    ├── 01_EDA_Frequency_Distributions.png
    ├── 02_EDA_Key_Insights.png
    ├── 03_GLM_Model_Summary.txt
    ├── 04_Lift_Analysis_Performance.png
    └── 05_Model_Diagnostics_Residuals.png
```

## 💡 Usage Tips

- **Run sequentially**: Execute notebooks 01-05 in order
- **Data isolation**: Each notebook loads its own inputs, making them portable
- **Re-execution**: Can re-run individual notebooks if parameters change
- **Debugging**: Focused notebooks make errors easier to locate
- **Collaboration**: Different team members can work on different notebooks
