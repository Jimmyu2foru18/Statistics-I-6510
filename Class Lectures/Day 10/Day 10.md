# Statistics I, Day 10: One-Sample and Two-Sample t Procedures, Matched Pairs, and Inference for Proportions

Welcome to Day 10! Day 9 finished z-procedures (σ known) and introduced t-procedures (σ unknown, estimated by s). Today we apply one-sample and two-sample t tests and confidence intervals to means, revisit matched pairs, and then begin Chapter 8: inference for a population proportion, where the parameter is p instead of μ and the test statistic is a z-score built from the sample proportion.

Throughout, "with α = 0.05" is assumed wherever the worksheet leaves the significance level blank, and confidence levels are stated explicitly (95% unless noted otherwise).

---

## Part A: One-Sample t Test and t-Interval (Apple Tree Yield)

Past research: mean yield μ₀ = 34.2 apples per year. You believe weather changes have *increased* this.

Sample of n = 15 trees: x̄ = 37.3 apples, s = 4.1 apples. Yield is approximately normal, σ is unknown → use a **one-sample t test**, df = n − 1 = 14.

### Step 1: Hypotheses

- H₀: μ = 34.2 (no increase)
- Hₐ: μ > 34.2 (increase; right-tailed test)

### Step 2: Check conditions

- **Random sample:** stated random sample of 15 trees. ✓
- **Normality:** apple yield is assumed normally distributed, so t procedures are valid even with n = 15. ✓
- **Independence:** 15 trees is well under 10% of the population of trees. ✓
- **σ unknown:** use s, so t (not z). ✓

### Step 3: Test statistic

Standard error:

SE = s / √n = 4.1 / √15 ≈ 4.1 / 3.8730 ≈ 1.0586

t = (x̄ − μ₀) / SE = (37.3 − 34.2) / 1.0586 = 3.1 / 1.0586 ≈ 2.93

df = 14.

### Step 4: Critical value and p-value

Right-tailed test at α = 0.05, df = 14:

Critical value t* = 1.761 (area 0.9500 to the left).

Since 2.93 > 1.761, the test statistic is in the rejection region.

p-value = P(t₁₄ > 2.93). From the t-table, this falls between 0.005 and 0.01; more precisely p ≈ 0.005.

### Step 5: Decision

p ≈ 0.005 < 0.05, so **reject H₀**. (Equivalently, 2.93 > 1.761.)

### Step 6: Conclusion

There is sufficient evidence at the 5% level to conclude that the mean apple yield has increased above 34.2 apples per year.

---

### One-sample 95% confidence interval for μ

CI = x̄ ± t* × (s / √n), df = 14, two-tailed t* for 95% = 2.145.

ME = 2.145 × 1.0586 ≈ 2.27

CI = 37.3 ± 2.27 = **(35.03, 39.57)** apples.

We are 95% confident the true mean yield is between 35.03 and 39.57 apples per year. Note that 34.2 is *outside* this interval, which agrees with rejecting H₀: μ = 34.2 — this is the CI/test duality from Day 9.

**Concept note:** With n = 15 we rely on the normality assumption because the CLT does not yet guarantee a normal sampling distribution. That is why the worksheet explicitly states "Assuming apple yield is normally distributed."

---

## Part B: Two-Sample t Test and CI (Math Learning Software)

New program group (1): n₁ = 20, x̄₁ = 79, s₁ = 3.4
Traditional group (2): n₂ = 23, x̄₂ = 77, s₂ = 4.9
Scores approximately normal; independent samples; σ₁, σ₂ unknown → unpooled two-sample t test.

We test for a *difference* (direction not specified), so this is two-tailed.

### Step 1: Hypotheses

- H₀: μ₁ − μ₂ = 0
- Hₐ: μ₁ − μ₂ ≠ 0 (two-tailed)

### Step 2: Check conditions

- Two independent random samples. ✓
- Both sample sizes reasonable (20 and 23). ✓
- Scores approximately normal within each group. ✓
- Independent samples. ✓

### Step 3: Test statistic

Standard error of the difference:

SE = √( s₁²/n₁ + s₂²/n₂ )
= √( 3.4²/20 + 4.9²/23 )
= √( 11.56/20 + 24.01/23 )
= √( 0.5780 + 1.0439 )
= √1.6219 ≈ 1.2735

t = (x̄₁ − x̄₂) / SE = (79 − 77) / 1.2735 = 2 / 1.2735 ≈ 1.57

### Step 4: Degrees of freedom and critical value

Conservative df = min(n₁ − 1, n₂ − 1) = min(19, 22) = 19.

(Software/Welch–Satterthwaite df ≈ 39, which gives essentially the same conclusion.)

Two-tailed α = 0.05, df = 19: critical values t = ±2.093.

Since |1.57| < 2.093, the statistic is not in the rejection region.

p-value (two-tailed, df = 19): P(|t| > 1.57) ≈ 0.14.

### Step 5: Decision

p ≈ 0.14 > 0.05, so **fail to reject H₀**.

### Step 6: Conclusion

There is **not enough evidence** at the 5% level to conclude a significant difference in mean scores between the new program and traditional methods.

---

### 90% confidence interval for μ₁ − μ₂

CI = (x̄₁ − x̄₂) ± t* × SE, with conservative df = 19.

For 90% confidence (two-tailed α = 0.10), t*₍₀.₀₅₎ with df = 19 is 1.729.

ME = 1.729 × 1.2735 ≈ 2.20

CI = 2 ± 2.20 = **(−0.20, 4.20)** points.

We are 90% confident the true difference (new − traditional) is between about −0.20 and 4.20 points. Because the interval contains 0, it agrees with failing to reject H₀: μ₁ − μ₂ = 0.

(Using software df ≈ 39 gives t* ≈ 1.685 and CI ≈ (−0.15, 4.15) — same conclusion.)

**Concept link to Day 6:** For independent variables, variances add: Var(X̄₁ − X̄₂) = σ₁²/n₁ + σ₂²/n₂. The two-sample standard error is the square root of that summed variance. Standard deviations do not add — variances do.

---

### Matched-pairs alternative (Part c)

Instead of two independent groups, a matched-pairs (paired) design would:

1. Take one sample of students.
2. Give each a pretest, then have them use the new program, then give a posttest.
3. Compute each student's difference d = post − pre.
4. Run a **one-sample t test** on the differences: H₀: μ_d = 0, Hₐ: μ_d ≠ 0.

**Why this can be more powerful:** pairing removes between-student variability (some students are simply better at math regardless of method), so the analysis isolates the program's effect. This is the same matched-pairs idea from Day 9, applied to a pretest/posttest design.

---

## Part C: Chapter 8 — Inference for a Proportion (Sunblock Example)

The parameter is now a population proportion p instead of a mean μ.

Your company claims its sunblock gives superior protection vs. a competitor. Of n = 20 randomly chosen subjects, x = 13 preferred your product; p̂ = 13/20 = 0.65.

Test: H₀: p = 0.5, Hₐ: p > 0.5 (right-tailed; "superior" means better than chance).

### Conditions for a one-sample z test for a proportion

- **Random:** subjects randomly chosen. ✓
- **Normal (sampling distribution of p̂):** under H₀, expected successes = np₀ = 20(0.5) = 10 and expected failures = n(1−p₀) = 10. Both ≥ 10, so normal calculations are safe (barely). ✓
- **Independence:** 20 subjects < 10% of the population. ✓

**CLT for proportions:** if np ≥ 10 and n(1−p) ≥ 10, then p̂ ~ N(p, √(p(1−p)/n)) approximately.

### Test statistic

SE under H₀ uses p₀ (not p̂):

SE = √( p₀(1 − p₀) / n ) = √( 0.5 × 0.5 / 20 ) = √0.0125 ≈ 0.1118

z = (p̂ − p₀) / SE = (0.65 − 0.50) / 0.1118 = 0.15 / 0.1118 ≈ 1.34

### p-value and decision

Right-tailed p-value = P(Z > 1.34) ≈ 1 − 0.9099 = 0.0901.

At α = 0.05, p ≈ 0.09 > 0.05, so **fail to reject H₀**.

**Conclusion:** There is not enough evidence to support a commercial claim that your product provides superior protection. The observed 65% could readily arise by chance when the true rate is 50%.

**Key difference from means tests:** for proportions we do not need a separate s — the standard deviation is determined by p₀ under H₀ via √(p₀(1−p₀)/n). That is why the test statistic is a z-score even though σ is unknown.

---

## Key Formulas

| Quantity | Formula | What it is for |
| :--- | :--- | :--- |
| One-sample t statistic | t = (x̄ − μ₀) / (s / √n) | Test μ when σ unknown |
| One-sample t df | df = n − 1 | One-sample / matched pairs |
| t-interval for μ | x̄ ± t* × (s / √n) | CI for μ, σ unknown |
| Two-sample t statistic | t = (x̄₁ − x̄₂) / √( s₁²/n₁ + s₂²/n₂ ) | Test μ₁ − μ₂, independent samples |
| Two-sample t SE | √( s₁²/n₁ + s₂²/n₂ ) | SE of difference in means |
| Two-sample t df (conservative) | min(n₁ − 1, n₂ − 1) | Conservative df |
| Two-sample t df (software) | (s₁²/n₁ + s₂²/n₂)² / [ (1/(n₁−1))(s₁²/n₁)² + (1/(n₂−1))(s₂²/n₂)² ] | Welch–Satterthwaite df |
| Matched pairs t statistic | t = (x̄_d − μ₀) / (s_d / √n) | One-sample t on differences |
| SE of p̂ (under H₀) | √( p₀(1 − p₀) / n ) | Proportion z test, σ set by p₀ |
| One-proportion z statistic | z = (p̂ − p₀) / √( p₀(1 − p₀) / n ) | Test a population proportion |
| Normal condition (proportions) | np₀ ≥ 10 and n(1 − p₀) ≥ 10 | Sampling distribution of p̂ approx. normal |

---

## Practice Problems

**1.** A sample of n = 16 students has mean exam score 78 with s = 6. Test at α = 0.05 whether the mean score differs from 75. Assume normality.

<details><summary>Solution</summary>

Two-tailed: H₀: μ = 75, Hₐ: μ ≠ 75. SE = 6/√16 = 1.5. t = (78−75)/1.5 = 2.00. df = 15. Critical two-tailed t₀.₀₂₅,₁₅ = ±2.131. |2.00| < 2.131, fail to reject H₀. p-value (two-tailed) ≈ 0.061 > 0.05. Not enough evidence the mean differs from 75.

</details>

**2.** Construct a 90% CI for the mean in problem 1.

<details><summary>Solution</summary>

df = 15, t*₍₀.₀₅₎ = 1.753. ME = 1.753 × 1.5 = 2.63. CI = 78 ± 2.63 = (75.37, 80.63). Since 75 is just outside, this is consistent with the borderline test result.

</details>

**3.** Two independent samples: n₁ = 12, x̄₁ = 55, s₁ = 7; n₂ = 14, x̄₂ = 50, s₂ = 9. Test H₀: μ₁ − μ₂ = 0 vs Hₐ: μ₁ − μ₂ > 0 at α = 0.05.

<details><summary>Solution</summary>

SE = √(49/12 + 81/14) = √(4.083 + 5.786) = √9.869 ≈ 3.142. t = (55−50)/3.142 = 1.59. Conservative df = min(11,13) = 11. Right-tailed critical t₀.₀₅,₁₁ = 1.796. 1.59 < 1.796, fail to reject H₀. p-value ≈ 0.073 > 0.05. Not enough evidence group 1 is higher.

</details>

**4.** Of 40 customers, 28 prefer a new website design. Test at α = 0.05 whether more than half prefer it (Hₐ: p > 0.5).

<details><summary>Solution</summary>

p̂ = 28/40 = 0.70. np₀ = 40(0.5) = 20, n(1−p₀) = 20, both ≥ 10 ✓. SE = √(0.5×0.5/40) = √0.00625 = 0.07906. z = (0.70−0.50)/0.07906 = 2.53. p-value = P(Z > 2.53) ≈ 0.0057. 0.0057 < 0.05, reject H₀. Sufficient evidence more than half prefer the new design.

</details>

### Multiple Choice

**5.** For a one-sample t test with n = 15, the degrees of freedom are:

- a) 14
- b) 15
- c) 16
- d) 30

<details><summary>Solution</summary>

df = n − 1 = 14 for a single mean.

**Final answer: a) 14**

</details>

**6.** In a two-sample t test, which quantity adds (rather than the standard deviations adding)?

- a) Means
- b) Standard deviations
- c) Variances
- d) Sample sizes

<details><summary>Solution</summary>

For independent samples, Var(X̄₁ − X̄₂) = σ₁²/n₁ + σ₂²/n₂ — variances add; SE is the square root of the sum.

**Final answer: c) Variances**

</details>

**7.** For a one-proportion z test, the standard error is computed using:

- a) p̂
- b) p₀ (the null value)
- c) s
- d) σ

<details><summary>Solution</summary>

Under H₀, p̂ ~ N(p₀, √(p₀(1−p₀)/n)), so the SE uses p₀.

**Final answer: b) p₀ (the null value)**

</details>

**8.** A 90% CI for μ₁ − μ₂ is (−0.20, 4.20). What is the decision for a two-tailed test of H₀: μ₁ − μ₂ = 0 at α = 0.10?

<details><summary>Solution</summary>

0 is inside the 90% CI, which corresponds to α = 0.10 two-tailed, so fail to reject H₀. The CI/test duality holds: C = 1 − α.

**Final answer: Fail to reject H₀**

</details>
