# Statistics I, Day 9: Z-Intervals, Z-Tests, Hypothesis Test Outcomes, T-Distributions, Matched Pairs, and Two-Sample t Procedures

Welcome to Day 9! Day 8 introduced confidence intervals and hypothesis tests for a population mean when the population standard deviation σ is known (z-procedures). Today we finish those z-procedures, then tackle the far more common real-world situation where σ is unknown. When σ is unknown we estimate it with the sample standard deviation s, and the standardized statistic no longer follows a normal curve — it follows a t-distribution with heavier tails. We will cover t-intervals and t-tests for one mean, matched pairs, and two independent samples.

---

## Part A: Z-Interval for a Population Mean (Potato Chip Problem)

Here is the setup: you take a random sample of 40 bags of potato chips and weigh them. The mean weight comes out to 11.8 oz. We happen to know the population standard deviation, σ = 1.4 oz.

- Sample mean: x̄ = 11.8 oz
- Population standard deviation: σ = 1.4 oz
- Sample size: n = 40

### 1a.) Checking the conditions for a Z-interval

Before building a confidence interval, verify the four conditions:

**Condition 1 — Random sample.** The 40 bags are randomly selected. Check.

**Condition 2 — Normality.** n = 40 ≥ 30, so by the Central Limit Theorem the sampling distribution of x̄ is approximately normal regardless of the population shape. Check.

**Condition 3 — Independence.** The 40 bags are less than 10% of all potato chip bags (10n = 400 ≪ total production), so observations are independent. Check.

**Condition 4 — Known sigma.** σ = 1.4 is given, not estimated from the data. Check.

All four conditions are satisfied, so we proceed with a Z-interval.

### 1b.) Finding a 95% confidence interval for μ

A confidence interval has the form estimate ± margin of error:

CI = x̄ ± z* × (σ / √n)

For 95% confidence, α = 0.05 and the critical value z*₍α/2₎ = 1.96 (area 0.9750 to its left).

**Standard error:**
SE = σ / √n = 1.4 / √40 ≈ 0.2214

**Margin of error:**
E = z* × SE = 1.96 × 0.2214 ≈ 0.4339

**Bounds:**
- Lower: 11.8 − 0.4339 = 11.37
- Upper: 11.8 + 0.4339 = 12.23

The 95% confidence interval is **(11.37, 12.23)** oz. We are 95% confident that the true mean weight of all bags of potato chips falls between 11.37 and 12.23 oz.

### 1c.) Sample size for a margin of error under 0.1

We want E < 0.1:

z* × (σ / √n) < 0.1
1.96 × (1.4 / √n) < 0.1

Solve for n:

√n > (1.96 × 1.4) / 0.1 = 27.44
n > (27.44)² ≈ 752.95

Round up: **n = 753**. We already have 40 bags, so we need 753 − 40 = **713 more bags**.

**Connection to Day 8:** E is proportional to 1/√n, so to halve the margin of error you must quadruple the sample size.

---

## Part B: Z-Test — Are the Bags Underfilled?

Now the manufacturer advertises 12 oz per bag. We test at α = 0.05 whether the mean weight is actually *lower* than advertised.

### Step 1: State the hypotheses

- Null hypothesis H₀: μ = 12
- Alternative hypothesis Hₐ: μ < 12

This is a **left-tailed** test because we check whether the mean is less than 12.

### Step 2: Check conditions

Random sample? Check. n = 40 satisfies normality (CLT)? Check. Independence? Check. Known sigma? Check. All met.

### Step 3: Calculate the test statistic

z = (x̄ − μ₀) / (σ / √n)

z = (11.8 − 12) / (1.4 / √40) ≈ −0.20 / 0.2214 ≈ −0.90

### Step 4: Find the p-value

The p-value is the probability, computed assuming H₀ is true, of getting a test statistic at least as extreme as the one observed. For a left-tailed test, that is the area to the left of z:

p-value = P(Z < −0.90) ≈ 0.1841

For reference, the critical value for a left-tailed test at α = 0.05 is −1.645.

### Step 5: Make a decision

Compare p-value to α = 0.05. Since 0.1841 > 0.05, **fail to reject H₀**.

Equivalently, the test statistic −0.90 is not less than the critical value −1.645, so we do not reject.

### Step 6: Conclusion

There is **not enough evidence** at the 0.05 significance level to conclude the mean weight is less than 12 oz. We cannot say the bags are underfilled based on this sample.

**Remember:** failing to reject H₀ does not prove H₀ is true. It only means the data are not strong enough to reject it.

---

## Part C: Outcomes of a Hypothesis Test (Type I, Type II, Power)

When we run a test, one of four things can happen:

| Decision | H₀ True | H₀ False |
| :--- | :--- | :--- |
| Reject H₀ | Type I error (false positive) | Correct decision |
| Fail to reject H₀ | Correct decision | Type II error (false negative) |

**α (alpha):** the probability of a Type I error we are willing to risk if we reject H₀. This is the significance level, chosen before the test.

**β (beta):** the probability of a Type II error if we do not reject H₀.

**Power = 1 − β:** the probability of correctly rejecting H₀ when it is actually false — the test's ability to detect a real effect.

Power rises when n rises, σ falls, α rises, or the true effect is farther from the null value θ₀.

---

## Part D: T-Distributions (When σ Is Unknown)

Z-procedures require knowing σ. In practice σ is almost never known, so we estimate it with the sample standard deviation s. The standardized statistic

t = (x̄ − μ) / (s / √n)

then follows a **t-distribution** with df = n − 1 degrees of freedom, not a normal curve.

### Why t instead of z?

Estimating σ with s adds extra uncertainty, especially for small samples. The t-distribution has **heavier tails** than the standard normal, which produces wider intervals and more conservative tests to account for that uncertainty. As the degrees of freedom grow, the t-distribution approaches the standard normal, so for large n the two are nearly identical.

### Degrees of freedom

For a single mean:

df = n − 1

We use df to look up critical t-values (t*) from the t-table. Each df gives a different curve and different critical values.

### Example: Robot food delivery times

You record eight weekday lunch delivery times from a campus robot service:

- n = 8
- x̄ = 23.1 minutes
- s = 14.328 minutes
- Goal: 95% CI for the true mean delivery time μ

**Step 1 — Degrees of freedom:** df = n − 1 = 7. For df = 7 at 95% confidence, t* = 2.365.

**Step 2 — Standard error:**
SE = s / √n = 14.328 / √8 ≈ 5.066 minutes

**Step 3 — Margin of error:**
ME = t* × SE = 2.365 × 5.066 ≈ 11.98 minutes

**Step 4 — Confidence interval:**
- Lower: 23.1 − 11.98 = 11.12
- Upper: 23.1 + 11.98 = 35.08

The 95% CI is **(11.12, 35.08)** minutes. The interval is wide because n is small and the t-critical value (2.365) is larger than the z-critical value (1.96), reflecting the extra uncertainty from estimating σ with s.

**Calculator commands:**
- `tcdf(lower, upper, df)`: t-probability between two values
- `invT(area, df)`: critical t-value with that area to its left

---

## Part E: Matched Pairs t Procedures

Matched pairs t procedures apply when we have two related measurements on the same individuals — a before/after or with/without design. We compute the difference for each individual, then run one-sample t procedures on those differences.

### Matched pairs conditions

1. **Paired data:** two measurements on the same (or matched) individuals.
2. **Normal differences:** the differences are approximately normal, roughly symmetric with no outliers, or n is large enough.
3. **Independent pairs:** the pairs are independent of each other.

Analyzing differences is powerful because pairing removes between-person variability, leaving only the treatment effect plus measurement noise.

### Example: MeasureMind 3D MultiSensor software

Researchers measured 51 machine parts with one software option checked and unchecked, in randomized order. The difference (with − without) was recorded for each part. We test at α = 0.05:

H₀: μ_d = 0
Hₐ: μ_d ≠ 0

(two-tailed; μ_d is the mean difference across all parts)

The differences are reasonably symmetric with no outliers, so t procedures are appropriate.

### Step-by-step solution

**Step 1 — Hypotheses:** H₀: μ_d = 0, Hₐ: μ_d ≠ 0.

**Step 2 — Conditions:** Paired (same 51 parts twice), differences symmetric/no outliers, pairs independent. Met.

**Step 3 — Sample statistics for the 51 differences:**

12, 8, 15, 10, 14, 9, 13, 11, 16, 12, 10, 14, 13, 9, 12, 15, 11, 13, 14, 10,
12, 11, 15, 13, 14, 11, 12, 14, 13, 10, 11, 14, 12, 13, 15, 11, 12, 14, 13, 10,
12, 14, 13, 11, 12, 15, 13, 12, 14, 11, 13

n = 51 pairs

x̄_d = Σdᵢ / n = 631 / 51 ≈ 12.3725

s_d = √[Σ(dᵢ − x̄_d)² / (n − 1)] ≈ 1.7996

**Step 4 — Standard error:**
SE = s_d / √n = 1.7996 / √51 ≈ 1.7996 / 7.1414 ≈ 0.2520

**Step 5 — t test statistic:**
t = (x̄_d − μ₀) / SE = (12.3725 − 0) / 0.2520 ≈ 49.10

**Step 6 — Degrees of freedom:**
df = n − 1 = 50

**Step 7 — p-value:** For a two-tailed test with df = 50,
p-value = 2 × P(t > 49.10) ≈ 0 (far into the tail)

**Step 8 — Decision:** p-value < 0.05, so **reject H₀**.

**Step 9 — Conclusion:** There is strong evidence at the 5% level that unchecking the software option changes measurement time. The mean difference is about 12.37 units, so the option has a measurable effect.

**Concept note:** Because this is a paired design, we analyze the *differences*, not the two raw columns separately. That controls for part-to-part differences and makes the test more sensitive to the option's effect.

---

## Part F: Two-Sample t Procedures

When data come from two independent samples (or two randomized groups), x̄₁ − x̄₂ estimates μ₁ − μ₂. Since σ₁ and σ₂ are unknown, we estimate them with s₁ and s₂:

SE = √( s₁²/n₁ + s₂²/n₂ )

The two-sample t statistic:

t = (x̄₁ − x̄₂) / √( s₁²/n₁ + s₂²/n₂ )

The statistic follows approximately a t-distribution. Degrees of freedom can be found with software (Welch–Satterthwaite) or conservatively as df = min(n₁ − 1, n₂ − 1).

**Concept link to Day 6:** For independent variables, variances add — Var(X − Y) = σ₁² + σ₂². The two-sample standard error is exactly the square root of that summed variance, scaled by sample size. Standard deviations do *not* add; variances do.

### Example: Directed reading activities

A treatment class (n₁ = 21) uses new directed reading activities for 8 weeks; a control class (n₂ = 23) does not. All students take a DRP reading test.

**Treatment (n₁ = 21):**
24 61 59 46
43 44 52 43
58 67 62 57
71 49 54
43 53 57
49 56 33

**Control (n₂ = 23):**
42 33 46 37
43 41 10 42
55 19 17 55
26 54 60 28
62 20 53 48
37 65 42

### Step-by-step two-sample t test

**Step 1 — Hypotheses:**
H₀: μ₁ − μ₂ = 0 (no treatment effect)
Hₐ: μ₁ − μ₂ > 0 (treatment improves reading)

Right-tailed test.

**Step 2 — Conditions:** Two independent random samples, reasonable sizes (21 and 23), DRP scores approximately normal within each group, samples independent. Met.

**Step 3 — Sample statistics:**

Treatment: sum = 1081, x̄₁ = 1081/21 ≈ 51.4762, s₁ ≈ 11.0074

Control: sum = 935, x̄₂ = 935/23 ≈ 40.6522, s₂ ≈ 15.2453

**Step 4 — Standard error:**
SE = √( s₁²/n₁ + s₂²/n₂ )
= √( 121.1629/21 + 232.4192/23 )
= √( 5.7697 + 10.1052 )
= √15.8749 ≈ 3.9843

**Step 5 — t test statistic:**
t = (x̄₁ − x̄₂) / SE = (51.4762 − 40.6522) / 3.9843 = 10.8240 / 3.9843 ≈ 2.7167

**Step 6 — Degrees of freedom:**
Conservative: df = min(20, 22) = 20

Software (Welch–Satterthwaite):
df = (s₁²/n₁ + s₂²/n₂)² / [ (1/(n₁−1))(s₁²/n₁)² + (1/(n₂−1))(s₂²/n₂)² ]
= (15.8749)² / [ (1/20)(5.7697)² + (1/22)(10.1052)² ]
= 252.0134 / (1.6645 + 4.6458 )
= 252.0134 / 6.3103 ≈ 39.94 → round down to 39

**Step 7 — p-value:**
- Conservative df = 20: p-value = P(t > 2.7167) ≈ 0.0066
- Software df ≈ 39: p-value ≈ 0.0048

**Step 8 — Decision:** Both p-values < 0.05, so **reject H₀** under either df choice.

**Step 9 — Conclusion:** Sufficient evidence at the 5% level that directed reading activities improve reading ability. The treatment group's mean DRP score is significantly higher than the control group's.

---

## Part G: Pooled vs. Unpooled Two-Sample t Tests

There are two versions:

- **Unpooled (unequal variance):** does not assume σ₁ = σ₂. This is what we used above; it is safer because equal variances are hard to verify. df from Welch–Satterthwaite or the conservative min(n₁−1, n₂−1).
- **Pooled (equal variance):** assumes σ₁ = σ₂ and pools the sample variances. It has exactly a t-distribution with df = n₁ + n₂ − 2. Common before computers, but the equal-variance assumption is difficult to check, so the unpooled test is generally preferred.

---

## Key Formulas

| Quantity | Formula | What it is for |
| :--- | :--- | :--- |
| SE (σ known) | σ / √n | Standard error when σ is known |
| Margin of error (Z-interval) | z* × (σ / √n) | Margin of error for a Z-interval |
| Z-interval for μ | x̄ ± z* × (σ / √n) | Z-interval for μ |
| Sample size for margin E | n = (z* × σ / E)² | Sample size for desired margin of error |
| Z-test statistic | z = (x̄ − μ₀) / (σ / √n) | Z-test statistic |
| p-value (left-tailed) | P(Z < z) | Area left of z |
| p-value (right-tailed) | P(Z > z) | Area right of z |
| p-value (two-tailed) | 2 × P(Z > \|z\|) | Twice the area beyond z |
| Power | 1 − β | Probability of correctly rejecting H₀ |
| T score | t = (x̄ − μ) / (s / √n) | T statistic when σ is unknown |
| Degrees of freedom (one mean) | df = n − 1 | df for a single mean / matched pairs |
| SE (σ unknown) | s / √n | Standard error using sample SD |
| T-interval for μ | x̄ ± t* × (s / √n) | T-interval for μ |
| Matched pairs t statistic | t = (x̄_d − μ₀) / (s_d / √n) | Matched pairs t test statistic |
| Matched pairs t-interval | x̄_d ± t* × (s_d / √n) | Matched pairs t-interval |
| Two-sample t statistic | t = (x̄₁ − x̄₂) / √( s₁²/n₁ + s₂²/n₂ ) | Two-sample t test statistic |
| Two-sample t SE | √( s₁²/n₁ + s₂²/n₂ ) | SE of difference in means |
| Two-sample t df (conservative) | min(n₁ − 1, n₂ − 1) | Conservative df |
| Two-sample t df (software) | (s₁²/n₁ + s₂²/n₂)² / [ (1/(n₁−1))(s₁²/n₁)² + (1/(n₂−1))(s₂²/n₂)² ] | Welch–Satterthwaite df |
| Pooled two-sample df | n₁ + n₂ − 2 | df when assuming equal variances |

---

## Practice Problems

**1.** A sample of 36 batteries has mean lifetime 8.2 hours with known σ = 1.5 hours. Construct a 99% confidence interval for the mean lifetime. (z* = 2.576)

<details><summary>Solution</summary>

SE = 1.5 / √36 = 1.5 / 6 = 0.25. E = 2.576 × 0.25 = 0.644. CI = 8.2 ± 0.644 = (7.556, 8.844). We are 99% confident the mean lifetime is between about 7.56 and 8.84 hours.

</details>

**2.** A machine is supposed to fill bottles with 16 oz. σ = 0.1 known. A sample of 25 has mean 15.97 oz. Test at α = 0.05 whether the mean is less than 16.

<details><summary>Solution</summary>

H₀: μ = 16, Hₐ: μ < 16 (left-tailed). z = (15.97 − 16) / (0.1 / √25) = −0.03 / 0.02 = −1.50. p-value = P(Z < −1.50) ≈ 0.0668. Since 0.0668 > 0.05, fail to reject H₀. Not enough evidence the machine is underfilling.

</details>

**3.** Ten students take a test before and after a study session. The differences (after − before) have x̄_d = 4.2 and s_d = 3.1. Construct a 95% CI for the mean improvement. df = 9, t* = 2.262.

<details><summary>Solution</summary>

SE = 3.1 / √10 ≈ 0.9803. ME = 2.262 × 0.9803 ≈ 2.217. CI = 4.2 ± 2.217 = (1.983, 6.417). We are 95% confident the mean improvement is between about 1.98 and 6.42 points; since the interval excludes 0, there is evidence of improvement.

</details>

**4.** Two independent samples: n₁ = 15, x̄₁ = 50, s₁ = 8; n₂ = 12, x̄₂ = 44, s₂ = 10. Compute the two-sample t statistic and the conservative df.

<details><summary>Solution</summary>

SE = √( 8²/15 + 10²/12 ) = √( 64/15 + 100/12 ) = √( 4.2667 + 8.3333 ) = √12.6 ≈ 3.5496. t = (50 − 44) / 3.5496 = 6 / 3.5496 ≈ 1.69. Conservative df = min(14, 11) = 11.

</details>

**5.** Why does the t-distribution have heavier tails than the standard normal, and what happens as df grows?

<details><summary>Solution</summary>

Because s is used in place of the unknown σ, extra estimation uncertainty enters, especially for small samples. Heavier tails produce wider intervals and more conservative tests to compensate. As df grows, s becomes a more stable estimate of σ, and the t-distribution converges to the standard normal.

</details>

### Multiple Choice

**6.** Which condition is required for a Z-interval for μ but NOT for a t-interval for μ?

- a) Random sample
- b) n ≥ 30 or normal population
- c) Known population standard deviation σ
- d) Independence (10n ≤ N)

<details><summary>Solution</summary>

Z-intervals require σ to be known; t-intervals estimate σ with s, so known σ is not required.

**Final answer: c) Known population standard deviation σ**

</details>

**7.** For a matched pairs test with n = 20 pairs, the degrees of freedom are:

- a) 19
- b) 20
- c) 39
- d) 38

<details><summary>Solution</summary>

Matched pairs reduce to a one-sample t on the differences, so df = n − 1 = 19.

**Final answer: a) 19**

</details>

**8.** Power = 1 − β increases when:

- a) n decreases
- b) σ increases
- c) α increases
- d) the true effect moves closer to θ₀

<details><summary>Solution</summary>

Power rises when n rises, σ falls, α rises, or the true effect is farther from θ₀. Among the options, only increasing α raises power.

**Final answer: c) α increases**

</details>
