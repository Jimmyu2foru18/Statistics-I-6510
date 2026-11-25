# Statistics I, Day 12: Regression Inference — ANOVA, Sum of Squares, Confidence and Prediction Intervals

Welcome to Day 12! Day 11 covered chi-squared tests for categorical data. Today we return to quantitative relationships and cover inference for simple linear regression: the ANOVA decomposition of total variation into sum of squares, the F test for a useful linear relationship, r and r², confidence intervals for the mean response, and prediction intervals for an individual future response — including lower and upper bounds for each.

---

## Part A: Simple Linear Regression Review

The population regression line:

ŷ = β₀ + β₁x

The fitted (sample) regression line:

ŷ = b₀ + b₁x

where:
- b₁ = slope, the estimated change in mean y per one-unit increase in x
- b₀ = y-intercept, the estimated mean y when x = 0
- x = explanatory variable, y = response variable

Conditions for regression inference:
1. **Linear:** the true relationship is roughly linear (check the scatterplot and residual plot).
2. **Independent:** observations are independent (random sample or randomized experiment, 10% condition).
3. **Normal:** for any fixed x, y varies normally around the regression line (check a histogram/NPP of residuals).
4. **Equal spread:** the standard deviation σ of y around the line is the same for all x (residual plot shows no fan shape).
5. **Random:** data come from a random sample or randomized experiment.

Degrees of freedom for regression inference: df = n − 2.

---

## Part B: ANOVA for Regression — Sum of Squares

ANOVA (analysis of variance) partitions the total variation in y into variation explained by the regression line and variation left unexplained (residuals).

### Definitions

For each observation i with fitted value ŷᵢ and residual eᵢ = yᵢ − ŷᵢ:

- **SST** (Total Sum of Squares) = Σ(yᵢ − ȳ)² — total variation in y about its mean.
- **SSR** (Regression Sum of Squares) = Σ(ŷᵢ − ȳ)² — variation explained by the regression line.
- **SSE** (Error/Residual Sum of Squares) = Σ(yᵢ − ŷᵢ)² = Σeᵢ² — unexplained variation.

Identity:

SST = SSR + SSE

### Degrees of freedom

| Source | df |
| :--- | :--- |
| Regression | 1 |
| Error (Residual) | n − 2 |
| Total | n − 1 |

### Mean Squares

- MSR = SSR / 1 = SSR
- MSE = SSE / (n − 2) = s², the estimated variance of the residuals

The regression standard error:

s = √MSE = √(SSE / (n − 2))

This estimates σ, the standard deviation of y values around the true regression line.

### Coefficient of determination r²

r² = SSR / SST = 1 − SSE / SST

r² is the fraction of variation in y explained by the regression on x. The correlation r = sign(b₁) × √r².

### ANOVA table for regression

| Source | df | SS | MS | F |
| :--- | :--- | :--- | :--- | :--- |
| Regression | 1 | SSR | MSR = SSR/1 | F = MSR/MSE |
| Error | n − 2 | SSE | MSE = SSE/(n−2) | |
| Total | n − 1 | SST | | |

### F test for a useful linear regression

H₀: β₁ = 0 (no linear relationship)
Hₐ: β₁ ≠ 0 (linear relationship; two-tailed)

F = MSR / MSE

Under H₀, F follows an F-distribution with df = (1, n − 2). Reject H₀ when F is large (p-value < α). Note: for simple linear regression, this F test is equivalent to the two-tailed t test for the slope, with F = t².

---

## Part C: Worked Example — Regression ANOVA

A random sample of n = 10 students: hours studied (x) vs. exam score (y).

Summary statistics:
- n = 10
- ȳ = 78.2, SST = 1240
- Regression line: ŷ = 65 + 4x
- SSR = 930
- SSE = 310

Check: SST = SSR + SSE → 930 + 310 = 1240 ✓

### ANOVA quantities

df regression = 1, df error = 10 − 2 = 8, df total = 9

MSR = SSR / 1 = 930
MSE = SSE / 8 = 310 / 8 = 38.75
s = √38.75 ≈ 6.22

r² = SSR / SST = 930 / 1240 = 0.75 → 75% of the variation in exam scores is explained by hours studied.

r = +√0.75 ≈ 0.866 (positive slope).

### F test

F = MSR / MSE = 930 / 38.75 = 24.0

df = (1, 8). Critical F at α = 0.05 is about 5.32. Since 24.0 > 5.32, **reject H₀**. There is strong evidence of a useful linear relationship between hours studied and exam score. (Equivalently, the t statistic for the slope is √24.0 ≈ 4.90.)

---

## Part D: Confidence Interval for the Mean Response

A confidence interval estimates the mean response μ_y|x for *all* individuals with a given explanatory value x₀:

ŷ₀ ± t* × SE(μ̂)

where ŷ₀ = b₀ + b₁x₀ is the predicted mean at x₀, and

SE(μ̂) = s × √[ 1/n + (x₀ − x̄)² / Σ(xᵢ − x̄)² ]

df = n − 2, t* from the t-distribution for the desired confidence level.

### Bounds

- **Lower bound:** ŷ₀ − t* × SE(μ̂)
- **Upper bound:** ŷ₀ + t* × SE(μ̂)

### Interpretation

We are C% confident the true mean response for all individuals with x = x₀ lies between the lower and upper bounds.

### Key property

The confidence interval is narrowest at x₀ = x̄ and grows wider as x₀ moves farther from x̄ (extrapolation increases uncertainty).

---

## Part E: Prediction Interval for an Individual Response

A prediction interval estimates a single future response y for one individual with x = x₀:

ŷ₀ ± t* × SE(ŷ)

where

SE(ŷ) = s × √[ 1 + 1/n + (x₀ − x̄)² / Σ(xᵢ − x̄)² ]

The extra "1 +" inside the square root accounts for the variability of an individual observation around the mean response.

### Bounds

- **Lower bound:** ŷ₀ − t* × SE(ŷ)
- **Upper bound:** ŷ₀ + t* × SE(ŷ)

### Interpretation

We are C% confident that the response for a *single future individual* with x = x₀ will fall between the lower and upper bounds.

### CI vs. PI

The prediction interval is always wider than the confidence interval for the same x₀ and confidence level, because predicting an individual value includes both uncertainty about the mean line and natural scatter of individual points around the line.

---

## Part F: Worked Example — CI and PI

Continue the study-hours example: n = 10, x̄ = 5 hours, Σ(xᵢ − x̄)² = 20, s = 6.22, regression ŷ = 65 + 4x.

Find intervals for x₀ = 6 hours at 95% confidence. df = 8, t*₀.₀₂₅,₈ = 2.306.

Predicted mean: ŷ₀ = 65 + 4(6) = 89.

### Confidence interval for the mean score at x₀ = 6

SE(μ̂) = 6.22 × √[ 1/10 + (6 − 5)² / 20 ]
= 6.22 × √[ 0.10 + 1/20 ]
= 6.22 × √[ 0.10 + 0.05 ]
= 6.22 × √0.15 ≈ 6.22 × 0.3873 ≈ 2.41

ME = 2.306 × 2.41 ≈ 5.56

- Lower bound: 89 − 5.56 = 83.44
- Upper bound: 89 + 5.56 = 94.56

95% CI for the mean score of all students who study 6 hours: **(83.44, 94.56)**.

### Prediction interval for one student who studies 6 hours

SE(ŷ) = 6.22 × √[ 1 + 1/10 + (6 − 5)² / 20 ]
= 6.22 × √[ 1 + 0.10 + 0.05 ]
= 6.22 × √1.15 ≈ 6.22 × 1.0724 ≈ 6.67

ME = 2.306 × 6.67 ≈ 15.38

- Lower bound: 89 − 15.38 = 73.62
- Upper bound: 89 + 15.38 = 104.38

95% prediction interval for one student who studies 6 hours: **(73.62, 104.38)**.

The prediction interval is much wider than the confidence interval, as expected.

---

## Part G: Calculator / TI-84 Steps

1. Enter x in L1 and y in L2.
2. STAT → CALC → LinRegTTest to get b₀, b₁, r, r², and the t test for the slope.
3. For predictions at x₀:
   - Store the regression equation: STAT → CALC → LinReg(a+bx) → Y1.
   - Compute ŷ₀ = Y1(x₀).
4. Standard errors and intervals are easiest with software output; on the TI-84, compute SE by hand using the formulas above with s from the LinRegTTest output and Σ(xᵢ − x̄)² from 1-Var Stats on L1.

---

## Key Formulas

| Quantity | Formula |
| :--- | :--- |
| Regression line | ŷ = b₀ + b₁x |
| Total SS | SST = Σ(yᵢ − ȳ)² |
| Regression SS | SSR = Σ(ŷᵢ − ȳ)² |
| Error SS | SSE = Σ(yᵢ − ŷᵢ)² = Σeᵢ² |
| ANOVA identity | SST = SSR + SSE |
| r² | SSR / SST = 1 − SSE/SST |
| Regression standard error | s = √(SSE / (n − 2)) |
| F statistic | F = MSR / MSE = SSR / [SSE/(n − 2)] |
| SE of mean response | s × √[ 1/n + (x₀ − x̄)² / Σ(xᵢ − x̄)² ] |
| SE of individual prediction | s × √[ 1 + 1/n + (x₀ − x̄)² / Σ(xᵢ − x̄)² ] |
| CI bounds (mean) | ŷ₀ ± t* × SE(μ̂) |
| PI bounds (individual) | ŷ₀ ± t* × SE(ŷ) |
| df | n − 2 |

---

## Practice Problems

**1.** For a regression on n = 12 observations, SST = 500 and SSE = 150. Find SSR, r², and s.

<details><summary>Solution</summary>

SSR = SST − SSE = 500 − 150 = 350. r² = 350/500 = 0.70. s = √(150 / (12 − 2)) = √15 ≈ 3.87.

</details>

**2.** A regression has n = 15, x̄ = 10, Σ(xᵢ − x̄)² = 40, s = 5, and regression line ŷ = 20 + 3x. Find the 95% CI for the mean response at x₀ = 12. df = 13, t* = 2.160.

<details><summary>Solution</summary>

ŷ₀ = 20 + 3(12) = 56. SE(μ̂) = 5 × √[ 1/15 + (12 − 10)² / 40 ] = 5 × √[ 0.0667 + 4/40 ] = 5 × √[ 0.0667 + 0.10 ] = 5 × √0.1667 ≈ 5 × 0.4082 ≈ 2.04. ME = 2.160 × 2.04 ≈ 4.41. Lower = 56 − 4.41 = 51.59, Upper = 56 + 4.41 = 60.41. CI: (51.59, 60.41).

</details>

**3.** Using problem 2's values, find the 95% prediction interval for one individual at x₀ = 12.

<details><summary>Solution</summary>

SE(ŷ) = 5 × √[ 1 + 1/15 + 4/40 ] = 5 × √[ 1 + 0.0667 + 0.10 ] = 5 × √1.1667 ≈ 5 × 1.0801 ≈ 5.40. ME = 2.160 × 5.40 ≈ 11.66. Lower = 56 − 11.66 = 44.34, Upper = 56 + 11.66 = 67.66. PI: (44.34, 67.66) — wider than the CI, as expected.

</details>

**4.** True or false: A prediction interval for an individual response is always wider than the confidence interval for the mean response at the same x₀ and confidence level.

<details><summary>Solution</summary>

True. The prediction SE includes the extra "+1" for individual variability, so its margin of error is larger.

</details>

**5.** In regression ANOVA, which sum of squares measures variation explained by the regression line?

<details><summary>Solution</summary>

SSR (Regression Sum of Squares) = Σ(ŷᵢ − ȳ)².

</details>

### Multiple Choice

**6.** The degrees of freedom for error in a simple linear regression with n = 20 observations are:

- a) 18
- b) 19
- c) 20
- d) 21

<details><summary>Solution</summary>

df error = n − 2 = 18.

**Final answer: a) 18**

</details>

**7.** At the same x₀ and confidence level, the margin of error for a prediction interval is:

- a) smaller than for a confidence interval
- b) equal to a confidence interval
- c) larger than for a confidence interval
- d) unrelated

<details><summary>Solution</summary>

The prediction SE includes an extra "+1" for individual scatter, so the prediction margin of error is larger.

**Final answer: c) larger than for a confidence interval**

</details>

**8.** If r² = 0.64 in a regression with a positive slope, what is r?

<details><summary>Solution</summary>

r = +√0.64 = 0.8 (positive because the slope is positive).

**Final answer: r = 0.8**

</details>
