Employee Data Analysis & Scientific Computing
A comprehensive Data Science script demonstrating data manipulation, statistical analysis, array operations, and data visualizations using Python's core data science libraries: Pandas, NumPy, Matplotlib, and Seaborn.

Project Overview
This repository features an Exploratory Data Analysis (EDA) pipeline on an employees.csv dataset. It illustrates fundamental techniques in Python for cleaning, subsetting, summarizing, and visualizing structured tabular data alongside numerical matrix computations.

Key Objectives:
Data Manipulation: File I/O, subsetting (loc/iloc), filtering, indexing, and handling missing value structures.

Aggregations & Grouping: Calculating summary statistics (mean, min, max, standard deviation) grouped by categorical attributes such as Gender and Team.

Numerical Computing: Array operations, matrix arithmetic, and broadcasting using NumPy.

Data Visualization: Creating diagnostic charts (Box plots, Histograms, Scatter plots, Line charts, Count plots, and Correlation Heatmaps).

Tech Stack & Dependencies
Language: Python 3.x

Libraries:

pandas — Data structures and tabular data manipulation

numpy — Multi-dimensional array operations and linear algebra

matplotlib — Base visualization framework

seaborn — High-level statistical data visualization

 Visualizations Highlights
The analysis covers several visual insights derived from the dataset:

Analysis Type	Chart Type	Purpose / Description
Distribution	Box Plot & Histogram	Examines the spread, median, outliers, and skewness of employee salaries.
Relationship	Scatter Plot	Evaluates the relationship between Salary and Bonus %.
Time Series	Line Plot	Tracks average salary trends over time based on employee Start Year.
Categorical	Count Plot	Compares team distributions segmented by Gender.
Correlation	Heatmap	Visualizes feature correlations between numerical metrics (Salary vs. Bonus %).
 Code Snippets & Workflow
1. Data Cleaning & Feature Engineering
Python
import pandas as pd

df = pd.read_csv("employees.csv")

# Convert 'Start Date' to datetime and extract the start year
df['Start Date'] = pd.to_datetime(df['Start Date'])
df['Start Year'] = df['Start Date'].dt.year

# Filter high earners
high_salaries = df[df["Salary"] > 100000]
2. Grouping & Aggregations
Python
# Average salary segment by Gender and Team
gender_salary = df.groupby('Gender')['Salary'].mean()
team_metrics = df.groupby(['Team']).mean(numeric_only=True)
3. Array Operations with NumPy
Python
import numpy as np

ar1 = np.array([[2, 3], [4, 2]])
ar2 = np.array([[[8, 3], [4, 2]], [[2, 3], [4, 2]]])

# Matrix operations
element_sum = np.add(ar1, ar2)
std_dev = ar2.std()


Run the analysis:
Open the provided script/notebook in Google Colab or Jupyter Notebook.

Upload your employees.csv file when prompted.
