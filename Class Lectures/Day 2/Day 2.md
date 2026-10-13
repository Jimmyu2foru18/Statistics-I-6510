# Statistics I, Day 2: Measures of Center, Dispersion, and Distribution

## Overview
Day 1 taught us how to *describe* data with pictures and categories. Today we summarize a quantitative data set with **numbers**: where is the center, and how spread out is it? These "summary statistics" let us compare distributions without listing every value.

---

## 1. Measures of Center (Central Tendency)

A **measure of center** is a single value meant to represent the "middle" or "typical" value of a data set.

### A. Mean (the average)

Sum every value, then divide by how many there are.

- **Sample mean** (our data is a *sample* of size $n$):
  $$\bar{x} = \frac{1}{n}\sum_{i=1}^{n} x_i$$
- **Population mean** (the whole *population* of size $N$):
  $$\mu = \frac{1}{N}\sum_{i=1}^{N} x_i$$

Here each $x_i$ is one observation, $n$ is the sample size, and $N$ is the population size.

### B. Median ($M$ or $Q_2$)

The **middle value** once the data are sorted from smallest to largest.
- If $n$ is **odd**, the median is the single middle value.
- If $n$ is **even**, the median is the **average of the two middle values**.

> The median is **resistant to outliers**: one extreme value barely moves it. The mean is *not* resistant.

### C. Mode

The **most frequent** value.
- There can be **more than one mode** if several values tie for most frequent.
- If every value appears the same number of times, there is **no mode**.

### D. Midrange

The value halfway between the extremes:
$$\text{Midrange} = \frac{\text{min} + \text{max}}{2}$$

> The midrange is very **sensitive to outliers** (like the mean), so it is used less often. We list it here because the class examples compute it.

---

## 2. Worked Example: Measures of Center

**Problem:** Find the mean, median, mode, and midrange of
$$[7, 3, 12, 15, 8, 19, 2, 12, 21, 18, 15, 10, 25, 6, 20]$$

**Sorted data** ($n = 15$):
$$[2, 3, 6, 7, 8, 10, 12, 12, 15, 15, 18, 19, 20, 21, 25]$$

1. **Mean:** $\displaystyle \bar{x} = \frac{193}{15} \approx 12.9$
2. **Median:** the 8th value of 15 → $M = 12$
3. **Mode:** $12$ and $15$ each appear twice → **bimodal**, mode $= \{12, 15\}$
4. **Midrange:** $\displaystyle \frac{2 + 25}{2} = 13.5$

---

## 3. Quartiles and Percentiles

- **Percentile:** the $p^{\text{th}}$ percentile is the value below which (or at) about $p\%$ of the data fall.
- **Quartiles** split the data into four equal parts:

| Symbol | Name | Meaning |
| :---: | :--- | :--- |
| $Q_1$ | First quartile ($25^{\text{th}}$ percentile) | 25% of the data are at or below this |
| $Q_2$ | Second quartile ($50^{\text{th}}$ percentile) | $=$ the **median** |
| $Q_3$ | Third quartile ($75^{\text{th}}$ percentile) | 75% of the data are at or below this |

### Worked Example: Quartiles

Using the sorted data above, split it at the median ($12$) and take the median of each half:

- Lower half: $[2, 3, 6, 7, 8, 10, 12]$ → $\;Q_1 = 7$
- Median: $Q_2 = 12$
- Upper half: $[15, 15, 18, 19, 20, 21, 25]$ → $\;Q_3 = 19$

> **Note on methods:** Quartiles have several standard conventions (here we *exclude* the median before averaging each half). Different tools/textbooks may give slightly different values for $Q_1, Q_3$ on the same data; see the note in **Day 3**. What matters is applying *one* method consistently.

---

## 4. Five-Number Summary and Boxplots

The **five-number summary** condenses a distribution into five values:

$$\text{Minimum} \;-\; Q_1 \;-\; \text{Median} \;-\; Q_3 \;-\; \text{Maximum}$$

A **box-and-whisker plot** (boxplot) is the picture of this summary: a box from $Q_1$ to $Q_3$, a line at the median, and "whiskers" out to the data range (with outliers plotted separately).

For our example the five-number summary is: $\;2, \;7, \;12, \;19, \;25$.

---

## 5. Interquartile Range (IQR) and Outlier Fences

- **IQR**: the spread of the middle 50% of data:
  $$IQR = Q_3 - Q_1$$
  For our example: $\;IQR = 19 - 7 = 12.$
  The IQR is **much less sensitive to outliers** than the full range.

- **Outlier fences** (the "$1.5 \times IQR$ rule"): a value is a suspected outlier if it lies beyond
  $$\text{Lower fence} = Q_1 - 1.5 \times IQR, \qquad \text{Upper fence} = Q_3 + 1.5 \times IQR$$
  For our example:
  $$\text{Lower} = 7 - 1.5(12) = -11, \qquad \text{Upper} = 19 + 1.5(12) = 37$$
  Every value ($2$ to $25$) is inside $[-11, 37]$, so **none are outliers**.

---

## 6. Measures of Variation / Dispersion

**Dispersion** measures describe how *spread out* the data are around the center.

| Measure | Formula | Our example |
| :--- | :--- | :--- |
| **Range** | $\text{max} - \text{min}$ | $25 - 2 = 23$ |
| **IQR** | $Q_3 - Q_1$ | $12$ |

### Variance, the average squared deviation from the mean

$$\text{(Population)} \; \sigma^2 = \frac{1}{N}\sum (x_i - \mu)^2
\qquad
\text{(Sample)} \; s^2 = \frac{1}{n-1}\sum (x_i - \bar{x})^2$$

> **Why $n-1$ for a sample?** Dividing by $n-1$ (instead of $n$) makes $s^2$ an **unbiased** estimate of the population variance $\sigma^2$. Look at the subscript: a **sample** statistic like $s^2$ uses $n-1$; a **population** parameter like $\sigma^2$ divides by $N$.

### Standard Deviation, square root of the variance

$$\sigma = \sqrt{\frac{1}{N}\sum (x_i-\mu)^2}
\qquad
s = \sqrt{\frac{1}{n-1}\sum (x_i-\bar{x})^2}$$

The standard deviation is in the **original units** of the data, so it is reported more often than the variance.

### Worked Example: Variance & Standard Deviation

**Problem:** Find the (sample) variance and standard deviation of $[3, 10, 12, 14, 21]$.

Mean: $\bar{x} = \frac{60}{5} = 12$.

| $x_i$ | $x_i - \bar{x}$ | $(x_i - \bar{x})^2$ |
| :---: | :---: | :---: |
| 3 | $3 - 12 = -9$ | 81 |
| 10 | $10 - 12 = -2$ | 4 |
| 12 | $12 - 12 = 0$ | 0 |
| 14 | $14 - 12 = 2$ | 4 |
| 21 | $21 - 12 = 9$ | 81 |
| | | **Total = 170** |

$$s^2 = \frac{170}{5 - 1} = \frac{170}{4} = 42.5
\qquad
s = \sqrt{42.5} \approx 6.52$$

*(If these five values were the entire population, we'd divide by $N=5$ instead: $\sigma^2 = 170/5 = 34$, $\sigma \approx 5.83$.)*

---

## 7. Bridging Concepts (preview of coming days)

These terms were introduced today and developed fully later:

- **Quantitative vs. Qualitative data**: quantitative = numerical amounts (continuous/discrete); qualitative = categories/labels (covered Day 1).
- **Density curve**: a smooth curve drawn through a histogram that represents the *overall pattern* of a distribution and the *probability* of falling in an interval (the total area under it is 1).
- **Normal distribution**: a specific symmetric, unimodal, bell-shaped density curve; the most important distribution in statistics.
- **Z-score**: how many standard deviations a value is from the mean:
  $$z = \frac{x - \mu}{\sigma}$$
  $z > 0$ is above the mean, $z < 0$ is below, and $|z|$ is the distance in standard deviations. We use $z$-scores heavily on **Day 3**.

---

## 8. Key Formulas

| Quantity | LaTeX | Plain / in words |
| :--- | :--- | :--- |
| Sample mean | $\bar{x}=\dfrac{1}{n}\sum x_i$ | (sum of all values) ÷ n |
| Population mean | $\mu=\dfrac{1}{N}\sum x_i$ | (sum of all values) ÷ N |
| Median $M$ | middle of sorted data | average the two middle values if $n$ even |
| Midrange | $\dfrac{\min+\max}{2}$ | (smallest + largest) ÷ 2 |
| Range | $\max-\min$ | largest − smallest |
| IQR | $Q_3-Q_1$ | third quartile − first quartile |
| Lower fence | $Q_1-1.5(\text{IQR})$ | Q1 minus 1.5 × IQR |
| Upper fence | $Q_3+1.5(\text{IQR})$ | Q3 plus 1.5 × IQR |
| Sample variance | $s^{2}=\dfrac{1}{n-1}\sum(x_i-\bar{x})^{2}$ | average squared deviation, ÷ (n−1) |
| Sample SD | $s=\sqrt{s^{2}}$ | square root of sample variance |
| Population variance | $\sigma^{2}=\dfrac{1}{N}\sum(x_i-\mu)^{2}$ | average squared deviation, ÷ N |
| $z$-score | $z=\dfrac{x-\mu}{\sigma}$ | (value − mean) ÷ SD |

---

## 9. Practice Problems

**1.** For $[4, 8, 6, 5, 3, 8, 9]$, find the mean, median, mode, and range.

<details><summary>Solution</summary>

Sum $=43$, so mean $=43/7 \approx 6.14$. Sorted: $[3,4,5,6,8,8,9]$; median $=6$ (middle of 7 values); mode $=8$; range $=9-3=6$.

</details>

**2.** Using the same data and the **median-exclusion** method, find $Q_1$, $Q_3$, and the IQR.

<details><summary>Solution</summary>

Exclude the median ($6$): lower half $[3,4,5] \Rightarrow Q_1=4$; upper half $[8,8,9] \Rightarrow Q_3=8$. IQR $=Q_3-Q_1=8-4=4$.

</details>

**3.** Find the sample standard deviation of $[2, 4, 4, 4, 5, 5, 7, 9]$ (round to 2 dp).

<details><summary>Solution</summary>

Mean $=40/8=5$. $\sum(x_i-\bar x)^2 = 9{+}1{+}1{+}1{+}0{+}0{+}4{+}16=32$. $s^2 = 32/(8-1) = 32/7 \approx 4.57$; $s \approx 2.14$.

</details>

**4.** A data set has $Q_1 = 20$, $Q_3 = 35$, min $=5$, max $=100$. Find the fences and flag any outliers.

<details><summary>Solution</summary>

IQR $=15$. Lower fence $=20-1.5(15)=-2.5$; upper fence $=35+1.5(15)=57.5$. Since $100>57.5$, **100 is an outlier**; $5$ is within $[-2.5, 57.5]$, so it is not.

</details>

**5.** For a distribution with $\mu = 50$ and $\sigma = 8$, find the $z$-score of $x = 62$ and interpret it.

<details><summary>Solution</summary>

$z=(62-50)/8=1.5$. The value is 1.5 standard deviations **above** the mean.

</details>

### Multiple Choice

**6.** Which measure of center is most resistant to a single extreme outlier?

- **a)** Mean
- **b)** Median
- **c)** Midrange
- **d)** Range

<details><summary>Solution</summary>

- The mean and the midrange both depend directly on the extreme value.
- The median uses only the middle position, so one outlier barely moves it.

**Final answer: (b) Median**

</details>

**7.** A data set has $Q_1 = 10$ and $Q_3 = 30$. Using the $1.5 \times \text{IQR}$ rule, the upper outlier fence is:

- **a)** 40
- **b)** 50
- **c)** 60
- **d)** 70

<details><summary>Solution</summary>

- $\text{IQR} = Q_3 - Q_1 = 30 - 10 = 20$.
- Upper fence $= Q_3 + 1.5 \times \text{IQR} = 30 + 1.5(20) = 30 + 30 = 60$.

**Final answer: (c) 60**

</details>
