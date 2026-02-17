Overview

This project analyzes NYC job postings using PySpark. The dataset was cleaned, transformed, and enriched with engineered features to answer business KPIs such as job category distribution, salary trends, qualification impact, and highest paid skills.

Data Processing
Cleaning & Preprocessing

Converted salary columns (Salary Range From, Salary Range To) to numeric.

Created avg_salary as mean of salary range.

Extracted posting year using regex due to malformed date values.

Parsed qualification text to identify degree requirement.

Feature Engineering

The following features were added:

avg_salary – average of salary range

has_degree – binary flag derived from minimum qualification text

salary_bucket – High / Medium / Low salary category

posting_year – extracted year from posting date

Basic Validation test added:
assert df.filter(col("avg_salary").isNull()).count() == 0


Deployment:
The pyspark application is containerized using Docker
Code should be in git


Triggerring Approach includes,
CI/CD pipeline
Airflow
Cron job



Challenges & Learnings
Challenges

Dirty date fields containing text instead of timestamps and missing numeric values in salary columns, unstructured data in few columns
 
Learnings
Needed few libraries to install on local laptop
Defensive parsing using regex
Date casting


Assumptions

Salary is calculated as average of min/max range.

Degree requirement inferred via text matching.

Skills extracted using comma separation.
