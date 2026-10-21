# Statistics I, Day 8: Normal Calculations, Confidence Intervals, and Hypothesis Testing

## Overview
Day 7 built the machinery of **sampling distributions** and the **Central Limit Theorem**. Today we finally *use* it for formal inference. The lecture has five strands:
1. **Normal calculations** — $z$-scores, percentiles, and the normal approximation to the binomial (Problems 1–2).
2. The **sampling distribution of a sample proportion** $\hat{p}$ (Problem 3).
3. **Confidence intervals for a population mean** — the *Z-Interval for $\mu$*.
4. **Hypothesis testing** — the classical (critical value) method and the $p$-value method.
5. The **Z-test for $\mu$**, and the fact that a confidence interval and a two-sided test are two views of the *same* question.

*Source cross-checked against the course slides (Moore/McCabe/Craig, Ch. 5 "Sampling Distributions" and Ch. 6 "Introduction to Inference") and the course standard-normal table.*

---

## Part A: Normal Calculations with Z-Scores (Problem 1: Tree Heights)

### The Setup

The heights of trees of a certain species are normally distributed with a mean of 25 ft and a standard deviation of 3 ft:
$$X \sim N(25,\ 3)$$

Let $X$ be the height of a **randomly selected tree**, and let $\bar{X}$ be the mean height of a **random sample of 10 trees**.

These are two different random variables, with two different distributions. The single tree is *wide* (SD = 3 ft); the average of 10 trees is *narrow* (SD = $3/\sqrt{10} \approx 0.9487$ ft):

| Random variable | What it is | Mean | Standard deviation | Distribution |
| :--- | :--- | :---: | :---: | :--- |
| $X$ | height of **one** tree | $\mu = 25$ | $\sigma = 3$ | $N(25,\ 3)$ |
| $\bar{X}$ | mean height of **10** trees | $\mu_{\bar{X}} = 25$ | $\sigma_{\bar{X}} = \dfrac{3}{\sqrt{10}} \approx 0.9487$ | $\approx N(25,\ 0.9487)$ |

> **Why $\bar{X}$ is Normal here even though $n = 10 < 30$:** the CLT only needs $n \ge 30$ when the *population* is not Normal. Here the population **is** exactly Normal, so the sampling distribution of $\bar{X}$ is Normal for *any* $n$.

### (a) Find $P(X < 26)$

1. **Standardize:** $\displaystyle z = \frac{26 - 25}{3} = \frac{1}{3} \approx 0.33$
2. **Read the area to the left of $z$** from the $Z$-table:
   $$P(X < 26) = P(Z < 0.33) = 0.6293$$
   (With the unrounded $z = 0.3333$, the exact value is $0.6306$.)

### (b) Find $P(X > 27)$

1. **Standardize:** $\displaystyle z = \frac{27 - 25}{3} = \frac{2}{3} \approx 0.67$
2. The table gives the area to the **left**, so use the complement:
   $$P(X > 27) = 1 - P(Z < 0.67) = 1 - 0.7486 = 0.2514$$
   (With the unrounded $z = 0.6667$, the exact value is $0.2525$.)

### (c) Find the 90th Percentile Height

A **$p^{\text{th}}$ percentile** is the value $x$ such that $P(X < x) = p$. Here we want $P(X < x) = 0.90$, so we must *invert* the standard-normal table:

1. **Find the $z$-score with 0.90 of the area to its left:** $z = 1.2816$
2. **Convert back to $x$** using $x = \mu + z\sigma$:
   $$x = 25 + (1.2816)(3) = 25 + 3.8448 = 28.8448 \approx 28.84 \text{ ft}$$

So **90% of the trees are shorter than 28.84 ft** and 10% are taller.

### (d) Find $P(\bar{X} < 26)$

Now the standard error of the mean is used instead of $\sigma$:
$$\sigma_{\bar{X}} = \frac{\sigma}{\sqrt{n}} = \frac{3}{\sqrt{10}} \approx 0.9487$$

1. **Standardize:** $\displaystyle z = \frac{26 - 25}{0.9487} = \frac{1}{0.9487} \approx 1.05$
2. **Read the area:**
   $$P(\bar{X} < 26) = P(Z < 1.05) = 0.8531$$
   (With the unrounded $z = 1.0541$, the exact value is $0.8541$.)

### (e) Find $P(\bar{X} > 27)$

1. **Standardize:** $\displaystyle z = \frac{27 - 25}{0.9487} = \frac{2}{0.9487} \approx 2.11$
2. **Complement:**
   $$P(\bar{X} > 27) = 1 - P(Z < 2.11) = 1 - 0.9826 = 0.0174$$
   (With the unrounded $z = 2.1082$, the exact value is $0.0175$.)

### Why (d)–(e) Look So Different From (a)–(b)

Compare the same two questions about a *single* tree versus the *average of ten*:

| Question | About one tree ($X$) | About the average of 10 ($\bar{X}$) |
| :--- | :---: | :---: |
| $P(\text{less than } 26)$ | $0.6293$ | $0.8531$ |
| $P(\text{more than } 27)$ | $0.2514$ | $0.0174$ |

Averages are **less variable** than individuals: the SD shrinks by a factor of $\sqrt{n}$, so $\bar{X}$ hugs 25 much more tightly than a single tree does. A sample mean of 27 is a much rarer event than a single tree of 27 ft.

### Calculator Commands

- `normalcdf(lower, upper, μ, σ)` — probability between two values (use $-1\text{E99}$ and $1\text{E99}$ for tails).
- `normalcdf(26, 1E99, 25, 3)` — part (a).
- `invNorm(area, μ, σ)` — the percentile command behind part (c): `invNorm(0.90, 25, 3) = 28.845`.

---

## Part B: Normal Approximation to the Binomial (Problem 2)

**Problem:** In a city with many residents, 20% of people own a car. Let $X$ be the number of people in a random sample of 200 residents of this city who own a car. Use the normal approximation to the binomial distribution to approximate the probability that $X$ is greater than 45.

### Step 1: Confirm $X$ Is Binomial

Check **BINS**: **B**inary (owns a car / doesn't), **I**ndependent (the city is large), **N**umber of trials fixed ($n = 200$), **S**uccess probability constant ($p = 0.20$). So:
$$X \sim \text{Binomial}(200,\ 0.20)$$

### Step 2: Check the Normal-Approximation Conditions

$$np = 200(0.20) = 40 \ge 10 \qquad\text{and}\qquad n(1-p) = 200(0.80) = 160 \ge 10 \quad\checkmark$$

Both expected counts are large, so the normal approximation is legitimate. *(Some editions use $np \ge 5$ and $nq \ge 5$; the $\ge 10$ rule is the one used in this course.)*

### Step 3: Find the Mean and SD of the Approximating Normal

$$\mu = np = 40, \qquad \sigma = \sqrt{np(1-p)} = \sqrt{(200)(0.20)(0.80)} = \sqrt{32} \approx 5.6569$$

### Step 4: Apply the Continuity Correction

The binomial is **discrete** and the normal is **continuous**, so "more than 45" must be stretched to include the whole bar at 45:
$$P(X > 45) \approx P(Y > 45.5) \qquad (Y \sim N(40,\ 5.6569))$$

### Step 5: Standardize and Finish

$$z = \frac{45.5 - 40}{5.6569} = \frac{5.5}{5.6569} \approx 0.97$$
$$P(X > 45) \approx P(Z > 0.97) = 1 - 0.8340 = 0.1660$$

*(The exact binomial answer is $P(X > 45) = 1 - \texttt{binomcdf}(200, 0.20, 45) \approx 0.1651$ — a very close match.)*

### Why the Continuity Correction Matters

Without it we would use $z = (45 - 40)/5.6569 \approx 0.88$, giving $P \approx 0.1884$ instead of $0.1660$. The correction is not a small technicality here: it is the difference between about 19% and about 17%. The general rule (recap from Day 7) is:

| Binomial (discrete) | Normal (continuous) approximation |
| :--- | :--- |
| $P(X = a)$ | $P(a - 0.5 < X < a + 0.5)$ |
| $P(X \le a)$ | $P(X < a + 0.5)$ |
| $P(X < a)$ | $P(X < a - 0.5)$ |
| $P(X \ge a)$ | $P(X > a - 0.5)$ |
| $P(X > a)$ | $P(X > a + 0.5)$ |

---

## Part C: The Sampling Distribution of a Sample Proportion (Problem 3)

**Problem:** Suppose that 70% of students on a college campus are satisfied with the food on campus. You take a random sample of 50 students from this campus. Let $\hat{p}$ be the proportion of students in your sample who are satisfied with the food.

### The Conditions

By the CLT, $\hat{p}$ is approximately Normal when the population is large, the sample is random, and the expected number of successes and failures are both at least 10:
$$np = 50(0.70) = 35 \ge 10, \qquad n(1-p) = 50(0.30) = 15 \ge 10 \quad\checkmark$$

### (a) Find the Mean and Standard Deviation of $\hat{p}$

$$\mu_{\hat{p}} = p = 0.70$$
$$\sigma_{\hat{p}} = \sqrt{\frac{p(1-p)}{n}} = \sqrt{\frac{(0.70)(0.30)}{50}} = \sqrt{0.0042} \approx 0.0648$$

This is the **standard error of a proportion**: the SD of the sampling distribution of $\hat{p}$.

### (b) Find $P(\hat{p} < 0.75)$

1. **Standardize:** $\displaystyle z = \frac{0.75 - 0.70}{0.0648} = 0.7715 \approx 0.77$
2. **Read the area:**
   $$P(\hat{p} < 0.75) = P(Z < 0.77) = 0.7794$$

### (c) Find $P(0.5 < \hat{p} < 0.8)$

1. **Standardize both ends:**
   $$z_1 = \frac{0.50 - 0.70}{0.0648} \approx -3.09, \qquad z_2 = \frac{0.80 - 0.70}{0.0648} \approx 1.54$$
2. **Subtract the cumulative areas:**
   $$P(0.5 < \hat{p} < 0.8) = P(Z < 1.54) - P(Z < -3.09) = 0.9382 - 0.0010 = 0.9372$$

### What the Answers Mean

Roughly **94%** of all random samples of 50 students will fall between 50% and 80% satisfied. The sample proportion is pinned tightly around $0.70$ (SE $\approx 0.065$), so it takes an unusual sample to land as low as 0.50 (more than 3 standard deviations away).

---

## Part D: Confidence Intervals for a Population Mean (Z-Interval for $\mu$)

### What a Confidence Interval Is

A **confidence interval** has two parts:

1. An **interval** computed from the data, with the form $\text{estimate} \pm \text{margin of error}$.
2. A **confidence level $C$**, the *capture rate* of the method: if we took every possible sample of size $n$ and made an interval from each one, $C \times 100\%$ of those intervals would contain the true parameter.

### The Formula and Its Parts

$$\text{CI for }\mu = \bar{x} \pm z^{*}_{\alpha/2}\cdot\frac{\sigma}{\sqrt{n}}$$

| Symbol | Meaning |
| :--- | :--- |
| $\bar{x}$ | sample mean — the *estimate* of $\mu$ |
| $\sigma$ | population standard deviation (must be **known**) |
| $n$ | sample size |
| $C$ | confidence level (e.g. $0.95$) |
| $\alpha$ | $1 - C$, the significance level |
| $z^{*}_{\alpha/2}$ | critical value with area $\alpha/2$ to its right |

The quantity $z^{*}_{\alpha/2}\cdot\dfrac{\sigma}{\sqrt{n}}$ is the **margin of error**, $E$.

### Finding the Critical Value $z^{*}$

The standard-normal table gives area to the **left**. We want the middle $C$ of the curve, so look up the area $1 - \alpha/2 = (1 + C)/2$:

| Confidence level $C$ | $\alpha$ | Area to the left of $z^{*}$ | $z^{*}_{\alpha/2}$ |
| :---: | :---: | :---: | :---: |
| 90% | 0.10 | 0.9500 | 1.645 |
| 95% | 0.05 | 0.9750 | 1.960 |
| 99% | 0.01 | 0.9950 | 2.575 |

### The Conditions

1. **Random sample** — the data come from an SRS of the population of interest.
2. **Normality** — the population is Normal, *or* $n \ge 30$ (so the CLT applies).
3. **Independence** — if sampling without replacement, $10n \le N$.
4. **Known variance** — $\sigma$ must be *given*, not estimated from the data.

### Worked Example: 95% Confidence Interval for Average Credits

**Problem:** You take a random sample of 40 students at a college and ask them how many credits they are taking this semester. You find a mean number of credits of 12.6. If the standard deviation for the number of credits taken for all college students is known to be 2.5, find a 95% confidence interval for the mean number of credits taken by all students at the college.

**Checking the conditions:**

1. **Random:** ✓ (a random sample was specified)
2. **Normality:** ✓ ($n = 40 \ge 30$)
3. **Independence:** ✓ ($10n = 10(40) = 400$; safe to assume $N > 400$)
4. **Known $\sigma$:** ✓ ($\sigma = 2.5$)

**Finding the critical value:**
$$C = 0.95 \Rightarrow \alpha = 1 - 0.95 = 0.05, \qquad \frac{\alpha}{2} = 0.025 \Rightarrow z^{*}_{\alpha/2} = 1.96$$

**Calculation:**
$$\text{SE} = \frac{\sigma}{\sqrt{n}} = \frac{2.5}{\sqrt{40}} = \frac{2.5}{6.3246} \approx 0.3953$$
$$E = 1.96(0.3953) \approx 0.77$$
$$\text{CI} = 12.6 \pm 0.77 = (11.83,\ 13.37)$$

**Interpretation:** We are 95% confident that the mean number of credits taken by all students at the college is between 11.83 credits and 13.37 credits.

### How Confidence Intervals Behave

| Change | Effect on $z^{*}$ | Effect on $E$ | Effect on the interval |
| :--- | :---: | :---: | :--- |
| Higher confidence level $C$ | $z^{*}$ increases | $E$ increases | **Wider** |
| Larger sample size $n$ | no change | $\sigma/\sqrt{n}$ decreases | **Narrower** |
| Smaller population SD $\sigma$ | no change | $E$ decreases | **Narrower** |

You can have *high confidence* or a *small margin of error*, but generally not both from the same sample — unless you collect more data.

### Choosing $n$ for a Desired Margin of Error

Start from $E = z^{*}_{\alpha/2}\cdot\dfrac{\sigma}{\sqrt{n}}$ and solve for $n$:
$$n = \left(\frac{z^{*}_{\alpha/2}\,\sigma}{E}\right)^{\!2}$$

**Example (course slide):** We want the margin of error of college savings contributions to be $\$30$ with 95% confidence, and $\sigma = \$1483$.
$$n = \left(\frac{(1.96)(1483)}{30}\right)^{2} = (96.889)^{2} \approx 9387.5 \Rightarrow n = 9388$$

**Always round *up*** — a smaller sample would give a margin of error *larger* than the one requested.

**Quick rule:** to halve the margin of error you must **quadruple** $n$ (because $\sqrt{4n} = 2\sqrt{n}$). Halving the margin of error of the credits example ($E = 0.77$ to $E \approx 0.39$) would take $n$ from 40 to 160.

### Cautions

- The data must come from an **SRS**; the formula is not valid for other sampling methods.
- $\sigma$ must be **known**. If it is not, use a **$t$ interval** instead (introduced in Ch. 7 of the slides).
- Confidence intervals are **not resistant to outliers**.
- If $n < 15$ and the population is not Normal, the true coverage is not $C$.
- The margin of error covers **random sampling error only** — it does not cover bias, nonresponse, or a badly chosen sample.

---

## Part E: Hypothesis Testing: The Framework

### Two Competing Ideas

A **significance test** is a formal procedure for assessing the evidence in the data against a claim (a *hypothesis*) about a population parameter.

- **Null hypothesis ($H_0$):** states that *no change has occurred* — the parameter equals the null value. It is the claim the test *challenges*.
- **Alternative hypothesis ($H_a$ or $H_1$):** contradicts the null hypothesis. It is the claim for which we are trying to find evidence.

The test works by *assuming $H_0$ is true* and asking: how likely would we be to collect a sample like this one? If the sample is very unlikely under $H_0$ (more unlikely than the significance level $\alpha$), we **reject $H_0$**; otherwise we **fail to reject $H_0$**.

### The Three Shapes of the Alternative

For a test about a parameter $\theta$ with null value $\theta_0$:

| Alternative | Meaning | Shape | Critical value(s) |
| :--- | :--- | :--- | :--- |
| $\theta < \theta_0$ | parameter is **less than** the null value | left-tailed | $-z_{\text{crit}}$ |
| $\theta > \theta_0$ | parameter is **greater than** the null value | right-tailed | $+z_{\text{crit}}$ |
| $\theta \ne \theta_0$ | parameter is **different from** the null value | two-tailed | $\pm z_{\text{crit}}$ |

The **direction** of $H_a$ is chosen to match the question being asked, and it must be chosen *before* looking at the data.

### Significance Level, Type I and Type II Errors, and Power

The **significance level** $\alpha$ is the long-run rate at which the test rejects a true $H_0$. It is decided *before* the test is run, based on how serious a false positive would be.

| | $H_0$ is **true** | $H_0$ is **false** |
| :--- | :--- | :--- |
| **Reject $H_0$** | **Type I error** (false alarm) — probability $= \alpha$ | Correct decision — probability $=$ power |
| **Fail to reject $H_0$** | Correct decision | **Type II error** (missed effect) — probability $= \beta$ |

- **Power** $= 1 - \beta$: the probability of rejecting $H_0$ when a specific alternative is true.
- Power rises when $n$ rises, when $\sigma$ falls, when $\alpha$ rises, and when the true effect is farther from $\theta_0$.

### The Five Steps of a Hypothesis Test

1. **State the hypotheses** ($H_0$ and $H_a$) and the significance level $\alpha$.
2. **Check the conditions** (random, normal/large enough, independent, known $\sigma$).
3. **Compute the test statistic** (a standardized distance from the null value).
4. **Find the $p$-value** *or* the **critical value** and compare.
5. **Write the conclusion** in context.

> *Note:* the original lecture notes numbered the steps inconsistently (step 3 onward were numbered but steps 1–2 were not). They are numbered 1–5 throughout this guide.

### The Test Statistic in General Form

$$\text{test statistic} = \frac{\text{sample version of the parameter} - \text{value from } H_0}{\text{standard error}}$$

| Symbol | Meaning |
| :--- | :--- |
| $\theta$ | the population parameter being tested |
| $\theta_0$ | the hypothesized null value of the parameter |
| $\hat{\theta}$ | the sample statistic (estimator of $\theta$) |
| $SE$ | standard error of the sampling distribution of the statistic |

---

## Part F: The Classical (Critical Value) Method

### Step 3: Find the Critical Value

The **critical value** is the value on the probability distribution whose tail area equals $\alpha$:

- **Left-tailed test:** the tail area $\alpha$ is in the **left** tail, bounded by $-z_{\text{crit}}$.
- **Right-tailed test:** the tail area $\alpha$ is in the **right** tail, bounded by $+z_{\text{crit}}$.
- **Two-tailed test:** the tail area is split evenly, with $\alpha/2$ in each tail, bounded by $-z_{\text{crit}}$ and $+z_{\text{crit}}$.

We look these up in the standard-normal table (or read them off the $z$-table's critical-value rows).

### Critical Values for Common $\alpha$ Levels

| Alternative | $\alpha = 0.10$ | $\alpha = 0.05$ | $\alpha = 0.01$ |
| :--- | :---: | :---: | :---: |
| Left-tailed ($z_{\text{crit}}$) | $-1.282$ | $-1.645$ | $-2.326$ |
| Right-tailed ($z_{\text{crit}}$) | $1.282$ | $1.645$ | $2.326$ |
| Two-tailed ($z_{\text{crit}}$) | $\pm 1.645$ | $\pm 1.960$ | $\pm 2.576$ |

### Step 4: Compare the Test Statistic to the Critical Value

| Alternative | Reject $H_0$ if |
| :--- | :--- |
| $H_a: \theta < \theta_0$ | $z < -z_{\text{crit}}$ |
| $H_a: \theta > \theta_0$ | $z > z_{\text{crit}}$ |
| $H_a: \theta \ne \theta_0$ | $z < -z_{\text{crit}}$ **or** $z > z_{\text{crit}}$ |

In words: if the test statistic is **more extreme** (further from 0) than the critical value, we reject $H_0$. Otherwise we fail to reject $H_0$.

### Step 5: Write the Conclusion

- **Reject $H_0$:** "At the $\alpha$ level there is **sufficient evidence** to support $H_a$."
- **Fail to reject $H_0$:** "At the $\alpha$ level there is **not sufficient evidence** to support $H_a$."

> **Never "accept $H_0$."** Failing to reject $H_0$ only means the evidence was not strong enough — the null may still be false (a Type II error), and the sample may simply have been too small.

### Worked Example: Are Students Taking More Than 13 Credits?

Continuing the credits data from Part D ($n = 40$, $\bar{x} = 12.6$, $\sigma = 2.5$).

**Step 1 — Hypotheses and level.** A college wants to know whether students are on average taking *more* than 13 credits:
$$H_0: \mu = 13, \qquad H_a: \mu > 13, \qquad \alpha = 0.05$$

**Step 2 — Conditions.** Random ✓, $n = 40 \ge 30$ ✓, $10n = 400 \le N$ ✓, $\sigma = 2.5$ known ✓.

**Step 3 — Test statistic.**
$$z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}} = \frac{12.6 - 13}{2.5/\sqrt{40}} = \frac{-0.4}{0.3953} \approx -1.01$$

**Step 4 — Critical value and decision.** Right-tailed test with $\alpha = 0.05$ gives $z_{\text{crit}} = 1.645$. Since $z = -1.01$ is **not** greater than $1.645$, we **fail to reject $H_0$**.

**Step 5 — Conclusion.** At the 5% significance level there is not sufficient evidence to conclude that the mean number of credits taken by students at the college is greater than 13.

*(Cross-check: the 95% CI from Part D was $(11.83,\ 13.37)$, which **contains** 13 — the two methods agree.)*

---

## Part G: The P-Value Method

### Definition

The **$p$-value** is the probability, **computed assuming $H_0$ is true**, that the test statistic would take a value **as extreme as or more extreme than** the one observed.

- The **smaller** the $p$-value, the **stronger** the evidence against $H_0$.
- A **large** $p$-value means the result is quite likely to occur by chance if $H_0$ were true — so it fails to provide convincing evidence against $H_0$.

### Tail Areas for Each Shape

| Alternative | The $p$-value is the area |
| :--- | :--- |
| $H_a: \theta > \theta_0$ | to the **right** of the test statistic |
| $H_a: \theta < \theta_0$ | to the **left** of the test statistic |
| $H_a: \theta \ne \theta_0$ | **twice** the area beyond the test statistic (once in each tail) |

### Decision Rule

- $p\text{-value} < \alpha$ → **reject $H_0$** (there is sufficient evidence to support $H_a$).
- $p\text{-value} \ge \alpha$ → **fail to reject $H_0$** (not sufficient evidence to support $H_a$).

### Worked Example: Is the Machine Overfilling?

**Problem:** A machine fills 16-ounce bottles. The process is Normal with known $\sigma = 0.1$ oz. A random sample of 25 bottles has a mean fill of 16.05 oz. Test at $\alpha = 0.05$ whether the machine is overfilling (mean fill greater than 16 oz).

**Step 1 — Hypotheses and level:**
$$H_0: \mu = 16, \qquad H_a: \mu > 16, \qquad \alpha = 0.05$$

**Step 2 — Conditions.** Random ✓, $n = 25$ with a Normal population ✓, $10n = 250 \le N$ ✓, $\sigma = 0.1$ known ✓.

**Step 3 — Test statistic:**
$$z = \frac{16.05 - 16}{0.1/\sqrt{25}} = \frac{0.05}{0.02} = 2.50$$

**Step 4 — $p$-value (right-tailed):**
$$p\text{-value} = P(Z > 2.50) = 1 - 0.9938 = 0.0062$$

**Step 5 — Decision and conclusion.** Since $0.0062 < 0.05$, we **reject $H_0$**. At the 5% significance level there is sufficient evidence that the machine is overfilling — the mean fill is greater than 16 ounces.

*(Cross-check: the 95% CI is $16.05 \pm 1.96(0.02) = (16.01,\ 16.09)$, which **excludes** 16.0 — the two methods agree.)*

### Reading a P-Value Off the $Z$-Table

Without technology, bracket the $p$-value between two table entries. For a two-tailed test with $z = 1.52$: the area to the left of $1.52$ is $0.9357$, so
$$p\text{-value} = 2(1 - 0.9357) = 0.1286, \qquad \text{so } 0.10 < p\text{-value} < 0.20$$

Because the $Z$-table only has two decimal places, the bracket is usually the honest answer.

### What a P-Value Is *Not*

- The $p$-value is **not** the probability that $H_0$ is true. It is a probability **computed under** $H_0$.
- A $p$-value of 0.006 does not mean "there is a 0.6% chance the null hypothesis is true."
- Statistical significance does not tell you the *size* of the effect, only that an effect is detectable.

---

## Part H: The Z-Test for $\mu$ and the CI ↔ Test Duality

### The Z-Test for a Population Mean

**1. Hypotheses:**
$$H_0: \mu = \mu_0, \qquad H_a: \mu < \mu_0 \ \text{ or } \ \mu > \mu_0 \ \text{ or } \ \mu \ne \mu_0$$

**2. Test statistic:**
$$z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$$

| Symbol | Meaning |
| :--- | :--- |
| $z$ | the calculated test statistic (a $z$-score for the sample mean) |
| $\bar{x}$ | sample mean |
| $\mu_0$ | hypothesized population mean from $H_0$ |
| $\sigma$ | population standard deviation |
| $n$ | sample size |
| $\sigma/\sqrt{n}$ | standard error of the sample mean |

**3. Critical value or $p$-value:** use the $z$-tables to find $z_{\text{crit}}$, or find the $p$-value directly.

**4. Decision:** reject $H_0$ if the test statistic falls in the rejection region (equivalently, if $p\text{-value} < \alpha$).

**5. Conclusion:** "At the $\alpha$ level there is (not) sufficient evidence to support $H_a$."

### The Duality: A Two-Sided Test and a Confidence Interval Are the Same Question

Because a two-sided test is symmetric, we can test $H_0: \mu = \mu_0$ with a $(1-\alpha)$ confidence interval:

$$C = 1 - \alpha$$

| Two-sided $z$-test at level $\alpha$ | Equivalent $C$-level interval | Same decision |
| :--- | :---: | :--- |
| $\alpha = 0.10$ | 90% CI | reject $H_0$ iff $\mu_0$ is **outside** the CI |
| $\alpha = 0.05$ | 95% CI | reject $H_0$ iff $\mu_0$ is **outside** the CI |
| $\alpha = 0.01$ | 99% CI | reject $H_0$ iff $\mu_0$ is **outside** the CI |

- $\mu_0$ **inside** the interval $\Rightarrow$ fail to reject $H_0$.
- $\mu_0$ **outside** the interval $\Rightarrow$ reject $H_0$.

This is why the credits example ($z = -1.01$, $p \approx 0.31$, fail to reject $H_0: \mu = 13$) matches its 95% CI $(11.83, 13.37)$: 13 is inside the interval.

### When to Use $t$ Instead of $z$

The $z$ procedures require the **population** $\sigma$ to be known. When $\sigma$ is unknown and is estimated by the sample standard deviation $s$, the standardized statistic follows a **$t$ distribution** with $df = n - 1$ instead of the Normal curve. That is the topic of the next chapter of the course slides (Ch. 7, "Inference for Means").

### Cautions About Significance Tests

- **Choosing $\alpha$:** consider the consequences of a false alarm; $0.05$ is the usual convention.
- **No sharp cutoffs:** there is no practical difference between a $p$-value of 0.049 and 0.051.
- **Absence of evidence is not evidence of absence:** failing to reject $H_0$ is not the same as showing $H_0$ is true.
- **Beware of searching for significance:** if many hypotheses are tested, some will look significant by chance alone.
- **Statistical significance ≠ practical importance:** with a large enough $n$, even a tiny effect can be "significant."

---

## Key Formulas

| Quantity | LaTeX | Plain / in words |
| :--- | :--- | :--- |
| $z$-score (individual) | $z=\dfrac{x-\mu}{\sigma}$ | (value − mean) ÷ population SD |
| $z$-score (sample mean) | $z=\dfrac{\bar{x}-\mu}{\sigma/\sqrt{n}}$ | (sample mean − μ) ÷ standard error |
| Standard error of the mean | $\sigma_{\bar{X}}=\dfrac{\sigma}{\sqrt{n}}$ | population SD ÷ √n |
| Mean of $\hat{p}$ | $\mu_{\hat{p}}=p$ | sample proportion centered on $p$ |
| Standard error of $\hat{p}$ | $\sigma_{\hat{p}}=\sqrt{\dfrac{p(1-p)}{n}}$ | √(pq ÷ n) |
| $p$-value (right-tailed) | $P(Z>z_{\text{obs}})$ | area to the right of the test statistic |
| $p$-value (left-tailed) | $P(Z<z_{\text{obs}})$ | area to the left of the test statistic |
| $p$-value (two-tailed) | $2\,P(Z>\lvert z_{\text{obs}}\rvert)$ | twice the area in one tail |
| Confidence interval for $\mu$ | $\bar{x}\pm z^{*}_{\alpha/2}\cdot\dfrac{\sigma}{\sqrt{n}}$ | estimate ± margin of error |
| Margin of error | $E=z^{*}_{\alpha/2}\cdot\dfrac{\sigma}{\sqrt{n}}$ | critical value × standard error |
| Significance level | $\alpha=1-C$ | tail area of the test |
| Critical value (two-tailed) | $z^{*}_{\alpha/2},\ \text{area left}=\dfrac{1+C}{2}$ | look up $(1+C)/2$ in the $z$-table |
| Sample size for margin of error $E$ | $n=\left(\dfrac{z^{*}_{\alpha/2}\sigma}{E}\right)^{2}$ | solve the margin-of-error formula for $n$ |
| Z-test statistic | $z=\dfrac{\bar{x}-\mu_0}{\sigma/\sqrt{n}}$ | (sample mean − null value) ÷ standard error |
| Continuity correction | $a \rightarrow a \pm 0.5$ | shift the cutoff by half a unit |
| Test ↔ interval duality | $C = 1 - \alpha$ | a two-sided test at level $\alpha$ matches a $C = 1-\alpha$ interval |

---

## Practice Problems

**1.** The heights of trees are Normal with $\mu = 25$ ft and $\sigma = 3$ ft. Find (a) $P(X < 28)$ and (b) the 25th percentile height.

<details><summary>Solution</summary>

(a) $z = (28-25)/3 = 1.00$, so $P(X<28) = P(Z<1.00) = 0.8413$.
(b) The 25th percentile has $z$ with $0.25$ area to its left: $z = -0.674$. So $x = 25 + (-0.674)(3) = 25 - 2.022 = 22.98$ ft.

</details>

**2.** Using the tree data ($n = 10$ trees), find $P(\bar{X} < 28)$ and $P(\bar{X} > 30)$.

<details><summary>Solution</summary>

$\sigma_{\bar{X}} = 3/\sqrt{10} \approx 0.9487$.
$P(\bar{X}<28)$: $z = (28-25)/0.9487 \approx 3.16$, so $P \approx 0.9992$.
$P(\bar{X}>30)$: $z = (30-25)/0.9487 \approx 5.27$, so $P(Z>5.27) \approx 0.0000007$ — essentially impossible. A sample mean of 30 ft is wildly inconsistent with a population centered at 25 ft.

</details>

**3.** A binomial random variable has $n = 100$ and $p = 0.45$. Approximate $P(X \le 50)$ with a normal distribution.

<details><summary>Solution</summary>

$np = 45 \ge 10$ and $n(1-p) = 55 \ge 10$, so the approximation is valid. $\mu = np = 45$, $\sigma = \sqrt{45 \cdot 0.55} = \sqrt{24.75} \approx 4.975$. With the continuity correction, $P(X \le 50) \approx P(Y < 50.5)$. $z = (50.5 - 45)/4.975 \approx 1.106$, so $P \approx 0.8656$.

</details>

**4.** In a random sample of 50 students, 32 say they are satisfied with campus food. What are the mean and standard deviation of the sampling distribution of $\hat{p}$ if the true satisfaction rate is $p = 0.70$?

<details><summary>Solution</summary>

$\mu_{\hat{p}} = p = 0.70$. $\sigma_{\hat{p}} = \sqrt{p(1-p)/n} = \sqrt{0.7(0.3)/50} = \sqrt{0.0042} \approx 0.0648$. (Conditions: $np = 35 \ge 10$ and $n(1-p) = 15 \ge 10$, so the Normal approximation is justified.)

</details>

**5.** A survey of 400 adults finds a 95% confidence interval of $(0.52,\ 0.60)$ for the proportion who support a policy. Is the margin of error 0.04 or 0.08? How would the margin of error change if $n$ were quadrupled?

<details><summary>Solution</summary>

The interval is centered at $0.56$ and extends $0.04$ on each side, so the margin of error is $E = 0.04$. Quadrupling $n$ halves the standard error (since $E \propto 1/\sqrt{n}$), so the new margin of error would be $0.02$.

</details>

**6.** Find the sample size needed to estimate a population mean with a margin of error of 2 units at 95% confidence, given $\sigma = 10$.

<details><summary>Solution</summary>

$n = \left(\frac{z^*_{\alpha/2}\sigma}{E}\right)^2 = \left(\frac{1.96(10)}{2}\right)^2 = (9.8)^2 = 96.04$. Round **up** to $n = 97$ so the margin of error is no more than 2.

</details>

**7.** A population has $\mu = 50$ and $\sigma = 8$. A random sample of 64 gives $\bar{x} = 52.4$. Test $H_0: \mu = 50$ against $H_a: \mu > 50$ at $\alpha = 0.05$ using the classical method.

<details><summary>Solution</summary>

$SE = 8/\sqrt{64} = 1.00$, so $z = (52.4 - 50)/1.00 = 2.40$. Right-tailed critical value at $\alpha = 0.05$: $z_{\text{crit}} = 1.645$. Since $2.40 > 1.645$, **reject $H_0$**. There is sufficient evidence at the 5% level that the population mean exceeds 50. (Equivalently, the $p$-value is $1 - 0.9918 = 0.0082 < 0.05$, and the 95% CI is $52.4 \pm 1.96(1.00) = (50.44, 54.36)$, which excludes 50.)

</details>

**8.** Explain why "failing to reject $H_0$" is not the same as "proving $H_0$ true."

<details><summary>Solution</summary>

Failing to reject $H_0$ only means the data were not strong enough to reject it at the chosen $\alpha$ — the test may have made a **Type II error** (the null really is false), or the sample may have been too small to detect a real effect. Statistical evidence is about the *strength of the evidence*, not proof. "Absence of evidence is not evidence of absence."

</details>

### Multiple Choice

**9.** A 99% confidence interval requires a larger critical value $z^*$ than a 95% interval. This is because:

- **a)** Higher confidence requires more data
- **b)** Higher confidence needs more area captured in the center, pushing the cutoffs further into the tails
- **c)** The standard error decreases as confidence increases
- **d)** $z^*$ is inversely related to $\alpha$

<details><summary>Solution</summary>

- A 99% interval must capture 99% of the area, leaving only 0.5% in each tail; a 95% interval leaves 2.5% in each tail.
- The cutoffs therefore move further out: $z^{*} = 2.575$ versus $1.960$, giving a **wider** interval.

**Final answer: (b) Higher confidence needs more area captured in the center, pushing the cutoffs further into the tails**

</details>

**10.** In a two-tailed test, the test statistic is $z = -1.85$ and $\alpha = 0.05$. The conclusion is:

- **a)** Reject $H_0$, because $z < -1.96$
- **b)** Fail to reject $H_0$, because $z > -1.96$
- **c)** Reject $H_0$, because $z < -1.645$
- **d)** Fail to reject $H_0$, because the $p$-value is 0.06

<details><summary>Solution</summary>

- For a two-tailed test at $\alpha = 0.05$, the critical values are $\pm 1.96$.
- $z = -1.85$ is *not* beyond $-1.96$, so it is in the non-rejection region.
- The $p$-value is $2(1 - 0.9678) = 0.0644 > 0.05$, which confirms the decision.

**Final answer: (b) Fail to reject $H_0$, because $z > -1.96$**

</details>

**11.** A 95% confidence interval for a population mean is computed as $(8.2,\ 11.8)$. Which null hypothesis would be **rejected** by the corresponding two-sided test at $\alpha = 0.05$?

- **a)** $H_0: \mu = 9$
- **b)** $H_0: \mu = 10$
- **c)** $H_0: \mu = 12$
- **d)** $H_0: \mu = 8$

<details><summary>Solution</summary>

- A two-sided test at $\alpha = 0.05$ rejects $H_0$ exactly when the null value lies **outside** the 95% interval.
- $12 > 11.8$, so $\mu_0 = 12$ is outside the interval and is rejected; $9$, $10$, and $8$ all lie inside it.

**Final answer: (c) $H_0: \mu = 12$**

</details>
