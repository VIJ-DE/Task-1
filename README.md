Task-1
Data Cleaning and Preprocessing
Here's a Python (Pandas) code snippet that performs common data cleaning and preprocessing tasks on a dataset:

import pandas as pd

# Load the dataset
df = pd.read_csv('your_dataset.csv')  # Replace with your file path

# Summary  before cleaning
print("Initial shape:", df.shape)
print("Initial missing values:\n", df.isnull().sum())
print("Initial duplicate rows:", df.duplicated().sum())

# 1. Remove duplicate rows
df.drop_duplicates(inplace=True)

# 2. Handle missing values
# Option A: Drop rows with any missing values
# df.dropna(inplace=True)

# Option B: Fill missing values (example for numeric and categorical)
df.fillna({
    col: df[col].mean() if df[col].dtype != 'object' else df[col].mode()[0]
    for col in df.columns
}, inplace=True)

# 3. Standardize text format (e.g., lowercase for object columns)
for col in df.select_dtypes(include='object').columns:
    df[col] = df[col].str.strip().str.lower()

# 4. Standardize date format (example)
# df['date_column'] = pd.to_datetime(df['date_column'])

# 5. Fix numeric precision (optional)
# df['price'] = df['price'].round(2)

# Summary after cleaning
print("Final shape:", df.shape)
print("Missing values after cleaning:\n", df.isnull().sum())

# Save the cleaned dataset
df.to_csv('cleaned_dataset.csv', index=False)
print("Cleaned dataset saved as 'cleaned_dataset.csv'")

Deliverables:

Cleaned file: cleaned_dataset.csv

Summary:

Removed duplicates

Handled missing values (either dropped or filled)

Standardized text (trimmed & lowercased)

Standardized formats (e.g., dates, precision)



Let me know if you want to customize this for a specific dataset or task. You can also upload your dataset, and I’ll adapt this script for it.

