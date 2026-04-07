# Student-Performance-Data-Audit
Python data profiling and integrity audit for student performance datasets.
import pandas as pd
import numpy as np

import pandas as pd
import numpy as np

# --- SECTION 1: DATA STRUCTURE VALIDATION ---
# Creating a 4x4 dimensional array to demonstrate handling of mixed datatypes (Integer, String, Float, Boolean)
data = [
    [10, "Apple", 15.5, True],
    [20, "Banana", 25.0, False],
    [30, "Cherry", 35.2, True],
    [40, "Date", 45.9, False]
]

# Initializing the DataFrame for structure testing
arr = pd.DataFrame(data)

# Outputting the array to verify successful construction
print("4x4 Array Validation:")
print(arr)

# Verifying schema and datatypes to ensure data integrity
print("\n--- Schema Verification ---")
print(arr.dtypes)


# --- SECTION 2: EXTERNAL DATASET AUDIT ---
# Loading the primary dataset for Exploratory Data Analysis (EDA)
# Dataset: Student Performance Statistics
df = pd.read_csv('study_performance.csv')

# Auditing the first 20 records to inspect for formatting inconsistencies
print("\n--- Initial Record Inspection (Top 20) ---")
print(df.head(20))

# Verifying the end of the file to ensure full data ingestion
print("\n--- Final Record Inspection (Tail) ---")
print(df.tail(3))

# --- SECTION 3: STATISTICAL PROFILING ---
# Generating a statistical summary to identify potential outliers or data anomalies
print("\n--- Statistical Audit Summary ---")
print(df.describe())

# Performing targeted analysis on specific performance metrics
print("\n--- Metric Analysis: Reading Scores ---")
print(f"Mean Score: {df['reading_score'].mean():.2f}")
print(f"Minimum Value: {df['reading_score'].min()}")
print(f"Maximum Value: {df['reading_score'].max()}")

# --- SECTION 4: DATA HEALTH & DISTRIBUTION ---
# Checking for missing values (non-empty entries) and confirming memory usage
print("\n--- Dataset Health Check (Nulls & Memory) ---")
print(df.info())

# Validating demographic distribution to ensure representative sample sizes
print("\n--- Categorical Audit: Race/Ethnicity ---")
print(df['race_ethnicity'].value_counts())

print("\n--- Categorical Audit: Parental Education Level ---")
print(df['parental_level_of_education'].value_counts())

# Identifying distinct values in the 'lunch' category for feature validation
print("\n--- Unique Value Identification: Lunch Program ---")
print(df['lunch'].unique())
print(f"Total Unique Values identified: {df['lunch'].nunique()}")
