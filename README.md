
# Probability Density Function Learning using Roll-Number-Parameterized Non-Linear Model

## Overview
This project demonstrates the learning of parameters of a probability density function after applying a roll-number-based non-linear transformation to real-world air quality data. The NO₂ concentration values from the India Air Quality dataset are used as the input feature.

The objective of the work is to apply a deterministic transformation, model the transformed data using a Gaussian-shaped probability density function, and estimate its parameters using statistical techniques.

---

## Dataset
- Source: India Air Quality Dataset (Kaggle)
- Feature Used: NO₂ concentration
- Data Type: Real-world environmental data

Non-numeric and missing values are removed during preprocessing.

---

## Methodology

### Step 1: Roll-Number-Based Transformation
Each NO₂ value \( x \) is transformed into a new variable \( z \) using the following function:

\[
z = x + a_r \sin(b_r x)
\]

where,

\[
a_r = 0.05 \times (r \bmod 7)
\]
\[
b_r = 0.3 \times ((r \bmod 5) + 1)
\]

Here, \( r \) represents the university roll number. This transformation introduces a controlled non-linearity while remaining deterministic.

---

### Step 2: Probability Density Function Modeling
The transformed variable \( z \) is modeled using the following probability density function:

\[
\hat{p}(z) = c \cdot e^{-\lambda (z - \mu)^2}
\]

This form corresponds to a Gaussian-shaped distribution.

---

### Step 3: Parameter Estimation
The parameters of the probability density function are learned using Maximum Likelihood Estimation (MLE):

- Mean (\( \mu \)) is estimated as the sample mean of \( z \)
- Variance (\( \sigma^2 \)) is estimated as the sample variance of \( z \)
- Lambda (\( \lambda \)) is computed as:
  \[
  \lambda = \frac{1}{2\sigma^2}
  \]
- Normalization constant (\( c \)) is computed as:
  \[
  c = \sqrt{\frac{\lambda}{\pi}}
  \]

These parameters ensure that the probability density function integrates to one.

---

## Results

### Estimated Parameters

| Parameter | Description |
|---------|-------------|
| \( mu \) | Mean of transformed variable |
| \( lambda \) | Inverse variance parameter |
| \( c \) | Normalization constant |

The exact numerical values are obtained by executing the provided Python script.


---

## Tools and Technologies
- Python
- NumPy
- Pandas

Statistical estimation methods are used; no machine learning libraries are involved.

---

## Repository Structure
