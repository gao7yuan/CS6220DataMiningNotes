# Week3 Data Preprocessing
9/16/19

## Data Transformation
- Aggregation
  - Combining two or more objects into a simple object
- Normalization / Standardization
  - Goal: entire set of data has a property
  1. min-max
  2. z-score
    - average = 0, std = 1
  3. normalization by decimal scaling
- Generalization
- Feature construction

## Data Cleaning
- Filling in missing data
  1. Ignore the instance
  2. Fill in the missing value manually
  3. Use a global constant to fill in the missing value
  4. Imputation
- Imputing missing data
  - Cold deck: mean, medium, etc.
    - good: efficient
    - bad: outliers, other feature values
  - Hot deck: similar case
    - good: simple
    - bad: more than one similar case
  - Distribution-based imputation: probability
    - good: more reliable
    - bad: estimate for each feature
  - Expectation-Maximization (EM) imputation
  - Statistical imputation
    - missing value as output, all the other values as input
    - good: impute value based on other features
    - bad: slow
  - Predictive imputation
    - good: accurate
    - bad: slow
- Smoothing out noisy data
  - noise = random error or variance in a measured variable
  - binning
    - consulting neighbor
  - clustering
  - regression
- Binning
  - equal-width partitioning
    - good: straightforward
    - bad: outliers or skewed not handled
  - equal-depth partitioning
    - good: data scaling
    - bad: managing categorical features
  - smoothing by bin means
  - smoothing by bin boundaries
- Removing outliers and artifacts
- Correcting inconsistent data
- Removing duplicate data

## Data Reduction
- PCA
  - random project vs. PCA
  - Scree plots
    - knee or elbow point
