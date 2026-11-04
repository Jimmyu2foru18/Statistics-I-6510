# Statistics I, Day 8: Normal Calculations, Confidence Intervals, and Hypothesis Tests

Welcome to Day 8! Today we bring together the normal distribution and sampling ideas from earlier days and use them for statistical inference. We will cover normal calculations with z-scores, confidence intervals for a population mean, and the foundations of hypothesis testing.

---

## Part A: Normal Calculations with z-scores

Tree heights of a certain species are normally distributed with mean 25 ft and standard deviation 3 ft:

X ~ N(25, 3)

Let X be the height of one randomly selected tree, and let X̄ be the mean height of a random sample of 10 trees.

**z-score formula (individual value):**

z = (x − μ) / σ

**z-score formula (sample mean):**

z = (X̄ − μ) / (σ / √n)

**Standard error of the mean:**

SE = σ / √n

The mean of 10 trees is less variable than one tree because the standard deviation shrinks by a factor of √n.

| Random variable | What it is | Mean | Standard deviation |
| :--- | :--- | :--- | :--- |
| X | height of one tree | μ = 25 | σ = 3 |
| X̄ | mean height of 10 trees | μ₍ₓ̄₎ = 25 | σ₍ₓ̄₎ = 3 / √10 ≈ 0.9487 |

### a.) Find P(X < 26)

z = (26 − 25) / 3 = 1/3 ≈ 0.33

P(X < 26) = P(Z < 0.33) = 0.6293

### b.) Find P(X > 27)

z = (27 − 25) / 3 = 2/3 ≈ 0.67

P(X > 27) = 1 − P(Z < 0.67) = 1 − 0.7486 = 0.2514

### c.) Find the 90th percentile height

**Definition:** A pth percentile is the value x such that P(X < x) = p.

Find z with 0.90 of the area to its left: z = 1.2816.

Convert back to x:

x = μ + z · σ = 25 + (1.2816)(3) = 28.8448 ≈ 28.84 ft

90% of trees are shorter than 28.84 ft.

### d.) Find P(X̄ < 26)

Standard error = 3 / √10 ≈ 0.9487.

z = (26 − 25) / 0.9487 ≈ 1.05.

P(X̄ < 26) = P(Z < 1.05) = 0.8531.

### e.) Find P(X̄ > 27)

z = (27 − 25) / 0.9487 ≈ 2.11.

P(X̄ > 27) = 1 − P(Z < 2.11) = 1 − 0.9826 = 0.0174.

Averages are less variable than individuals.

### Calculator commands

- normalcdf(lower, upper, mu, sigma): probability between two values. Use −1E99 and 1E99 for tails.
- normalcdf(26, 1E99, 25, 3): part (a).
- invNorm(area, mu, sigma): percentile command. invNorm(0.90, 25, 3) = 28.845.

---

## Part B: Normal Approximation to the Binomial

Suppose 20% of people own a car. Let X = number of car owners in a sample of 200 residents. Approximate P(X > 45).

**Definition:** X is binomial if it meets the BINS conditions:
- Binary: two outcomes (owns a car or does not).
- Independent: trials are independent.
- Number: the number of trials n is fixed.
- Same probability: the probability of success p is the same on every trial.

X ~ Binomial(200, 0.20).

**Binomial mean:** μ = np
**Binomial standard deviation:** σ = √(np(1 − p))

**Normal approximation conditions:** np ≥ 10 and n(1 − p) ≥ 10.

np = 200(0.20) = 40
n(1 − p) = 200(0.80) = 160

Both are at least 10, so the normal approximation is valid.

Mean: μ = np = 40
SD: σ = √(200 · 0.20 · 0.80) = √32 ≈ 5.6569

**Continuity correction:** Because the binomial is discrete and the normal is continuous, "more than 45" becomes "greater than 45.5."

P(X > 45) ≈ P(Y > 45.5)

z = (45.5 − 40) / 5.6569 ≈ 0.97

P(X > 45) ≈ P(Z > 0.97) = 1 − 0.8340 = 0.1660.

Exact binomial: P(X > 45) ≈ 0.1651. Close match.

**Continuity correction rule:**

| Binomial (discrete) | Normal (continuous) approximation |
| :--- | :--- |
| P(X = a) | P(a − 0.5 < X < a + 0.5) |
| P(X ≤ a) | P(X < a + 0.5) |
| P(X < a) | P(X < a − 0.5) |
| P(X ≥ a) | P(X > a − 0.5) |
| P(X > a) | P(X > a + 0.5) |

---

## Part C: Sampling Distribution of a Sample Proportion

Suppose 70% of students are satisfied with campus food. Take a sample of 50 students. Let p̂ = proportion satisfied.

**Definition:** The sampling distribution of a statistic is the distribution of that statistic across all possible random samples of size n from a population.

**Central Limit Theorem:** As n grows, the sampling distribution of a statistic becomes approximately normal.

**Conditions for p̂ to be approximately Normal:** np ≥ 10 and n(1 − p) ≥ 10.

np = 50(0.70) = 35
n(1 − p) = 50(0.30) = 15

Both are at least 10, so p̂ is approximately Normal.

**Mean of p̂:** μ₍p̂₎ = p
**Standard error of p̂:** σ₍p̂₎ = √(p(1 − p) / n)

μ₍p̂₎ = p = 0.70
σ₍p̂₎ = √(0.70 · 0.30 / 50) = √0.0042 ≈ 0.0648

### b.) P(p̂ < 0.75)

z = (0.75 − 0.70) / 0.0648 ≈ 0.77

P(p̂ < 0.75) = P(Z < 0.77) = 0.7794

### c.) P(0.5 < p̂ < 0.8)

z₁ = (0.50 − 0.70) / 0.0648 ≈ −3.09
z₂ = (0.80 − 0.70) / 0.0648 ≈ 1.54

P(0.5 < p̂ < 0.8) = P(Z < 1.54) − P(Z < −3.09) = 0.9382 − 0.0010 = 0.9372

About 94% of samples of 50 students fall between 50% and 80% satisfied.

---

## Part D: Confidence Interval for a Population Mean (Z-interval)

**Definition:** A confidence interval has two parts:
1. An interval computed from the data, with the form estimate ± margin of error.
2. A confidence level C, the capture rate of the method.

**Z-interval for μ formula:**

CI for μ = X̄ ± z*₍α/2₎ · (σ / √n)

where:
- X̄ is the sample mean, the estimate of μ
- σ is the population standard deviation, which must be known
- n is the sample size
- C is the confidence level
- α = 1 − C
- z*₍α/2₎ is the critical value with area (1 + C)/2 to its left

**Margin of error:**

E = z*₍α/2₎ · (σ / √n)

**Standard error:**

SE = σ / √n

**Finding z*:** Look up area (1 + C)/2 in the z-table.

| Confidence level C | α | Area to left of z* | z*₍α/2₎ |
| :--- | :--- | :--- | :--- |
| 90% | 0.10 | 0.9500 | 1.645 |
| 95% | 0.05 | 0.9750 | 1.960 |
| 99% | 0.01 | 0.9950 | 2.575 |

**Conditions for a Z-interval:**
1. Random sample: the data come from an SRS of the population.
2. Normality: the population is Normal, or n ≥ 30 so the CLT applies.
3. Independence: if sampling without replacement, 10n ≤ N.
4. Known sigma: σ must be given, not estimated from the data.

### Worked example: 95% CI for average credits

Sample of 40 students, mean 12.6 credits, σ = 2.5 known.

Conditions: random, n = 40 ≥ 30, independence, known sigma. All met.

z* = 1.96

SE = 2.5 / √40 ≈ 0.3953
E = 1.96 · 0.3953 ≈ 0.77

CI = 12.6 ± 0.77 = (11.83, 13.37)

Interpretation: We are 95% confident the mean credits is between 11.83 and 13.37.

### Choosing n for a desired margin of error

**Sample size formula:**

n = (z*₍α/2₎ · σ / E)²

Always round up so the margin of error is no more than requested.

Example: margin of error $30 at 95% confidence, σ = $1483.

n = (1.96 · 1483 / 30)² = (96.889)² ≈ 9387.5, so n = 9388.

To halve the margin of error, quadruple n, because E is proportional to 1 / √n.

---

## Part E: Hypothesis Testing Framework

**Definition:** A significance test is a formal procedure for assessing the evidence in the data against a claim about a population parameter.

**Null hypothesis (H₀):** states that no change has occurred, meaning the parameter equals the null value. It is the claim the test challenges.

**Alternative hypothesis (Hₐ or H₁):** contradicts the null hypothesis. It is the claim for which we are trying to find evidence.

**Significance level (α):** the probability of a Type I error we are willing to risk if we reject H₀. Decided before the test.

The test works by assuming H₀ is true and asking how likely we would be to collect a sample like this one. If the sample is very unlikely under H₀, more unlikely than α, we reject H₀; otherwise we fail to reject H₀.

**Three shapes of the alternative:**

| Alternative | Meaning | Shape |
| :--- | :--- | :--- |
| θ < θ₀ | less than null value | left-tailed |
| θ > θ₀ | greater than null value | right-tailed |
| θ ≠ θ₀ | different from null value | two-tailed |

**Five steps of a hypothesis test:**

1. State H₀ and Hₐ, and α.
2. Check conditions.
3. Compute the test statistic.
4. Find the p-value or critical value and compare.
5. Write the conclusion in context.

**Test statistic formula:**

Test statistic = (sample statistic − null value) / standard error

For a test about μ with σ known:

z = (X̄ − μ₀) / (σ / √n)

**Never "accept H₀."** Failing to reject H₀ does not prove H₀ is true.

**Type I and Type II errors:**

| | H₀ True | H₀ False |
| :--- | :--- | :--- |
| Reject H₀ | Type I error (false positive) | Correct decision |
| Fail to reject H₀ | Correct decision | Type II error (false negative) |

**Definitions:**

- α = probability of Type I error if we reject H₀ (significance level).
- β = probability of a Type II error if we do not reject H₀.
- Power = 1 − β = probability of rejecting H₀ when a specific alternative is true.

Power rises when n rises, σ falls, α rises, or the true effect is farther from θ₀.

---

## Part F: Classical (Critical Value) Method

**Definition:** The critical value is the value on the probability distribution whose tail area equals α.

- Left-tailed test: tail area α is in the left tail, bounded by −z_crit.
- Right-tailed test: tail area α is in the right tail, bounded by +z_crit.
- Two-tailed test: tail area is split evenly, with α/2 in each tail, bounded by −z_crit and +z_crit.

**Critical values:**

| | α = 0.10 | α = 0.05 | α = 0.01 |
| :--- | :--- | :--- | :--- |
| Left-tailed | −1.282 | −1.645 | −2.326 |
| Right-tailed | 1.282 | 1.645 | 2.326 |
| Two-tailed | ±1.645 | ±1.960 | ±2.576 |

**Decision rule:** Reject H₀ if the test statistic is more extreme, further from 0, than the critical value. Otherwise fail to reject H₀.

### Worked example: Students taking more than 13 credits

H₀: μ = 13, Hₐ: μ > 13, α = 0.05.

z = (12.6 − 13) / (2.5 / √40) ≈ −1.01.

Right-tailed critical value at α = 0.05 is 1.645. Since −1.01 is not greater than 1.645, fail to reject H₀.

Conclusion: Not enough evidence that mean credits is greater than 13.

---

## Part G: P-value Method

**Definition:** The p-value is the probability, computed assuming H₀ is true, that the test statistic would take a value as extreme as or more extreme than the one observed.

- The smaller the p-value, the stronger the evidence against H₀.
- A large p-value means the result is likely to occur by chance if H₀ were true.

**Tail areas:**

| Alternative | The p-value is the area |
| :--- | :--- |
| Hₐ: θ > θ₀ | to the right of the test statistic |
| Hₐ: θ < θ₀ | to the left of the test statistic |
| Hₐ: θ ≠ θ₀ | twice the area beyond the test statistic |

**Decision rule:**
- p-value < α: reject H₀.
- p-value ≥ α: fail to reject H₀.

### Worked example: Machine overfilling

Machine fills 16-ounce bottles, σ = 0.1 known. Sample of 25, mean fill 16.05 oz. Test at α = 0.05 whether mean fill is greater than 16.

H₀: μ = 16, Hₐ: μ > 16.

z = (16.05 − 16) / (0.1 / √25) = 0.05 / 0.02 = 2.50.

p-value = P(Z > 2.50) = 1 − 0.9938 = 0.0062.

Since 0.0062 < 0.05, reject H₀. Sufficient evidence the machine is overfilling.

**What a p-value is not:**
- The p-value is not the probability that H₀ is true. It is a probability computed under H₀.
- Statistical significance does not tell you the size of the effect.

---

## Part H: Z-test for μ and CI-test Duality

**Z-test statistic:**

z = (X̄ − μ₀) / (σ / √n)

**CI-test duality:** Because a two-sided test is symmetric, we can test H₀: μ = μ₀ with a C = 1 − α confidence interval:

- μ₀ inside the interval: fail to reject H₀.
- μ₀ outside the interval: reject H₀.

| Two-sided z-test at level α | Equivalent interval | Same decision |
| :--- | :--- | :--- |
| α = 0.10 | 90% CI | reject H₀ iff μ₀ is outside the CI |
| α = 0.05 | 95% CI | reject H₀ iff μ₀ is outside the CI |
| α = 0.01 | 99% CI | reject H₀ iff μ₀ is outside the CI |

**When to use t instead of z:** The z procedures require the population σ to be known. When σ is unknown and estimated by s, use a t-distribution with df = n − 1.
