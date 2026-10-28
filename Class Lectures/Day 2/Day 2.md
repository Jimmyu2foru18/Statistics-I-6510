# Statistics I, Day 2: Measures of Center, Dispersion, and Distribution

Welcome to Day 2! Day 1 taught us how to describe data with pictures and categories. Today we take the next step: we summarize a quantitative data set with numbers. Where is the center? How spread out is it? These summary statistics let us compare distributions without having to list every single value.

---

## 1. Measures of Center (Central Tendency)

A **measure of center** is a single value meant to represent the "middle" or "typical" value of a data set. It is our best one-number summary of where the data tend to cluster.

### A. Mean (the average)

The mean is what most people mean when they say "average." You sum up every value and then divide by how many values there are.

- **Sample mean** (our data is a sample of size n):
  x̄ = (1/n) × Σxᵢ
- **Population mean** (the whole population of size N):
  μ = (1/N) × Σxᵢ

Here each xᵢ is one observation, n is the sample size, and N is the population size.

### B. Median (M or Q₂)

The **median** is the middle value once the data are sorted from smallest to largest.
- If n is **odd**, the median is the single middle value.
- If n is **even**, the median is the average of the two middle values.

The median is **resistant to outliers**: one extreme value barely moves it. The mean is **not** resistant, so a single huge or tiny value can pull the mean away from the center.

### C. Mode

The **mode** is the most frequent value.
- There can be **more than one mode** if several values tie for most frequent.
- If every value appears the same number of times, there is **no mode**.

### D. Midrange

The **midrange** is the value halfway between the smallest and largest observations:
Midrange = (min + max) / 2

The midrange is very sensitive to outliers, like the mean, so it is used less often. We list it here because the class examples compute it.

---

## 2. Worked Example: Measures of Center

**Problem:** Find the mean, median, mode, and midrange of
[7, 3, 12, 15, 8, 19, 2, 12, 21, 18, 15, 10, 25, 6, 20]

First, sort the data (n = 15):
[2, 3, 6, 7, 8, 10, 12, 12, 15, 15, 18, 19, 20, 21, 25]

**1. Mean:**
x̄ = 193 / 15 ≈ 12.9

**2. Median:** The 8th value of 15 is M = 12.

**3. Mode:** The values 12 and 15 each appear twice, so this is **bimodal**, and the mode is {12, 15}.

**4. Midrange:**
(2 + 25) / 2 = 13.5

---

## 3. Quartiles and Percentiles

A **percentile** is the value below which (or at) about p percent of the data fall. For example, the 90th percentile is the value below which about 90 percent of observations fall.

**Quartiles** split the data into four equal parts:

| Symbol | Name | Meaning |
| :--- | :--- | :--- |
| Q₁ | First quartile (25th percentile) | 25% of the data are at or below this |
| Q₂ | Second quartile (50th percentile) | This equals the median |
| Q₃ | Third quartile (75th percentile) | 75% of the data are at or below this |

### Worked Example: Quartiles

Using the sorted data from earlier, split it at the median (12) and take the median of each half:

- Lower half: [2, 3, 6, 7, 8, 10, 12] → Q₁ = 7
- Median: Q₂ = 12
- Upper half: [15, 15, 18, 19, 20, 21, 25] → Q₃ = 19

**Note on methods:** Different textbooks and tools use slightly different conventions for quartiles. Here we exclude the median before averaging each half. Other methods may give slightly different values for Q₁ and Q₃ on the same data. What matters is applying one method consistently and knowing which one your tools use.

---

## 4. Five-Number Summary and Boxplots

The **five-number summary** condenses a distribution into five values:

Minimum − Q₁ − Median − Q₃ − Maximum

A **box-and-whisker plot** (boxplot) is the picture of this summary: a box from Q₁ to Q₃, a line at the median, and "whiskers" extending out to the data range, with any outliers plotted separately.

For our example, the five-number summary is: 2, 7, 12, 19, 25.

---

## 5. Interquartile Range (IQR) and Outlier Fences

The **IQR** measures the spread of the middle 50 percent of the data:
IQR = Q₃ − Q₁

For our example: IQR = 19 − 7 = 12.

The IQR is much less sensitive to outliers than the full range because it ignores the extreme tails.

**Outlier fences** use the "1.5 × IQR rule." A value is a suspected outlier if it lies beyond:
Lower fence = Q₁ − 1.5 × IQR
Upper fence = Q₃ + 1.5 × IQR

For our example:
Lower fence = 7 − 1.5(12) = −11
Upper fence = 19 + 1.5(12) = 37

Every value from 2 to 25 is inside [−11, 37], so none are outliers.

---

## 6. Measures of Variation / Dispersion

**Dispersion** measures describe how spread out the data are around the center.

| Measure | Formula | Our example |
| :--- | :--- | :--- |
| Range | max − min | 25 − 2 = 23 |
| IQR | Q₃ − Q₁ | 12 |

### Variance: the average squared deviation from the mean

Variance measures how far, on average, each value is from the mean, but in squared units.

Population variance:
σ² = (1/N) × Σ(xᵢ − μ)²

Sample variance:
s² = (1/(n−1)) × Σ(xᵢ − x̄)²

**Why n−1 for a sample?** Dividing by n−1 instead of n makes s² an **unbiased** estimate of the population variance σ². A sample statistic like s² uses n−1, while a population parameter like σ² divides by N.

### Standard Deviation: square root of the variance

The standard deviation is simply the square root of the variance:

σ = √[(1/N) × Σ(xᵢ − μ)²]
s = √[(1/(n−1)) × Σ(xᵢ − x̄)²]

The standard deviation is in the original units of the data, so it is reported more often than the variance.

### Worked Example: Variance and Standard Deviation

**Problem:** Find the sample variance and standard deviation of [3, 10, 12, 14, 21].

Mean: x̄ = 60 / 5 = 12.

| xᵢ | xᵢ − x̄ | (xᵢ − x̄)² |
| :---: | :---: | :---: |
| 3 | 3 − 12 = −9 | 81 |
| 10 | 10 − 12 = −2 | 4 |
| 12 | 12 − 12 = 0 | 0 |
| 14 | 14 − 12 = 2 | 4 |
| 21 | 21 − 12 = 9 | 81 |
| | **Total = 170** | |

s² = 170 / (5 − 1) = 170 / 4 = 42.5
s = √42.5 ≈ 6.52

If these five values were the entire population, we would divide by N = 5 instead: σ² = 170/5 = 34, and σ ≈ 5.83.

---

## 7. Bridging Concepts (preview of coming days)

These terms were introduced today and will be developed fully later:

- **Quantitative vs. Qualitative data:** Quantitative means numerical amounts (continuous or discrete). Qualitative means categories or labels, covered on Day 1.
- **Density curve:** a smooth curve drawn through a histogram that represents the overall pattern of a distribution and the probability of falling in an interval. The total area under it equals 1.
- **Normal distribution:** a specific symmetric, unimodal, bell-shaped density curve. It is the most important distribution in statistics.
- **Z-score:** how many standard deviations a value is from the mean:
  z = (x − μ) / σ
  z > 0 means above the mean, z < 0 means below, and |z| is the distance in standard deviations. We use z-scores heavily on Day 3.

---

## 8. Key Formulas

| Quantity | Formula | Plain meaning |
| :--- | :--- | :--- |
| Sample mean | x̄ = (1/n)Σxᵢ | Sum of all values divided by n |
| Population mean | μ = (1/N)Σxᵢ | Sum of all values divided by N |
| Median M | Middle of sorted data | Average the two middle values if n is even |
| Midrange | (min + max) / 2 | Smallest plus largest, divided by 2 |
| Range | max − min | Largest minus smallest |
| IQR | Q₃ − Q₁ | Third quartile minus first quartile |
| Lower fence | Q₁ − 1.5(IQR) | Q1 minus 1.5 times the IQR |
| Upper fence | Q₃ + 1.5(IQR) | Q3 plus 1.5 times the IQR |
| Sample variance | s² = (1/(n−1))Σ(xᵢ − x̄)² | Average squared deviation, divided by n−1 |
| Sample SD | s = √s² | Square root of the sample variance |
| Population variance | σ² = (1/N)Σ(xᵢ − μ)² | Average squared deviation, divided by N |
| z-score | z = (x − μ) / σ | Value minus mean, divided by SD |

---

## 9. Practice Problems

**1.** For [4, 8, 6, 5, 3, 8, 9], find the mean, median, mode, and range.

<details><summary>Solution</summary>

Sum = 43, so mean = 43/7 ≈ 6.14. Sorted: [3, 4, 5, 6, 8, 8, 9]. Median = 6 (the middle of 7 values). Mode = 8. Range = 9 − 3 = 6.

</details>

**2.** Using the same data and the median-exclusion method, find Q₁, Q₃, and the IQR.

<details><summary>Solution</summary>

Exclude the median (6): lower half [3, 4, 5] → Q₁ = 4; upper half [8, 8, 9] → Q₃ = 8. IQR = Q₃ − Q₁ = 8 − 4 = 4.

</details>

**3.** Find the sample standard deviation of [2, 4, 4, 4, 5, 5, 7, 9] (round to 2 dp).

<details><summary>Solution</summary>

Mean = 40/8 = 5. Σ(xᵢ − x̄)² = 9 + 1 + 1 + 1 + 0 + 0 + 4 + 16 = 32. s² = 32/(8−1) = 32/7 ≈ 4.57; s ≈ 2.14.

</details>

**4.** A data set has Q₁ = 20, Q₃ = 35, min = 5, max = 100. Find the fences and flag any outliers.

<details><summary>Solution</summary>

IQR = 15. Lower fence = 20 − 1.5(15) = −2.5. Upper fence = 35 + 1.5(15) = 57.5. Since 100 > 57.5, 100 is an outlier. The value 5 is within [−2.5, 57.5], so it is not an outlier.

</details>

**5.** For a distribution with μ = 50 and σ = 8, find the z-score of x = 62 and interpret it.

<details><summary>Solution</summary>

z = (62 − 50) / 8 = 1.5. The value is 1.5 standard deviations above the mean.

</details>

### Multiple Choice

**6.** Which measure of center is most resistant to a single extreme outlier?

- a) Mean
- b) Median
- c) Midrange
- d) Range

<details><summary>Solution</summary>

The mean and midrange both depend directly on the extreme value. The median uses only the middle position, so one outlier barely moves it.

**Final answer: b) Median**

</details>

**7.** A data set has Q₁ = 10 and Q₃ = 30. Using the 1.5 × IQR rule, the upper outlier fence is:

- a) 40
- b) 50
- c) 60
- d) 70

<details><summary>Solution</summary>

IQR = Q₃ − Q₁ = 30 − 10 = 20. Upper fence = Q₃ + 1.5 × IQR = 30 + 1.5(20) = 30 + 30 = 60.

**Final answer: c) 60**

</details>
