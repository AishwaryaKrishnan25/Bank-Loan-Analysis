# 📌 Loan Approval Analysis

A data analytics project that analyzes historical loan application data to uncover approval patterns, risk factors, and trends. This project uses Python libraries for data preprocessing, visualization, and rule-based loan approval analysis without machine learning.

## 🚀 Features
- Data cleaning and preprocessing (handling missing values & duplicates)
- Exploratory Data Analysis (EDA) with visualization
- Rule-based loan approval logic (credit score, income, DTI ratio)
- Risk segmentation (low, medium, high)
- Statistical reports and insights for financial institutions
- No machine learning used – purely data-driven rules

## 🛠️ Tech Stack
- **Programming Language:** Python 3.10+
- **Libraries:**
  - Pandas
  - NumPy
  - Matplotlib
  - Seaborn
- **Tools:** Jupyter Notebook
- **Data Format:** CSV

## 📊 Key Insights
- High credit score (670+) and stable income → higher approval rate.
- Education loans have high rejection/default rates (~70% for poor credit).
- Debt consolidation loans carry the highest interest rates.
- Mortgage owners are lower-risk borrowers.
- Previous defaults and short credit histories are strong risk indicators.

## ⚙️ Installation
1. Clone the repository:
```
git clone https://github.com/your-username/loan-approval-analysis.git
cd loan-approval-analysis
```

2. Install dependencies:
```
pip install -r requirements.txt
```
3. Open Jupyter Notebook:
``` 
jupyter notebook
 ```


## 🛠️ Example Code

### 1️⃣ Data Preprocessing
```python
import pandas as pd

# Load dataset
data = pd.read_csv("data/loan_data.csv")

# Check missing values and duplicates
print(data.isna().sum())
print(f"Duplicate rows: {data.duplicated().sum()}")

# Handle missing values
data.fillna(method="ffill", inplace=True)

# Remove duplicates
data.drop_duplicates(inplace=True)
```

### 2️⃣ Exploratory Data Analysis (EDA)
```Python
import matplotlib.pyplot as plt
import seaborn as sns

# Age distribution
plt.figure(figsize=(8, 4))
sns.histplot(data['person_age'], bins=20, kde=True)
plt.title('Age Distribution')
plt.show()

# Loan Approval Status
plt.figure(figsize=(6, 4))
data['loan_status'].value_counts().plot(kind='bar', color=['green', 'red'])
plt.title('Loan Approval Status')
plt.xlabel('Status')
plt.ylabel('Count')
plt.show()

# Correlation Heatmap
plt.figure(figsize=(10, 6))
sns.heatmap(data.corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()
```

### 3️⃣ Rule-Based Loan Approval
```python
def loan_approval(row):
    if row['credit_score'] > 700 and row['debt_to_income'] < 0.4:
        return "Approved"
    elif row['credit_score'] < 600 or row['debt_to_income'] > 0.6:
        return "Rejected"
    else:
        return "Manual Review"

data['loan_status'] = data.apply(loan_approval, axis=1)
print(data['loan_status'].value_counts())
```

## 📈 Future Enhancements
- Real-time data integration
- Advanced statistical scoring (logistic regression)
- Automated rule adjustments based on economic trends
- Interactive dashboards (Tableau/Power BI)

<!-- --- -->

## 🧾 License
This project is licensed under the MIT License.

## 📚 References
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [Kaggle Loan Approval Dataset](https://www.kaggle.com/datasets/architsharma01/loan-approval-prediction-dataset)
