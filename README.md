# Exp No.2 : Exploratory Data Analysis (EDA)

## Aim
To perform Exploratory Data Analysis (EDA) on the heart disease dataset to understand the data distribution, relationships, and key patterns useful for business insights and model building.

## Dataset
The dataset used for this experiment is `heartdisease.csv`. It contains medical and demographic information such as age, sex, cholesterol levels (`totChol`), `BMI`, blood pressure, and target values (`TenYearCHD`) indicating heart disease presence.

## Algorithm
1. Import required Python libraries (`numpy`, `pandas`, `seaborn`, `matplotlib`).
2. Load the dataset into a Pandas DataFrame.
3. Display the dataset structure, shape, and descriptive statistics.
4. Check for missing values and duplicate rows.
5. Examine correlations among numeric features using a correlation matrix and heatmap.
6. Visualize univariate distributions using histograms, boxplots, and countplots.
7. Analyze bivariate and multivariate relationships using scatter plots and pairplots.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Basic Exploration** | `df.info()` | Inspect dataset structure and data types |
| | `df.describe()` | Generate descriptive statistics |
| | `df.isnull().sum()` | Detect missing values in each column |
| | `df.duplicated().sum()` | Identify duplicate rows |
| | `df.corr()` | Find correlations between numeric variables |
| **Univariate Analysis** | `sns.histplot()` | Plot histogram (distribution of single variable) |
| | `sns.boxplot()` | Identify outliers using boxplot |
| | `sns.countplot()` | Count occurrences of categorical variables |
| **Bivariate Analysis** | `sns.scatterplot()` | Display relationship between two variables |
| | `sns.heatmap()` | Show correlation matrix visually |
| **Multivariate Analysis** | `sns.pairplot()` | Show pairwise relationships across variables |
| **Visualization Controls** | `plt.figure()`, `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display plotted charts |

## Program & Output
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv('/content/heartdisease.csv')

# Basic Exploration
print("=== Dataset Shape ===")
print(df.shape)

print("\n=== Dataset Info ===")
df.info()

print("\n=== First 5 Rows ===")
display(df.head())

print("=== Descriptive Statistics ===")
display(df.describe())

print("\n=== Missing Values ===")
print(df.isnull().sum())

print("\n=== Duplicate Rows ===")
print(df.duplicated().sum())

# Univariate Analysis
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

# Age distribution
sns.histplot(df['Age'], kde=True, ax=axes[0], color='skyblue')
axes[0].set_title('Age Distribution')

# Cholesterol boxplot to find outliers
if 'Totalcholestrol' in df.columns:
    sns.boxplot(y=df['Totalcholestrol'], ax=axes[1], color='lightgreen')
    axes[1].set_title('Cholesterol Boxplot')

# Target class count (TenYearCHD)
if 'TenYearCHD' in df.columns:
    sns.countplot(x=df['TenYearCHD'], ax=axes[2], palette='pastel')
    axes[2].set_title('TenYearCHD Count')

plt.tight_layout()
plt.show()

# Correlation Analysis
plt.figure(figsize=(12, 8))
correlation_matrix = df.corr(numeric_only=True)
sns.heatmap(correlation_matrix, annot=True, fmt='.2f', cmap='coolwarm', linewidths=0.5)
plt.title('Correlation Matrix Heatmap')
plt.show()

# Bivariate Analysis
if 'Age' in df.columns and 'Totalcholestrol' in df.columns and 'TenYearCHD' in df.columns:
    plt.figure(figsize=(10, 6))
    sns.scatterplot(x='Age', y='Totalcholestrol', hue='TenYearCHD', data=df, alpha=0.7)
    plt.title('Age vs Cholesterol by Heart Disease Status (TenYearCHD)')
    plt.xlabel('Age')
    plt.ylabel('Total Cholesterol')
    plt.grid(True, linestyle='--', alpha=0.5)
    plt.show()

    <img width="523" height="612" alt="image" src="https://github.com/user-attachments/assets/5a5ea5eb-24f2-41cf-bd45-264feda23a54" />
    <img width="1697" height="310" alt="image" src="https://github.com/user-attachments/assets/71235354-cd1c-4bba-9fd0-80a805cac5d4" />
    <img width="1698" height="402" alt="image" src="https://github.com/user-attachments/assets/c04fef42-7ff1-4352-8350-5484508b69c1" />
    <img width="486" height="506" alt="image" src="https://github.com/user-attachments/assets/783fe44d-1461-4ed0-90e2-344cab301a01" />
    <img width="1706" height="571" alt="image" src="https://github.com/user-attachments/assets/f585d690-81fe-42d4-9f4c-38a502256437" />
<img width="1187" height="675" alt="image" src="https://github.com/user-attachments/assets/a5394fda-34e5-4bb2-8752-69e92522d13a" />





## Result
The heart disease dataset has 250 records with no missing values, showing normal age distributions and some cholesterol outliers.
