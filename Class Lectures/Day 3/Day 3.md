# Statistics I, Day 3: Descriptive Statistics & the Normal Distribution

## Overview
Today ties everything from Days 1–2 together into one **end-to-end descriptive-statistics problem**, then introduces the **normal distribution** and how to compute probabilities with **Z-scores**.

---

## Part A: A Complete Descriptive-Statistics Problem

**Problem:** For the sample data below, find the mean, median, mode, midrange, range, variance, standard deviation, quartiles, interquartile range, and the upper and lower fences. Decide whether any observation is an outlier.

$$[3, 7, 12, 14, 15, 15, 19, 20, 21, 45] \qquad (n = 10)$$

The data are already sorted.

### 1. Measures of Center and Location

- **Mean:**
  $$\bar{x} = \frac{3+7+12+14+15+15+19+20+21+45}{10} = \frac{171}{10} = 17.1$$

- **Median ($Q_2$):** $n$ is even, so average the 5th and 6th values (both $15$):
  $$M = 15$$

- **Mode:** the only repeated value is $15$ (twice) → $\text{mode} = 15$

- **Midrange:**
  $$\frac{\min + \max}{2} = \frac{3 + 45}{2} = 24$$

### 2. Measures of Variation and Spread

- **Range:** $\;45 - 3 = 42$

- **Quartiles** (using the *linear-interpolation* method, see note below):

| Quartile | Position of rank | Value |
| :---: | :--- | :---: |
| $Q_1$ ($25^{\text{th}}$) | $(n{-}1)(0.25)+1 = 3.25$ | $12 + 0.25(14-12) = 12.5$ |
| $Q_2$ (median) |  | $15$ |
| $Q_3$ ($75^{\text{th}}$) | $(n{-}1)(0.75)+1 = 7.75$ | $19 + 0.75(20-19) = 19.75$ |
| $Q_4$ (max) |  | $45$ |

- **Interquartile Range:**
  $$IQR = Q_3 - Q_1 = 19.75 - 12.5 = 7.25$$

- **Outlier fences:**
  $$\text{Lower} = Q_1 - 1.5(IQR) = 12.5 - 1.5(7.25) = 1.625$$
  $$\text{Upper} = Q_3 + 1.5(IQR) = 19.75 + 1.5(7.25) = 30.625$$
  Since $45 > 30.625$, the value **$45$ is an outlier**. Nothing is below $1.625$.

- **Sample variance:**
  $$s^2 = \frac{\sum (x_i - \bar{x})^2}{n-1} = \frac{1150.9}{9} \approx 127.88$$

- **Sample standard deviation:**
  $$s = \sqrt{127.88} \approx 11.31$$

> **Note: quartile conventions differ.** On Day 2 ($n=15$) we got $Q_1=7$, $Q_3=19$ by *excluding the median and averaging each half*. Here ($n=10$) the values $12.5$ and $19.75$ come from *linear interpolation*. Both are correct under their own convention, which is exactly why **calculators, software, and textbooks can report slightly different quartiles for the same data**. Always apply one method consistently and know which one your tools use.

### Summary of Results

| Statistic | Value |
| :--- | ---: |
| Mean | $17.1$ |
| Median | $15$ |
| Mode | $15$ |
| Midrange | $24$ |
| Range | $42$ |
| $Q_1$ | $12.5$ |
| $Q_2$ (median) | $15$ |
| $Q_3$ | $19.75$ |
| IQR | $7.25$ |
| Lower fence / Upper fence | $1.625$ / $30.625$ |
| Sample variance $s^2$ | $\approx 127.88$ |
| Sample std. dev. $s$ | $\approx 11.31$ |
| Outlier? | **Yes, $45$** |

---

## Part B: Normal-Distribution Probability Applications

Suppose a variable $X$ is approximately **normal** with mean $\mu = 8.5$ and standard deviation $\sigma = 2.3$:
$$X \sim N(8.5, 2.3)$$

Because there are infinitely many normal distributions, we **standardize** every value to a **$z$-score**, which converts $X$ to the *standard normal* $Z \sim N(0,1)$:
$$z = \frac{x - \mu}{\sigma}$$

We then read the probability $P(Z < z)$ from the standard-normal table (area to the left of $z$) or a calculator.

### A. Proportion less than $7.5$

1. Standardize: $\displaystyle z = \frac{7.5 - 8.5}{2.3} = \frac{-1.0}{2.3} \approx -0.4348$
2. Look up the cumulative area:
   $$P(X < 7.5) = P(Z < -0.4348) \approx 0.3319 \;\; (33.19\%)$$

### B. Proportion greater than $10.1$

1. Standardize: $\displaystyle z = \frac{10.1 - 8.5}{2.3} = \frac{1.6}{2.3} \approx 0.6957$
2. Use the complement (tables give area to the *left*, so subtract from 1):
   $$P(X > 10.1) = 1 - P(Z < 0.6957) \approx 1 - 0.7567 = 0.2433 \;\; (24.33\%)$$

### C. Proportion between $7.5$ and $10.1$

Take the difference of the two cumulative areas:
$$P(7.5 < X < 10.1) = P(Z < 0.6957) - P(Z < -0.4348) \approx 0.7567 - 0.3319 = 0.4248 \;\; (42.48\%)$$

### Tips for Normal Calculations

- Always convert to a **$z$-score first**.
- The standard-normal table gives area to the **left** ($<$). For a **right tail** ($>$), use $1 - (\text{left area})$.
- For an **interval**, subtract the smaller cumulative area from the larger one.
- Check plausibility: our three answers add the expected way, $0.3319 + 0.4248 + 0.2433 = 1.000$.

---

## Key Formulas

| Quantity | Formula | Plain / in words |
| :--- | :--- | :--- |
| Mean | $\bar{x}=\dfrac{\sum x_i}{n}$ | sum ÷ count |
| Median | middle value | average two middle values if $n$ even |
| Mode | most frequent value | value appearing most often |
| Midrange | $\dfrac{\min+\max}{2}$ | (min + max) ÷ 2 |
| Range | $\max-\min$ | largest − smallest |
| $Q_1, Q_3$ (linear interp.) | rank $(n{-}1)p$ | value at the 25% / 75% position |
| IQR | $Q_3-Q_1$ | middle-50% spread |
| Fences | $Q_{1}-1.5\,\text{IQR},\; Q_{3}+1.5\,\text{IQR}$ | quartiles minus/plus 1.5 × IQR |
| Sample variance / SD | $s^{2}=\dfrac{\sum(x_i-\bar x)^2}{n-1};\; s=\sqrt{s^2}$ | avg sq. deviation ÷ (n−1); its square root |
| $z$-score | $z=\dfrac{x-\mu}{\sigma}$ | (value − mean) ÷ SD |
| Normal probability | $P(a<X<b)=P(z_a<Z<z_b)$ | difference of two cumulative areas |

---

## Practice Problems

**1.** For $[4, 6, 7, 9, 10, 12, 40]$, find: mean, median, mode, range, $Q_1$, $Q_3$, IQR, the outlier fences (linear-interpolation quartiles), sample SD, and flag any outlier.

<details><summary>Solution</summary>

Mean $=88/7 \approx 12.57$; median $=9$; **no mode**; range $=40-4=36$. Linear-interp. quartiles: $Q_1=6.5$, $Q_3=11$, IQR $=4.5$. Fences: lower $=6.5-1.5(4.5)=-0.25$; upper $=11+1.5(4.5)=17.75$. Since $40>17.75$, **40 is an outlier**; nothing below $-0.25$. Sample SD: $s^2 \approx 153.29$, so $s\approx 12.38$.

</details>

**2.** In problem 1, which summary statistic is most affected by the outlier ($40$) and which is least? Explain.

<details><summary>Solution</summary>

Most affected: **mean** ($12.57$) and **standard deviation/range**, which shoot up. Least affected: **median** ($9$) and the **IQR** ($4.5$); these are *resistant* to outliers.

</details>

**3.** Let $X \sim N(50, 10)$. Find (a) $P(X<40)$, (b) $P(X>65)$, (c) $P(40<X<65)$.

<details><summary>Solution</summary>

(a) $z=(40-50)/10=-1 \Rightarrow P\approx0.1587$; (b) $z=(65-50)/10=1.5 \Rightarrow P(Z>1.5)\approx0.0668$; (c) $0.9332-0.1587=0.7745$.

</details>

**4.** Why do we convert to a $z$-score before using the standard-normal table?

<details><summary>Solution</summary>

There are infinitely many normal curves (one for each $\mu,\sigma$), but tables/`normalcdf` are set up for the single **standard** normal $Z\sim N(0,1)$. The $z$-score converts any $x$ to that common scale.

</details>

### Multiple Choice

**5.** If $X$ is normally distributed with mean $50$ and standard deviation $10$, what is $P(X < 50)$?

- **a)** 0
- **b)** 0.25
- **c)** 0.50
- **d)** 1.00

<details><summary>Solution</summary>

- The $z$-score is $(50 - 50)/10 = 0$.
- A normal distribution is symmetric about its mean, so half the area lies below the mean.

**Final answer: (c) 0.50**

</details>

**6.** For the data $[3, 7, 12, 14, 15, 15, 19, 20, 21, 45]$, which statement is true?

- **a)** The mean is less than the median
- **b)** There are no outliers
- **c)** The mean is greater than the median
- **d)** The median is an outlier

<details><summary>Solution</summary>

- Mean $= 17.1$ and median $= 15$.
- The large value $45$ pulls the mean above the median.

**Final answer: (c) The mean is greater than the median**

</details>
