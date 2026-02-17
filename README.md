# Healthcare Provider Fraud Detection - Project Structure

## Overview
This project is organized into specialized Jupyter notebooks, each focusing on a specific phase of the machine learning pipeline. This modular approach makes the project easier to understand, maintain, and update.

---

## 📁 Project Organization

### **Notebook 1: Data Loading and Exploration**
**File:** `01_Data_Loading_and_Exploration.ipynb`

**Purpose:** Initial data inspection and understanding
- Load all datasets (Beneficiary, Inpatient, Outpatient)
- Display dataset shapes and basic information
- Identify and report missing values
- Remove duplicate records
- Generate data quality summary statistics

**Key Outputs:**
- Cleaned datasets with duplicates removed
- Missing value reports per dataset
- Data dimension summary

---

### **Notebook 2: Data Visualization**
**File:** `02_Data_Visualization.ipynb`

**Purpose:** Visual exploration and pattern discovery
- Visualize missing data patterns (heatmaps, bar charts)
- Explore target variable distribution
- Analyze numerical feature distributions (histograms, box plots)
- Examine categorical features
- Create correlation matrices
- Generate summary statistics visualizations

**Key Outputs:**
- Missing value visualizations
- Feature distributions
- Correlation analysis
- Summary statistics

---

### **Notebook 3: Feature Engineering and Cleaning**
**File:** `03_Feature_Engineering_and_Cleaning.ipynb`

**Purpose:** Data preparation for machine learning
- Handle missing values (mean/median imputation)
- Engineer features from Inpatient data:
  - Claim counts
  - Total costs and deductibles
  - Average claim amounts
- Engineer features from Outpatient data:
  - Similar aggregations as inpatient
- Create Beneficiary-level features:
  - Age calculations
  - Financial ratios
  - Coverage metrics
- Aggregate all features into unified datasets
- Apply feature scaling (StandardScaler)
- Save processed datasets

**Key Outputs:**
- `X_train_processed.csv` - Training features
- `X_test_processed.csv` - Test features
- `y_train.csv` - Training labels
- Scaled and aggregated data ready for modeling

---

### **Notebook 4: Model Training and Evaluation**
**File:** `04_Model_Training_and_Evaluation.ipynb`

**Purpose:** Build and evaluate machine learning models
- Split data into train/validation sets
- Train multiple models:
  - Logistic Regression
  - Random Forest
  - Gradient Boosting
  - XGBoost
- Compare model performance:
  - Accuracy, Precision, Recall, F1-Score
  - ROC-AUC scores
- Evaluate best model:
  - Confusion matrix
  - ROC curve
  - Precision-recall curve
- Analyze feature importance
- Generate final test predictions

**Key Outputs:**
- Model performance comparison table
- Evaluation plots (ROC, PR, confusion matrix)
- Feature importance analysis
- `fraud_detection_predictions.csv` - Final predictions on test set

**Performance Metrics:**
- Accuracy: Overall correctness
- Precision: True fraud detection rate among predicted fraud cases
- Recall: Percentage of actual fraud cases detected
- F1-Score: Balanced precision-recall metric
- ROC-AUC: Model discrimination ability

---

### **Notebook 5: Exploratory Data Analysis and Insights**
**File:** `05_EDA_and_Insights.ipynb`

**Purpose:** Deep analysis and business insights
- Analyze fraud patterns and characteristics
- Compare fraud vs non-fraud statistics
- Feature comparison by fraud status
- Beneficiary analysis (age, chronic conditions)
- Claims analysis (inpatient vs outpatient patterns)
- Financial analysis (reimbursement patterns)
- Generate key findings and recommendations

**Key Outputs:**
- Fraud pattern visualizations
- Feature importance for fraud detection
- Statistical comparisons
- Business insights and recommendations

---

## 🔄 Workflow and Dependencies

```
01_Data_Loading
    ↓
02_Data_Visualization
    ↓
03_Feature_Engineering → Outputs: X_train, X_test, y_train
    ↓
04_Model_Training → Uses processed data
    ↓ → Outputs: predictions, model metrics
05_EDA_and_Insights → Analyzes original data for insights
```

**Data Files Used:**
- `Train_Beneficiarydata-1542865627584.csv` - Training beneficiary data
- `Train_Inpatientdata-1542865627584.csv` - Training inpatient claims
- `Train_Outpatientdata-1542865627584.csv` - Training outpatient claims
- `Train-1542865627584.csv` - Training labels
- `Test_Beneficiarydata-1542969243754.csv` - Test beneficiary data
- `Test_Inpatientdata-1542969243754.csv` - Test inpatient claims
- `Test_Outpatientdata-1542969243754.csv` - Test outpatient claims
- `Test-1542969243754.csv` - Test IDs

---

## 📊 Key Features

### Beneficiary Features
- Age (calculated from DOB)
- Chronic disease indicators
- Coverage months
- Financial reimbursement/deductible amounts

### Inpatient Features
- Claims count
- Total claim costs
- Total deductible amounts
- Average claim amounts

### Outpatient Features
- Claims count
- Total claim costs
- Total deductible amounts
- Average claim amounts

### Derived Features
- Financial ratios (reimbursement to coverage)
- IP to OP ratios
- Total healthcare costs

---

## 🎯 Model Performance

The notebook trains multiple models and compares their performance:
- **Logistic Regression** - Baseline
- **Random Forest** - Ensemble method
- **Gradient Boosting** - Sequential boosting
- **XGBoost** - Optimized gradient boosting

Best model typically selected based on:
1. ROC-AUC score (discrimination ability)
2. F1-Score (balance between precision and recall)
3. Recall (fraud detection rate - business critical)

---

## 📈 Output Files

### Processing Outputs
- `X_train_processed.csv` - Processed training features (scaled)
- `X_test_processed.csv` - Processed test features (scaled)
- `y_train.csv` - Training labels

### Model Outputs
- `fraud_detection_predictions.csv` - Final predictions with probabilities
  - Columns: BeneID, PotentialFraud, FraudProbability

---

## 🚀 How to Use

1. **Start with Notebook 1**: Run data loading to understand dataset structure
2. **Then Notebook 2**: Visualize data patterns and distributions
3. **Then Notebook 3**: Execute feature engineering and data preparation
4. **Then Notebook 4**: Train and evaluate models
5. **Finally Notebook 5**: Analyze insights and patterns

Alternatively, run them sequentially to get the complete pipeline flow.

---

## 💡 Key Insights

- **Class Imbalance**: Non-fraud cases vastly outnumber fraud cases (requires special handling)
- **Feature Importance**: Financial features and claim patterns are strong fraud indicators
- **Model Choice**: Ensemble methods (XGBoost/Random Forest) typically outperform linear models
- **Threshold Tuning**: Adjust prediction threshold based on business requirements (precision vs recall trade-off)

---

## 🔧 Requirements

```python
pandas
numpy
scikit-learn
xgboost
matplotlib
seaborn
```

---

## 📝 Notes

- All notebooks use stratified splitting to maintain class balance in train/validation splits
- StandardScaler is applied to numerical features before modeling
- Missing values are handled with mean imputation for numerical and 'Unknown' for categorical
- Feature importance is calculated from the best performing model
- Final predictions include both classification and probability scores

---

## 📞 Support

For questions about specific notebooks or steps, refer to the markdown sections and code comments within each notebook.
