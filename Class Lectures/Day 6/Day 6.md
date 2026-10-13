# Statistics I, Day 6: Linear Combinations of Random Variables & the Binomial Distribution

## Overview
So far we've summarized *data*. Now we work with **random variables** and their distributions. Today covers two topics:
1. How the **mean and variance** behave when we add, subtract, or scale random variables (**Rules for Means and Variances**).
2. The **binomial distribution**: the model for counting successes in a fixed number of yes/no trials.

*Source cross-checked against the course slides (Moore/McCabe/Craig, Ch. 4 & "Sampling Distributions").*

---

## Part A: Rules for Linear Combinations of Random Variables

Let $X$ and $Y$ be random variables with means $\mu_X = E(X)$, $\mu_Y = E(Y)$ and variances $\sigma_X^2 = \text{Var}(X)$, $\sigma_Y^2 = \text{Var}(Y)$.

### Rules for Means

- **Rule 1** (scale & shift): if $a$ and $b$ are fixed numbers, $\;E(a + bX) = a + b\,\mu_X$
- **Rule 2** (sum): $\;E(X + Y) = \mu_X + \mu_Y$
- **Rule 3** (difference): $\;E(X - Y) = \mu_X - \mu_Y$

### Rules for Variances and Standard Deviations

- **Rule 1** (scale & shift): $\;\text{Var}(a + bX) = b^{2}\,\sigma_X^{2}$. A shift $a$ does nothing; a scale $b$ multiplies variance by $b^2$.
- **Rule 2** (independent $X, Y$): $\;\text{Var}(X \pm Y) = \sigma_X^{2} + \sigma_Y^{2}$
- **Rule 3** (with correlation $\rho$): $\;\text{Var}(X \pm Y) = \sigma_X^{2} + \sigma_Y^{2} \pm 2\rho\,\sigma_X\sigma_Y$

> **Crucial takeaway #1:** For a **difference** $X - Y$, the **means subtract** but the **variances still add** ($\sigma_X^2 + \sigma_Y^2$). Uncertainty grows when you combine random variables; it does not cancel.

> **Crucial takeaway #2:** To get the **standard deviation** of a combination, take the square root of the summed variances:
> $$sd(X \pm Y) = \sqrt{\sigma_X^2 + \sigma_Y^2} \quad \neq \ \sigma_X \pm \sigma_Y$$
> Standard deviations **do not** simply add or subtract.

*(Rule 3 generalizes Rule 2: when $X$ and $Y$ are independent, $\rho = 0$, so the cross-term $2\rho\sigma_X\sigma_Y$ vanishes and we recover $\sigma_X^2 + \sigma_Y^2$.)*

### Worked Example

Let $X$ have mean $\mu_X = 10$ and SD $\sigma_X = 3$; let $Y$ have mean $\mu_Y = 6$ and SD $\sigma_Y = 2$; and suppose $X, Y$ are **independent**. Find the mean and SD of (a) $X + Y$ and (b) $X - Y$.

**(a) $X + Y$:**
$$\text{Mean} = 10 + 6 = 16, \qquad \text{Var} = 3^2 + 2^2 = 9 + 4 = 13, \qquad SD = \sqrt{13} \approx 3.61$$

**(b) $X - Y$:**
$$\text{Mean} = 10 - 6 = 4, \qquad \text{Var} = 3^2 + 2^2 = 13, \qquad SD = \sqrt{13} \approx 3.61$$

Notice the **means differ** ($16$ vs. $4$) but the **spread is identical** because variances always add.

---

## Part B: The Binomial Distribution

A random variable $X$ counts the number of **"successes"** in a fixed number of trials. It is **binomial** when all four conditions (remember **BINS**) hold:

| Letter | Condition | In plain terms |
| :---: | :--- | :--- |
| **B** | **Binary** | Each trial has exactly two outcomes: *success* (prob. $p$) or *failure* (prob. $1-p$). |
| **I** | **Independent** | Trials are independent; one result does not affect another. |
| **N** | **Number** | The number of trials $n$ is fixed in advance. |
| **S** | **Success** | The probability of success $p$ is the same on every trial. |

Notation: $X \sim \text{Binomial}(n, p)$, taking whole-number values $0, 1, \dots, n$.

### Formulas

- **Probability of exactly $k$ successes:**
  $$P(X = k) = \binom{n}{k}\,p^{k}(1-p)^{\,n-k} \quad \text{where } \binom{n}{k} = \frac{n!}{k!\,(n-k)!}$$
  ($\binom{n}{k}$ counts the different arrangements of $k$ successes among $n$ trials; $0! = 1$.)

- **Mean (expected successes):** $\quad \mu = n\,p$
- **Variance:** $\quad \sigma^{2} = n\,p\,(1-p)$
- **Standard deviation:** $\quad \sigma = \sqrt{n\,p\,(1-p)}$

> **Note:** The mean/SD formulas $\mu = np$ and $\sigma = \sqrt{np(1-p)}$ work **only** for binomial variables; don't apply them to other distributions.

> On a graphing calculator: `binompdf(n,p,k)` = $P(X=k)$; `binomcdf(n,p,k)` = $P(X \le k)$.

---

### Worked Example: Defective Lightbulbs

A machine produces lightbulbs. Each bulb has a **3% chance** of being defective. Let $X$ = number of defective bulbs in a batch of $n = 200$.

**Check BINS:**
- **B**inary: defective (success) or not (failure).
- **I**ndependent: one bulb's outcome doesn't affect another's.
- **N**umber: fixed $n = 200$.
- **S**uccess: constant $p = 0.03$.

So $X \sim \text{Binomial}(200,\, 0.03)$.

**(a) Mean and standard deviation:**
$$\mu = np = 200(0.03) = 6$$
$$\sigma = \sqrt{np(1-p)} = \sqrt{200(0.03)(0.97)} = \sqrt{5.82} \approx 2.41$$

**(b) Exactly 5 defective:**
$$P(X = 5) = \binom{200}{5}(0.03)^{5}(0.97)^{195} = \texttt{binompdf}(200, 0.03, 5) \approx 0.1623$$

**(c) 3 or fewer defective:**
$$P(X \le 3) = \texttt{binomcdf}(200, 0.03, 3) \approx 0.1472$$

---

## Key Formulas

| Quantity | LaTeX | Plain / in words |
| :--- | :--- | :--- |
| Mean of $a+bX$ | $\mu_{a+bX} = a + b\mu_X$ | start with μₓ, multiply by b, add a |
| Mean of $X\pm Y$ | $\mu_{X\pm Y} = \mu_X \pm \mu_Y$ | add/subtract the two means |
| Var of $a+bX$ | $\sigma^2_{a+bX} = b^{2}\sigma_X^{2}$ | multiply variance by b² (shift a ignored) |
| Var of $X\pm Y$ (indep.) | $\sigma^{2}_{X\pm Y} = \sigma_X^{2} + \sigma_Y^{2}$ | **add** the two variances (even for a difference) |
| SD of a combination | $\sqrt{\sigma_X^2 + \sigma_Y^2}$ | square root of the summed variances |
| Binomial PMF | $\binom{n}{k}p^{k}(1-p)^{n-k}$ | (n choose k) × pᵏ × (1−p)^(n−k) |
| Binomial mean | $np$ | trials × success probability |
| Binomial SD | $\sqrt{np(1-p)}$ | √(npq), q = 1 − p |

---

## Practice Problems

**1.** Let $A$ have mean $50$ and SD $8$; let $B$ have mean $30$ and SD $5$; assume $A, B$ independent. Find the mean and SD of $A - B$.

<details><summary>Solution</summary>

Mean $= 50 - 30 = 20$. Variance $= 8^2 + 5^2 = 64 + 25 = 89$; SD $= \sqrt{89} \approx 9.43$.

</details>

**2.** A fair coin is flipped $n = 40$ times; let $X$ = number of heads. Find $\mu$ and $\sigma$.

<details><summary>Solution</summary>

$p = 0.5$. $\mu = np = 40(0.5) = 20$; $\sigma = \sqrt{np(1-p)} = \sqrt{40(0.5)(0.5)} = \sqrt{10} \approx 3.16$.

</details>

**3.** Using the fair-coin setup above, find $P(X \le 15)$.

<details><summary>Solution</summary>

`binomcdf(40, 0.5, 15)` $\approx 0.0769$ (about $7.7\%$).

</details>

**4.** Why can't we compute the mean of $X$ as $np$ if $X$ counts something that is *not* binomial (e.g., a Poisson count)?

<details><summary>Solution</summary>

$\mu = np$ and $\sigma = \sqrt{np(1-p)}$ are valid **only** for binomial variables. Other distributions have their own mean formulas (e.g., Poisson mean $= \lambda$).

</details>

### Multiple Choice

**5.** $X$ and $Y$ are independent with $\text{Var}(X) = 4$ and $\text{Var}(Y) = 9$. What is $\text{Var}(X + Y)$?

- **a)** 5
- **b)** 13
- **c)** 6
- **d)** 36

<details><summary>Solution</summary>

- For independent variables, variances add for any linear combination.
- $\text{Var}(X + Y) = 4 + 9 = 13$.

**Final answer: (b) 13**

</details>

**6.** Let $X$ be binomial with $n = 10$ trials and success probability $p = 0.5$. The mean of $X$ is:

- **a)** 5
- **b)** 2.5
- **c)** 0.5
- **d)** 10

<details><summary>Solution</summary>

- The binomial mean equals $np$.
- Mean $= 10 \times 0.5 = 5$.

**Final answer: (a) 5**

</details>
