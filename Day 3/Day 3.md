# Statistics I - Day 3 Notes: Comprehensive Descriptive Statistics & Normal Distribution

## 1. Comprehensive Problem Walkthrough
**Problem**: Find the mean, median, mode, midrange, range, variance, standard deviation, quartiles, interquartile range, and upper and lower fences for the following sample data. Determine whether any of the observations are outliers[cite: 3].
$$\text{Data: } [3, 7, 12, 14, 15, 15, 19, 20, 21, 45]$$

### A. Measures of Center and Location
* **Mean ($\bar{x}$)**: 
  $$\bar{x} = \frac{\sum x_i}{n} = \frac{3 + 7 + 12 + 14 + 15 + 15 + 19 + 20 + 21 + 45}{10} = \frac{171}{10} = 17.1$$[cite: 3]

* **Median ($M$ or $Q_2$)**:
  Since $n = 10$ (even), the median is the average of the 5th and 6th sorted values ($15$ and $15$):
  $$M = 15.0$$[cite: 3]

* **Mode**:
  The most frequent value in the dataset is $15$ (appearing twice):
  $$\text{Mode} = 15$$[cite: 3]

* **Midrange**:
  $$\text{Midrange} = \frac{\text{Minimum} + \text{Maximum}}{2} = \frac{3 + 45}{2} = \frac{48}{2} = 24.0$$[cite: 3]

---

### B. Measures of Variation and Spread
* **Range**:
  $$\text{Range} = \text{Maximum} - \text{Minimum} = 45 - 3 = 42$$[cite: 3]

* **Quartiles**:
  * $Q_1$ (First Quartile / 25th percentile): $12.5$[cite: 3]
  * $Q_2$ (Second Quartile / Median): $15.0$[cite: 3]
  * $Q_3$ (Third Quartile / 75th percentile): $19.75$[cite: 3]
  * $Q_4$ (Maximum): $45$[cite: 3]

* **Interquartile Range ($IQR$)**:
  $$IQR = Q_3 - Q_1 = 19.75 - 12.5 = 7.25$$[cite: 3]

* **Fences and Outliers**:
  * $\text{Lower Fence} = Q_1 - 1.5 \times IQR = 12.5 - 1.5 \times (7.25) = 12.5 - 10.875 = 1.625$[cite: 3]
  * $\text{Upper Fence} = Q_3 + 1.5 \times IQR = 19.75 + 1.5 \times (7.25) = 19.75 + 10.875 = 30.625$[cite: 1, 3]
  * **Outliers**: Any observation below $1.625$ or above $30.625$ is an outlier. Therefore, **$45$** is an outlier[cite: 3].

* **Sample Variance ($s^2$)**:
  $$s^2 = \frac{\sum (x_i - \bar{x})^2}{n - 1} \approx 127.88$$[cite: 3]

* **Sample Standard Deviation ($s$)**:
  $$s = \sqrt{127.88} \approx 11.31$$[cite: 3]

---

## 2. Normal Distribution Probability Applications
**Problem**: The distribution of a dataset is approximately normal with a mean of $\mu = 8.5$ and standard deviation of $\sigma = 2.3$. What proportion of observations do we expect to be[cite: 3]?

### A. Less than 7.5
1. Calculate the Z-score for $x = 7.5$:
   $$z = \frac{x - \mu}{\sigma} = \frac{7.5 - 8.5}{2.3} = \frac{-1.0}{2.3} \approx -0.4348$$[cite: 1, 3]
2. Find the cumulative proportion using the standard normal distribution table or calculator:
   $$P(X < 7.5) \approx 0.3319 \text{ (or } 33.19\%)$$[cite: 3]

### B. Greater than 10.1
1. Calculate the Z-score for $x = 10.1$:
   $$z = \frac{10.1 - 8.5}{2.3} = \frac{1.6}{2.3} \approx 0.6957$$[cite: 1, 3]
2. Find the upper-tail proportion:
   $$P(X > 10.1) = 1 - P(Z < 0.6957) \approx 1 - 0.7567 = 0.2433 \text{ (or } 24.33\%)$$[cite: 3]

### C. Between 7.5 and 10.1
1. Subtract the lower cumulative probability from the upper cumulative probability:
   $$P(7.5 < X < 10.1) = P(Z < 0.6957) - P(Z < -0.4348)$$[cite: 3]
   $$P(7.5 < X < 10.1) \approx 0.7567 - 0.3319 = 0.4248 \text{ (or } 42.48\%)$$[cite: 3]
