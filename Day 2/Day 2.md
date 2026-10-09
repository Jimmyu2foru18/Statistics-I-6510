# Statistics I - Day 2 Notes: Measures of Center, Dispersion, and Distribution

## 1. Measures of Center (Central Tendency)
Measures of center give us a single value that attempts to describe a set of data by identifying the central position within that data set[cite: 1].

### A. Mean
The arithmetic average of a dataset[cite: 1].
* **Sample Mean**: 
  $$\bar{x} = \frac{1}{n}\sum_{i=1}^{n}x_i$$
  *(Where each $x_i$ is one observation in the sample, and $n$ is the sample size)*[cite: 1]
* **Population Mean**: 
  $$\mu = \frac{1}{N}\sum_{i=1}^{N}x_i$$
  *(Where each $x_i$ is one observation in the population, and $N$ is the population size)*[cite: 1]

### B. Median ($M$)
The middle value when all observations are placed in numerical order[cite: 1].
* If there are an even number of observations, it is halfway between the middle values[cite: 1].

### C. Mode
The most frequent value in a dataset[cite: 1].
* There can be multiple modes if there is a tie for what value appears most[cite: 1].
* If all values appear the same number of times, then there is no mode[cite: 1].

---

### Worked Example: Measures of Center
**Problem**: Find the mean, median, mode, and midrange of the following sample data[cite: 1]:
$$\text{Data: } [7, 3, 12, 15, 8, 19, 2, 12, 21, 18, 15, 10, 25, 6, 20]$$

1. **Mean**:
   $$\bar{x} = \frac{193}{15} = 12.9$$[cite: 1]

2. **Median**:
   Sorted data: $[2, 3, 6, 7, 8, 10, 12, 12, 15, 15, 18, 19, 20, 21, 25]$[cite: 1]
   $$\text{Median} = 12$$[cite: 1]

3. **Mode**:
   $$\text{Mode} = 12 \text{ and } 15$$[cite: 1]

4. **Midrange**:
   $$\text{Midrange} = \frac{\text{min} + \text{max}}{2} = \frac{2 + 25}{2} = 13.5$$[cite: 1]

---

## 2. Quartiles and Percentiles
* **Percentile**: The $n^{\text{th}}$ percentile for a distribution is the value that $n\%$ of the observations are less than or equal to[cite: 1].
* **Special Percentiles / Quartiles**:
  * $Q_1$ (First Quartile) $= 25\%$ of the data set[cite: 1]
  * $Q_2$ (Second Quartile) $= 50\%$ of the data set $=$ Median[cite: 1]
  * $Q_3$ (Third Quartile) $= 75\%$ of the data set[cite: 1]

### Worked Example: Quartiles
Using our sorted sample data[cite: 1]:
$$[2, 3, 6, 7, 8, 10, 12, 12, 15, 15, 18, 19, 20, 21, 25]$$
* $Q_1 = 7$[cite: 1]
* $Q_2 = 12$[cite: 1]
* $Q_3 = 19$[cite: 1]

---

## 3. Five-Number Summary and Boxplots
* **Five-Number Summary**: Minimum $\mid Q_1 \mid$ Median $\mid Q_3 \mid$ Maximum[cite: 1]
* **Box and Whisker Plot**: Graphical visualization of the five-number summary[cite: 1].

---

## 4. Interquartile Range (IQR) and Fences
* **IQR**:
  $$IQR = Q_3 - Q_1 = 19 - 7 = 12$$[cite: 1]
  *(Note: The IQR is less susceptible to outliers than the overall range.)*[cite: 1]
* **Outlier Fences**:
  * $\text{Lower Limit} = Q_1 - 1.5 \times IQR = 7 - 1.5 \times 12 = -11$[cite: 1]
  * $\text{Upper Limit} = Q_3 + 1.5 \times IQR = 19 + 1.5 \times 12 = 37$[cite: 1]

---

## 5. Measures of Variation / Dispersion
These tell us how spread out our data is in a distribution[cite: 1].
* **Range**: $\text{max} - \text{min} = 25 - 2 = 23$[cite: 1]

### Variance
Measure of the average squared deviation of observations from the mean[cite: 1].
* **Population Variance**: 
  $$\sigma^2 = \frac{1}{N}\sum_{i=1}^{N}(x_i - \mu)^2$$[cite: 1]
* **Sample Variance**: 
  $$s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(x_i - \bar{x})^2$$[cite: 1]

### Worked Example: Variance Calculation
**Problem**: Find the variance of the sample data: $[3, 10, 12, 14, 21]$[cite: 1]
* **Mean**: 
  $$\bar{x} = \frac{3 + 10 + 12 + 14 + 21}{5} = \frac{60}{5} = 12$$[cite: 1]

| $x_i$ | $x_i - \mu$ | $(x_i - \bar{x})^2$ |
| :---: | :---: | :---: |
| $3$ | $3 - 12 = -9$ | $81$ |[cite: 1]
| $10$ | $10 - 12 = -2$ | $4$ |[cite: 1]
| $12$ | $12 - 12 = 0$ | $0$ |[cite: 1]
| $14$ | $14 - 12 = 2$ | $4$ |[cite: 1]
| $21$ | $21 - 12 = 9$ | $81$ |[cite: 1]
| **Total** | | **170** |[cite: 1]

* **Sample Variance ($s^2$)**: 
  $$s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(x_i - \bar{x})^2 = \frac{170}{5-1} = \frac{170}{4} = 42.5$$[cite: 1]

### Standard Deviation
Square root of the variance[cite: 1].
* **Population Standard Deviation**: 
  $$\sigma = \sqrt{\frac{1}{N}\sum_{i=1}^{N}(x_i - \mu)^2}$$[cite: 1]
* **Sample Standard Deviation**: 
  $$s = \sqrt{\frac{1}{n-1}\sum_{i=1}^{n}(x_i - \bar{x})^2}$$[cite: 1]

---

## 6. General Concepts
* **Quantitative vs Qualitative Data**[cite: 1]
* **Density Curve**[cite: 1]
* **Normal Distribution**[cite: 1]
* **Z-Scores**[cite: 1]
