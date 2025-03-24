# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv("/content/titanic_dataset .csv")  # Replace with actual path

# Display basic info
df.info()

# Display first few rows
df.head()

# Check shape
print(f"Dataset contains {df.shape[0]} rows and {df.shape[1]} columns")
```
1
```
# Set PassengerId as index
df.set_index("PassengerId", inplace=True)

# Summary statistics
df.describe()
```
2

```
# Count unique values in categorical columns
categorical_columns = ["Survived", "Pclass", "Sex", "Embarked"]
for col in categorical_columns:
    print(f"{col} unique values:\n", df[col].value_counts(), "\n")
```
3

```
sns.countplot(data=df, x="Survived")
plt.title("Survival Count")
plt.show()
```
4

```
df["Pclass"].unique()
```
5

```
df.rename(columns={"Sex": "Gender"}, inplace=True)
```
```
sns.catplot(x='Survived', hue='Gender', data=df, kind='count')
plt.title("Survival by Gender")
plt.show()
```
6

```
sns.boxplot(x="Survived", y="Age", data=df)
plt.title("Age Distribution by Survival")
plt.show()
```
7
```
sns.boxplot(x="Pclass", y="Age", hue="Gender", data=df)
plt.title("Age Distribution Across Passenger Classes and Gender")
plt.show()
```
8

```

sns.catplot(x="Pclass", y="Survived", hue="Gender", data=df, kind="bar")
plt.title("Survival Rate by Passenger Class and Gender")
plt.show()
```
9

```

plt.figure(figsize=(10,6))

# Select only numerical columns
numerical_df = df.select_dtypes(include=["number"])

# Compute correlation and plot heatmap
sns.heatmap(numerical_df.corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Feature Correlation Heatmap")
plt.show()

```
10

```

sns.pairplot(df, hue="Survived", diag_kind="kde")
plt.show()

```
11


# RESULT
       
