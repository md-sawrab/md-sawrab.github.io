---
layout: post
title:  Statistics for Data Science — Measure of Dispersion
date: 2024-12-28 2:50
categories: [Statistics Blog Series]
tags: [Statistics]
---

Welcome to the new series — Statistics For Data Science. In this article, we will dive into the fundamental concepts of measures of dispersion. In the second article of this series, we discussed Measures of Central Tendency.

Descriptive statistics not only help in summarizing data but also in understanding its variability. Measures of dispersion are essential for understanding the spread or variability within a dataset.

In this article, we’ll explore the different measures of dispersion like range, variance, and standard deviation, Interquartile Range (IQR) and their importance in data science.

### **What is Dispersion?**

Dispersion refers to the extent to which data points differ from the central value (mean or median). If the data points are close to the central value, the dispersion is low, and if they are spread out, the dispersion is high. Dispersion gives us insights into the consistency of the data. It answers questions like:

- How tightly are the data points clustered?
- Is there a significant variation in the data?
- Are there any outliers?

Understanding the spread of data is essential for predictive modeling, hypothesis testing, and data analysis.

There are few metrics which tells about the dispersion of a dataset:

1. Range
2. Variance
3. Standard deviation
4. Interquartile Range (IQR)

### **Why is Dispersion Important?**

Dispersion is important because central tendency measures like mean and median alone cannot describe a dataset comprehensively. Two datasets with the same mean can have very different distributions, and ignoring dispersion can lead to misleading interpretations.

For example, if two datasets have the same average income, one might think the distribution is identical. However, one dataset may have incomes tightly clustered around the mean, while the other might include people with extremely low and extremely high incomes. The measure of dispersion helps capture this spread and provides a more complete understanding of the data.

### **Common Measures of Dispersion**

#### Range:
The range is the simplest measure of dispersion. It is the difference between the maximum and minimum values in a dataset. It provides a simple measure of the spread or variability of the data.

Formula:

Range = Max Value — Min Value

Example:

Consider the following data set: 4, 6, 9, 14, 18

Here,

Minimum Value = 4
Maximum Value = 18
Range = 18–4 = 14

The range tells us that the data spans 14 units.

Python Code:

data = [4, 6, 9, 14, 18]
data_range = max(data) - min(data)
print(f"Range: {data_range}")
Output:

# Range: 14
Interpretation of the range depends on the specific dataset and context. A larger range indicates greater variability in the data, while a smaller range suggests less variability.

2. Variance

Variance in statistics is a measure of how much the values in a dataset differ from the mean (average) of the data. It provides an idea of the spread or dispersion of the data points.

Formula for Population: For a population, variance σ² is calculated as:


Where:

N is the total number of observations in the population.
xi​ represents each data point.
x̄ is the population mean.
Formula for Sample: For a sample, variance is calculated as:


Where:

n is the total number of observations in the sample.
x̄ is the sample mean.
Example:

Consider the sample data set: 3, 7, 8, 10, 15

Mean (x̄) = 8.6
Deviations from the mean: -5.6, -1.6, -0.6, 1.4, 6.4
Squared deviations: 31.36, 2.56, 0.36, 1.96, 40.96
Sum of squared deviations:


Sample Variance:


Python Code:

import pandas as pd

# Sample data
data = pd.Series([10, 20, 15, 25, 30, 5, 40])

# Calculate Variance
variance = data.var()
print(f"Variance: {variance}")
Output:


# Variance: 145.23809523809524
Variance can also be influenced by the outliers as the extreme values can make the impact as like as range. if the variance is high, it implies the data points in the dataset are widely dispersed (far away from the mean value) while the lower value says the data points are close to each other.

3. Standard Deviation

The standard deviation is the square root of the variance. It is more interpretable than variance as it is in the same units as the original data.

Formula for population:


Formula for sample:


Example:
Example:

Using the previous variance example (sample variance = 19.3):


Python Code

# Calculate Standard Deviation
std_dev = data.std()
print(f"Standard Deviation: {std_dev}")
4. Interquartile Range (IQR)

The interquartile range is a measure of the spread of the middle 50% of the data. It is the difference between the third quartile (Q3) and the first quartile (Q1).

Formula:

IQR = Q3 — Q1

Where:
- Q1 is the median of the first half of the data (25th percentile)
- Q3 is the median of the second half of the data (75th percentile)

Example:

Consider the data set: 3, 7, 8, 10, 15

- Arrange the data in ascending order: 3, 7, 8, 10, 15
- Median (Q2) = 8
- First Quartile (Q1) = 7
- Third Quartile (Q3) = 10

IQR = 10–7 = 3

Python Code:

# Calculate IQR
iqr = data.quantile(0.75) - data.quantile(0.25)
print(f"Interquartile Range (IQR): {iqr}")
Output

# Interquartile Range (IQR): 3.0
The IQR is useful for understanding the spread of the central data points while being resistant to outliers. It is often used in boxplots to identify outliers and the spread of data.

### **Use of Dispersion in Data Science**

In data science, understanding the variability of your data is critical in several ways:

- **Modeling:** Models like linear regression assume homoscedasticity (constant variance of errors). If the variance changes, it can affect model accuracy.
- **Outliers:** High dispersion may indicate outliers or data points that are unusually far from the central tendency.
- **Risk Assessment:** In fields like finance, a higher standard deviation indicates higher risk because the data (e.g., returns) is more spread out.
- **Comparison of Datasets:** The coefficient of variation allows for the comparison of datasets that are on different scales or have different units.

Thanks for reading .