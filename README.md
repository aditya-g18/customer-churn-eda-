# Customer Churn Analysis (EDA) using Python

## 📌 Project Overview

This project focuses on **Exploratory Data Analysis (EDA)** of a telecom **Customer Churn dataset** using Python.

Customer churn refers to when customers **stop using a company's service**. Understanding churn is very important for businesses because retaining customers is often cheaper than acquiring new ones.

In this project, the dataset was explored, cleaned, and visualized to identify **patterns and factors that influence customer churn**.

The analysis was performed using **Python, Pandas, Matplotlib, and Seaborn in Jupyter Notebook**.

---

# 🎯 Objective

The main objectives of this project were:

* Understand the **distribution of churned vs non-churned customers**
* Identify **customer characteristics related to churn**
* Analyze how **services, demographics, and tenure impact churn**
* Visualize patterns using **data visualization techniques**

---

# 🧰 Tools & Libraries Used

The following Python libraries were used:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

* **Pandas** → data manipulation and analysis
* **NumPy** → numerical operations
* **Matplotlib** → data visualization
* **Seaborn** → advanced statistical visualizations

---

# 📂 Dataset Description

The dataset contains telecom customer information such as:

* CustomerID
* Gender
* SeniorCitizen
* Partner
* Dependents
* Tenure
* PhoneService
* InternetService
* Contract
* MonthlyCharges
* TotalCharges
* Churn

The **target variable** is:

**Churn**

* Yes → Customer left the company
* No → Customer stayed

---

# 🔎 Data Exploration

Basic dataset exploration was performed using the following commands:

```python
df.head()
df.shape
df.info()
df.describe()
df.isnull().sum()
df.duplicated().sum()
```

This helped understand:

* dataset structure
* column data types
* missing values
* duplicate records
* statistical summary of numerical columns

---

# 🧹 Data Cleaning

## 1️⃣ Converting TotalCharges Column

The `TotalCharges` column contained **string values instead of numeric values**, so it was converted to numeric.

```python
df['TotalCharges'] = pd.to_numeric(df['TotalCharges'], errors='coerce')
```

---

## 2️⃣ Handling Missing Values

Missing values in `TotalCharges` were filled using the mean.

```python
df['TotalCharges'] = df['TotalCharges'].fillna(df['TotalCharges'].mean())
```

---

## 3️⃣ Converting SeniorCitizen Column

The column contained values **0 and 1**, which were converted to more readable labels.

```python
df['SeniorCitizen'] = df['SeniorCitizen'].replace({0:'No', 1:'Yes'})
```

---

# 📊 Exploratory Data Analysis

Several visualizations were created to analyze churn patterns.

---

# 1️⃣ Churn Distribution

```python
sns.countplot(x='Churn', data=df)
plt.title("Customer Churn Distribution")
```

This chart shows how many customers **stayed vs left** the company.

---

# 2️⃣ Churn Percentage

```python
gd = df.groupby('Churn').agg({'Churn':'count'})

plt.pie(gd['Churn'], labels=gd.index, autopct='%1.1f%%')
```

This visualization shows the **percentage of churned and retained customers**.

---

# 3️⃣ Gender vs Churn

```python
sns.countplot(x='gender', data=df, hue='Churn')
```

This compares churn behavior between **male and female customers**.

---

# 4️⃣ Senior Citizen vs Churn

```python
sns.countplot(x='SeniorCitizen', data=df, hue='Churn')
```

This visualization shows how churn differs between **senior citizens and non-senior customers**.

---

# 5️⃣ Senior Citizen Churn Percentage

```python
ct = pd.crosstab(df['SeniorCitizen'], df['Churn'], normalize='index') * 100
ct.plot(kind='bar', stacked=True)
```

This stacked bar chart shows **percentage churn for each group**.

---

# 6️⃣ Tenure Distribution

```python
sns.histplot(x='tenure', data=df)
```

This visualization helps understand how **customer tenure affects churn behavior**.

---

# 🔍 Key Insights

From the analysis, several important insights were observed:

### 1️⃣ Overall Churn Rate

A noticeable portion of customers have churned, indicating **customer retention challenges**.

---

### 2️⃣ Senior Citizens Have Higher Churn

Senior citizens show **higher churn rates compared to non-senior customers**.

---

### 3️⃣ Tenure Plays an Important Role

Customers with **short tenure are more likely to churn**, while customers who stay longer tend to remain loyal.

---

### 4️⃣ Gender Has Little Impact

Churn distribution between male and female customers appears **relatively balanced**, suggesting gender is not a strong churn factor.

---

# 📈 Skills Demonstrated

This project demonstrates important **data analyst skills**, including:

* Data Cleaning
* Handling Missing Values
* Data Type Conversion
* Exploratory Data Analysis (EDA)
* Data Visualization
* Pattern Identification
* Business Insight Generation

---

# 🚀 Future Improvements

Possible extensions for this project:

* Build a **Machine Learning model to predict churn**
* Perform **feature engineering**
* Create an **interactive dashboard using Power BI or Tableau**
* Deploy churn prediction using **Streamlit**

---

# 👨‍💻 Author

Aditya Gupta
Aspiring **Data Analyst / Data Scientist**

Learning **Python, Data Analysis, Machine Learning, and Data Visualization**.
