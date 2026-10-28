# Statistics I, Day 3: Descriptive Statistics and the Normal Distribution

Welcome to Day 3! Today we tie together everything from Days 1 and 2 into one complete descriptive-statistics problem. Then we introduce the normal distribution and learn how to compute probabilities using Z-scores.

---

## Part A: A Complete Descriptive-Statistics Problem

**Problem:** For the sample data below, find the mean, median, mode, midrange, range, variance, standard deviation, quartiles, interquartile range, and the upper and lower fences. Decide whether any observation is an outlier.

[3, 7, 12, 14, 15, 15, 19, 20, 21, 45]   (n = 10)

The data are already sorted.

### 1. Measures of Center and Location

**Mean:** Add all values and divide by n:
x̄ = (3 + 7 + 12 + 14 + 15 + 15 + 19 + 20 + 21 + 45) / 10 = 171 / 10 = 17.1

**Median (Q₂):** n is even, so average the 5th and 6th values. Both are 15.
M = 15

**Mode:** The only repeated value is 15 (it appears twice).
Mode = 15

**Midrange:** The value halfway between the smallest and largest:
(min + max) / 2 = (3 + 45) / 2 = 24

### 2. Measures of Variation and Spread

**Range:** max − min = 45 − 3 = 42

**Quartiles** (using the linear-interpolation method):

| Quartile | Position of rank | Value |
| :---: | :--- | :---: |
| Q₁ (25th) | (n−1)(0.25) + 1 = 3.25 | 12 + 0.25(14 − 12) = 12.5 |
| Q₂ (median) | | 15 |
| Q₃ (75th) | (n−1)(0.75) + 1 = 7.75 | 19 + 0.75(20 − 19) = 19.75 |
| Q₄ (max) | | 45 |

**Interquartile Range:**
IQR = Q₃ − Q₁ = 19.75 − 12.5 = 7.25

**Outlier fences:**
Lower fence = Q₁ − 1.5(IQR) = 12.5 − 1.5(7.25) = 1.625
Upper fence = Q₃ + 1.5(IQR) = 19.75 + 1.5(7.25) = 30.625

Since 45 > 30.625, the value **45 is an outlier**. Nothing is below 1.625.

**Sample variance:**
s² = Σ(xᵢ − x̄)² / (n − 1) = 1150.9 / 9 ≈ 127.88

**Sample standard deviation:**
s = √127.88 ≈ 11.31

**Note on quartile conventions:** Quartile methods differ. On Day 2 (n = 15), we got Q₁ = 7 and Q₃ = 19 by excluding the median and averaging each half. Here (n = 10), the values 12.5 and 19.75 come from linear interpolation. Both are correct under their own convention, which is exactly why calculators, software, and textbooks can report slightly different quartiles for the same data. Always apply one method consistently and know which one your tools use.

### Summary of Results

| Statistic | Value |
| :--- | ---: |
| Mean | 17.1 |
| Median | 15 |
| Mode | 15 |
| Midrange | 24 |
| Range | 42 |
| Q₁ | 12.5 |
| Q₂ (median) | 15 |
| Q₃ | 19.75 |
| IQR | 7.25 |
| Lower fence / Upper fence | 1.625 / 30.625 |
| Sample variance s² | ≈ 127.88 |
| Sample std. dev. s | ≈ 11.31 |
| Outlier? | Yes, 45 |

---

## Part B: Normal-Distribution Probability Applications

Suppose a variable X is approximately **normal** with mean μ = 8.5 and standard deviation σ = 2.3:

X ~ N(8.5, 2.3)

Because there are infinitely many normal distributions, we **standardize** every value to a **z-score**, which converts X to the *standard normal* Z ~ N(0,1):

z = (x − μ) / σ

We then read the probability P(Z < z) from the standard-normal table (area to the left of z) or from a calculator.

### A. Proportion less than 7.5

1. Standardize: z = (7.5 − 8.5) / 2.3 = (−1.0) / 2.3 ≈ −0.4348
2. Look up the cumulative area:
   P(X < 7.5) = P(Z < −0.4348) ≈ 0.3319 (33.19%)

### B. Proportion greater than 10.1

1. Standardize: z = (10.1 − 8.5) / 2.3 = 1.6 / 2.3 ≈ 0.6957
2. Use the complement. Tables give area to the left, so subtract from 1:
   P(X > 10.1) = 1 − P(Z < 0.6957) ≈ 1 − 0.7567 = 0.2433 (24.33%)

### C. Proportion between 7.5 and 10.1

Take the difference of the two cumulative areas:
P(7.5 < X < 10.1) = P(Z < 0.6957) − P(Z < −0.4348) ≈ 0.7567 − 0.3319 = 0.4248 (42.48%)

### Tips for Normal Calculations

- Always convert to a z-score first.
- The standard-normal table gives area to the left (<). For a right tail (>), use 1 minus the left area.
- For an interval, subtract the smaller cumulative area from the larger one.
- Check plausibility: our three answers add up as expected, 0.3319 + 0.4248 + 0.2433 = 1.000.

---

## Key Formulas

| Quantity | Formula | Plain meaning |
| :--- | :--- | :--- |
| Mean | x̄ = Σxᵢ / n | Sum divided by count |
| Median | Middle value | Average two middle values if n is even |
| Mode | Most frequent value | Value appearing most often |
| Midrange | (min + max) / 2 | Minimum plus maximum, divided by 2 |
| Range | max − min | Largest minus smallest |
| Q₁, Q₃ (linear interp.) | rank (n−1)p | Value at the 25% or 75% position |
| IQR | Q₃ − Q₁ | Middle-50% spread |
| Fences | Q₁ − 1.5×IQR, Q₃ + 1.5×IQR | Quartiles minus/plus 1.5 times IQR |
| Sample variance / SD | s² = Σ(xᵢ − x̄)² / (n−1); s = √s² | Average squared deviation divided by n−1; its square root |
| z-score | z = (x − μ) / σ | Value minus mean, divided by SD |
| Normal probability | P(a < X < b) = P(zₐ < Z < z_b) | Difference of two cumulative areas |

---

## Practice Problems

**1.** For [4, 6, 7, 9, 10, 12, 40], find: mean, median, mode, range, Q₁, Q₃, IQR, the outlier fences (linear-interpolation quartiles), sample SD, and flag any outlier.

<details><summary>Solution</summary>

Mean = 88/7 ≈ 12.57; median = 9; no mode; range = 40 − 4 = 36. Linear-interp. quartiles: Q₁ = 6.5, Q₃ = 11, IQR = 4.5. Fences: lower = 6.5 − 1.5(4.5) = −0.25; upper = 11 + 1.5(4.5) = 17.75. Since 40 > 17.75, 40 is an outlier; nothing below −0.25. Sample SD: s² ≈ 153.29, so s ≈ 12.38.

</details>

**2.** In problem 1, which summary statistic is most affected by the outlier (40) and which is least? Explain.

<details><summary>Solution</summary>

Most affected: the mean (12.57) and the standard deviation and range, which shoot up. Least affected: the median (9) and the IQR (4.5); these are resistant to outliers.

</details>

**3.** Let X ~ N(50, 10). Find (a) P(X < 40), (b) P(X > 65), (c) P(40 < X < 65).

<details><summary>Solution</summary>

(a) z = (40 − 50) / 10 = −1 → P ≈ 0.1587; (b) z = (65 − 50) / 10 = 1.5 → P(Z > 1.5) ≈ 0.0668; (c) 0.9332 − 0.1587 = 0.7745.

</details>

**4.** Why do we convert to a z-score before using the standard-normal table?

<details><summary>Solution</summary>

There are infinitely many normal curves, one for each μ and σ, but tables and normalcdf are set up for the single standard normal Z ~ N(0,1). The z-score converts any x to that common scale.

</details>

### Multiple Choice

**5.** If X is normally distributed with mean 50 and standard deviation 10, what is P(X < 50)?

- a) 0
- b) 0.25
- c) 0.50
- d) 1.00

<details><summary>Solution</summary>

The z-score is (50 − 50) / 10 = 0. A normal distribution is symmetric about its mean, so half the area lies below the mean.

**Final answer: c) 0.50**

</details>

**6.** For the data [3, 7, 12, 14, 15, 15, 19, 20, 21, 45], which statement is true?

- a) The mean is less than the median
- b) There are no outliers
- c) The mean is greater than the median
- d) The median is an outlier

<details><summary>Solution</summary>

Mean = 17.1 and median = 15. The large value 45 pulls the mean above the median.

**Final answer: c) The mean is greater than the median**

</details>
