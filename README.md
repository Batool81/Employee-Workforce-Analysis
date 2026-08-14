# Employee Workforce Analysis

##  Project Overview

An end-to-end **Employee Workforce Analysis** project developed in Python to explore workforce structure, salary patterns, employee tenure, team composition, and bonus relationships.

The project demonstrates how raw employee data can be transformed into meaningful business insights through **data cleaning, feature engineering, exploratory data analysis (EDA), statistical analysis, and data visualization**.

The analysis was developed using **Google Colab** and Python's core data analysis libraries.

---

##  Business Objective

The objective of this project is to analyse employee workforce data and answer key business questions related to:

* Workforce size and organisational structure
* Employee distribution across teams
* Gender distribution across the organisation
* Salary distribution and salary variation
* Salary differences between genders and teams
* Relationship between salary and bonus percentage
* Employee tenure and years of service
* Salary trends based on employee start year
* Identification of high-earning employees

The project aims to demonstrate how data analysis can support **workforce planning, compensation analysis, and organisational decision-making**.

---

## Key Business Questions

The analysis investigates the following questions:

1. How many employees are in the organisation?
2. How are employees distributed across teams?
3. How is the workforce distributed by gender?
4. What is the average and median employee salary?
5. Which teams have the highest average salaries?
6. How does salary vary between genders?
7. Is there a relationship between salary and bonus percentage?
8. How has average salary changed according to employee start year?
9. What is the average employee tenure?
10. How many employees earn more than £100,000?
11. Who are the highest-paid employees?
12. Which teams have the largest workforce?

---

#  Technologies & Tools

| Technology       | Purpose                                   |
| ---------------- | ----------------------------------------- |
| **Python**       | Data analysis and programming             |
| **Pandas**       | Data manipulation, cleaning and analysis  |
| **NumPy**        | Numerical operations                      |
| **Matplotlib**   | Data visualization                        |
| **Seaborn**      | Statistical visualization                 |
| **Google Colab** | Development environment                   |
| **GitHub**       | Project documentation and version control |

---

#  Analytical Workflow

The project follows an end-to-end analytical workflow:

```text
Raw Employee Data
       ↓
Data Loading
       ↓
Data Understanding
       ↓
Data Quality Checks
       ↓
Data Cleaning
       ↓
Feature Engineering
       ↓
Exploratory Data Analysis
       ↓
Statistical Analysis
       ↓
Data Visualization
       ↓
Business Findings
       ↓
Conclusion & Recommendations
```

---

# 1. Data Loading

The employee dataset is uploaded into Google Colab and loaded using Pandas.

```python
from google.colab import files

uploaded = files.upload()

df = pd.read_csv("employees.csv")
```

The first and last records are then inspected to understand the structure of the dataset.

---

# 2. Data Understanding

Initial analysis includes:

* Dataset dimensions
* Column names
* Data types
* Dataset information
* First and last observations

```python
df.shape
df.columns
df.dtypes
df.info()
df.head()
```

This provides an initial understanding of the employee dataset before analysis begins.

---

# 3. Data Quality Assessment

The project checks for common data-quality issues including:

* Missing values
* Duplicate records
* Number of unique teams
* Number of gender categories
* Date-format consistency

```python
df.isnull().sum()
df.duplicated().sum()
```

---

# 4. Data Cleaning

The `Start Date` field is converted into a proper datetime format, and duplicate records are removed.

```python
df["Start Date"] = pd.to_datetime(
    df["Start Date"],
    errors="coerce"
)

df = df.drop_duplicates()
```

This prepares the dataset for reliable analysis.

---

# 5. Feature Engineering

Two analytical features are created from the employee start date:

### Start Year

The year an employee joined the organisation.

### Years of Service

An estimate of employee tenure based on the start year.

```python
df["Start Year"] = df["Start Date"].dt.year

df["Years of Service"] = (
    2026 - df["Start Year"]
)
```

These features allow employee tenure and salary trends to be investigated.

---

# 6. Workforce KPIs

Key workforce indicators are calculated, including:

* Total employees
* Average salary
* Median salary
* Highest salary
* Average bonus percentage
* Number of teams
* Average years of service

Example:

```python
total_employees = len(df)

average_salary = df["Salary"].mean()

median_salary = df["Salary"].median()

average_bonus = df["Bonus %"].mean()
```

These KPIs provide a high-level overview of the organisation's workforce.

---

#  Exploratory Data Analysis

## 7. Employees by Team

Employee counts are calculated for each team and visualised using a horizontal bar chart.

This identifies teams with the largest and smallest workforce populations.

---

## 8. Employee Gender Distribution

The project analyses the overall gender composition of the workforce using a count plot.

This provides an overview of workforce demographics.

---

## 9. Team & Gender Distribution

A grouped count plot compares gender distribution across individual teams.

This allows differences in team composition to be explored visually.

---

#  Salary Analysis

## 10. Salary Distribution

A histogram with a KDE curve is used to examine the distribution of employee salaries.

This helps identify:

* The general salary range
* Concentration of salaries
* Distribution shape
* Potential skewness

---

## 11. Salary Outliers

A box plot is used to examine salary variation and identify potential outliers.

The analysis also calculates:

* Mean
* Median
* Minimum
* Maximum
* Standard deviation

---

## 12. Salary by Gender

Salary statistics are calculated separately for each gender.

The analysis includes:

* Number of employees
* Average salary
* Median salary
* Minimum salary
* Maximum salary

An average-salary comparison is then visualised using a bar chart.

---

## 13. Salary by Team

Salary statistics are calculated for each team, including:

* Employee count
* Average salary
* Median salary
* Standard deviation
* Minimum salary
* Maximum salary

The project also identifies the **top 10 teams by average salary**.

---

# Salary & Bonus Analysis

## 14. Salary vs Bonus Percentage

A scatter plot is used to investigate the relationship between employee salary and bonus percentage.

The Pearson correlation coefficient is also calculated:

```python
salary_bonus_correlation = (
    df["Salary"].corr(df["Bonus %"])
)
```

This provides a numerical measure of the relationship between the two variables.

---

# Correlation Analysis

A correlation heatmap is created using:

* Salary
* Bonus %
* Start Year
* Years of Service

This provides an overview of relationships between key numerical employee variables.

---

#  Salary Trends

Average salary is calculated according to employee start year.

A line chart is then used to visualise how average salary varies across different joining years.

---

#  Employee Tenure

Years of service are analysed to understand the distribution of employee tenure.

A histogram is used to visualise the number of employees across different tenure levels.

The project also investigates the relationship between:

**Years of Service → Salary**

using a scatter plot.

---

# High-Earning Employees

Employees earning more than **£100,000** are identified and analysed.

```python
high_earners = df[
    df["Salary"] > 100000
]
```

The project also identifies the **top 10 highest-paid employees** using:

```python
df.nlargest(10, "Salary")
```

---

# Team Workforce Summary

A consolidated team-level summary is created containing:

* Number of employees
* Average salary
* Median salary
* Average bonus
* Average years of service

This provides a single analytical view of workforce characteristics across teams.

---

#  Key Outputs

The analysis produces several important outputs:

### Workforce

* Total employee count
* Number of teams
* Team size distribution
* Gender distribution

### Compensation

* Average salary
* Median salary
* Salary range
* Salary variation
* Highest-paid employees
* High-earner count

### Employee Tenure

* Average years of service
* Tenure distribution
* Salary vs tenure relationship

### Relationships

* Salary vs bonus correlation
* Correlation between salary, bonus and tenure

---

#  Business Insights

The final notebook automatically calculates key metrics such as:

* Largest team
* Team with the highest average salary
* Average salary
* Median salary
* Highest salary
* Average bonus percentage
* Average employee tenure
* Salary/bonus correlation

The actual numerical findings are generated directly from the dataset to ensure that conclusions are **data-driven rather than assumed**.

---

#  Potential Business Recommendations

Depending on the findings from the analysis, the organisation could investigate:

* Salary variation between teams
* Compensation consistency across similar workforce groups
* Relationship between salary and bonus structures
* Workforce distribution across teams
* Employee tenure and retention patterns
* Potential salary outliers requiring further review
* Workforce planning based on team size and employee tenure

These recommendations should be interpreted alongside organisational policies, job roles, seniority, performance, and other factors not included in the dataset.

---

#  Skills Demonstrated

This project demonstrates practical experience with:

* Python
* Pandas
* NumPy
* Data Cleaning
* Data Quality Assessment
* Feature Engineering
* Exploratory Data Analysis
* Descriptive Statistics
* GroupBy & Aggregation
* Data Filtering
* Data Visualization
* Matplotlib
* Seaborn
* Correlation Analysis
* Business Analysis
* Data-driven Insights

---

#  Conclusion

This project demonstrates an end-to-end approach to analysing employee workforce data using Python.

---

## Author

Batool Fouz

Data Analytics | Python | SQL | Power BI | Excel | Machine Learning
