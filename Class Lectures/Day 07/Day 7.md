# Statistics I, Day 7: Expected Value, Poisson, Continuous Distributions, and Sampling

Welcome to Day 7! Today gathers several bridging ideas between descriptive statistics and inference:

1. Expected value and standard deviation of a discrete distribution.
2. More binomial probability calculations.
3. The Poisson distribution, for counting events in an interval.
4. Continuous distributions and density curves (PDFs).
5. The normal approximation to the binomial.
6. Sampling distributions and the Central Limit Theorem (CLT).

---

## Part A: Expected Value and Standard Deviation

The **expected value** of a discrete random variable is its long-run average outcome:

E(X) = Σ x · P(x)
σ² = E(X²) − [E(X)]², where E(X²) = Σ x² · P(x)

Think of expected value as the value you would expect to get on average if you repeated the experiment many times.

### Worked Example: A Raffle

100 tickets are sold. First prize = $500; four second prizes of $50 each; each ticket costs $10. Let X = your profit or loss if you buy one ticket.

**(a) Probability distribution of X** (subtract the $10 cost from any prize):

| X | −10 | 40 | 490 |
| :---: | :---: | :---: |
| P(X) | 95/100 | 4/100 | 1/100 |

**(b) Expected value and standard deviation:**

| Quantity | x = −10 | x = 40 | x = 490 | Total |
| :--- | ---: | ---: | ---: | ---: |
| x · P(x) | −9.5 | 1.6 | 4.9 | −3.0 |
| x² · P(x) | 95 | 64 | 2401 | 2560 |

E(X) = −3.0
σ² = 2560 − (−3)² = 2560 − 9 = 2551, so σ = √2551 ≈ 50.51

**(c) Is buying a ticket a good idea? No.** E(X) is negative: on average you lose about $3 per ticket. That outcome favors the organizer, not the buyer.

---

## Part B: A Binomial Application on College Degrees

In a large city, 30% of adults have a college degree. For a random sample of n = 150 adults, let X = the number who have a degree.

**(a) Is X binomial?** Check BINS:
- Binary: has a degree (success) or not (failure).
- Independent: the population is large, so responses are approximately independent.
- Number: fixed n = 150.
- Success: constant p = 0.30.

Yes, X ~ Binomial(150, 0.30).

**(b) Mean and standard deviation:**
μ = np = 150(0.30) = 45
σ = √(np(1 − p)) = √(150 × 0.30 × 0.70) = √31.5 ≈ 5.61

**(c) Exactly 50 have a degree:** P(X = 50) = binompdf(150, 0.30, 50) ≈ 0.0467

**(d) More than 30 have a degree:** P(X > 30) = 1 − binomcdf(150, 0.30, 30) ≈ 1 − 0.0038 = 0.9962

**(e) Fewer than 35 have a degree:** P(X < 35) = P(X ≤ 34) = binomcdf(150, 0.30, 34) ≈ 0.0283

---

## Part C: The Poisson Distribution

Use the **Poisson** distribution to count events in a fixed interval of time or space when they occur at an average rate and independently. The rate is written μ or λ; either way it is also the mean.

P(X = k) = (e⁻ᵅᵘ × λᵏ) / k!, where mean = variance = λ (or μ), and SD = √λ

Calculator: poissonpdf(λ,k) for a point value, poissoncdf(λ,k) for a cumulative value.

### Worked Example: Coffee Shop Customers

A coffee shop averages 7 customers per hour. Let X = number of customers in the next hour, Poisson with λ = 7.

**(a) Exactly 10 customers:** P(X = 10) = poissonpdf(7, 10) ≈ 0.0710

**(b) 8 or fewer customers:** P(X ≤ 8) = poissoncdf(7, 8) ≈ 0.7291

**(c)** If X counts customers in the next 10 hours, the rate scales to λ = 7 × 10 = 70, so E(X) = 70.

---

## Part D: Continuous Probability Distributions

A **continuous** random variable can take any value in an interval. Because there are uncountably many possible values:
P(X = a) = 0 for any specific value a.

So we compute the probability of falling within an interval using a **probability density function (PDF)** f(x). Here probability equals area:
P(a ≤ X ≤ b) = ∫ₐᵇ f(x) dx = area under f(x) from a to b

**Properties of a PDF:**
1. f(x) ≥ 0 for all x (never negative).
2. Total area under f(x) equals 1: ∫₋∞ᵘᵉ f(x) dx = 1.

On a histogram, height equals count or frequency. On a density curve, height is scaled so that area, not height, equals probability.

---

## Part E: The Normal Distribution (recap)

A **normal** random variable X has a symmetric, unimodal, bell-shaped PDF centered at mean μ with SD σ:
X ~ N(μ, σ)

The **standard normal** Z ~ N(0,1) has mean 0 and SD 1. Convert with the z-score (from Day 3):
z = (x − μ) / σ

---

## Part F: Normal Approximation to the Binomial

When n is large, a binomial distribution is roughly bell-shaped, so we approximate it with a normal distribution provided (course rule of thumb):
np ≥ 10 and n(1 − p) ≥ 10

using X ~ N(μ, σ), where μ = np and σ = √(np(1 − p)).

Because the binomial is discrete and the normal is continuous, apply a **continuity correction**:

| Binomial (discrete) | Normal (continuous) approximation |
| :--- | :--- |
| P(X = a) | P(a − 0.5 < X < a + 0.5) |
| P(X ≤ a) | P(X < a + 0.5) |
| P(X < a) | P(X < a − 0.5) |
| P(X ≥ a) | P(X > a − 0.5) |
| P(X > a) | P(X > a + 0.5) |

### Worked Example (using the college-degree binomial)

X ~ Binomial(150, 0.30): μ = 45, σ = √31.5 ≈ 5.61, and np = 45 and n(1 − p) = 105 are both ≥ 10, so the approximation is valid.

Approximate P(X > 30):
1. Continuity correction: X > 30 becomes X > 30.5.
2. Standardize: z = (30.5 − 45) / √31.5 ≈ (−14.5) / 5.61 ≈ −2.58.
3. Normal probability: P(X > 30) ≈ P(Z > −2.58) ≈ 0.9951.

The exact binomial result was 0.9962, a very close match.

---

## Part G: Sampling Distributions and the Central Limit Theorem

**Sampling distribution:** the distribution of a statistic, such as a mean x̄ or proportion p̂, across all possible random samples of size n from a population.

**Central Limit Theorem (CLT):** as n grows, the sampling distribution of a statistic becomes approximately normal, whatever the population's shape, as long as the population has a finite standard deviation.

### CLT for the Sample Mean x̄

If X has mean μ and SD σ, then for an SRS of size n, the sample mean x̄ is approximately normal when X is normal or n is large (n ≥ 30):
x̄ ~ N(μ, σ/√n), where μ₍ₓ̄₎ = μ and σ₍ₓ̄₎ = σ/√n

Here σ₍ₓ̄₎ = σ/√n is the **standard error of the mean**: averages are less variable than individuals.

### Worked Example (course slide)

Technician maintenance time is strongly right-skewed with μ = 1 hour and σ = 1 hour. Your company services an SRS of n = 70 units and budgets 1.1 hours per unit. Is that enough?

By the CLT, x̄ is approximately N(1, 1/√70) = N(1, 0.12) since n = 70 ≥ 30.
P(x̄ < 1.1) = P(Z < (1.1 − 1) / 0.12) ≈ P(Z < 0.84) ≈ 0.80.

So there is about a 20% chance the average time exceeds the budget, even though the population is skewed, because the average is nearly normal.

### CLT for the Sample Proportion p̂

Let p̂ = x/n be the sample proportion, with population success rate p and q = 1 − p. If np ≥ 10 and nq ≥ 10:
p̂ ~ N(p, √(pq/n)), where μ₍p̂₎ = p and σ₍p̂₎ = √(p(1−p)/n)

Here σ₍p̂₎ = √(p(1−p)/n) is the **standard error of the proportion**.

---

## Key Formulas

| Quantity | Formula | Plain meaning |
| :--- | :--- | :--- |
| Expected value | Σ x · P(x) | Sum of each value times its probability |
| Variance (shortcut) | E(X²) − [E(X)]² | Mean of squared values minus mean squared |
| Binomial mean / SD | np / √(np(1−p)) | Trials times p; square root of npq |
| Poisson PMF / mean | (e⁻λ λᵏ) / k! / λ | e⁻λ times λᵏ over k!; mean equals variance equals λ |
| PDF probability | ∫ₐᵇ f(x) dx | Area under f(x) from a to b |
| z-score | (x − μ) / σ | Value minus mean, divided by SD |
| Normal approx. condition | np ≥ 10, n(1−p) ≥ 10 | Enough expected successes and failures |
| CLT mean (standard error) | μ, σ/√n | Mean stays μ; SD shrinks by √n |
| CLT proportion (SE) | p, √(p(1−p)/n) | Mean equals p; SD equals square root of pq over n |

---

## Practice Problems

**1.** Values X = −2, 0, 3, 10 with probabilities 0.5, 0.2, 0.2, 0.1. Find E(X) and σ (round to 2 dp).

<details><summary>Solution</summary>

E(X) = (−2)(0.5) + (0)(0.2) + (3)(0.2) + (10)(0.1) = −1 + 0 + 0.6 + 1.0 = 0.6.
E(X²) = 4(0.5) + 0 + 9(0.2) + 100(0.1) = 2 + 0 + 1.8 + 10 = 13.8.
σ² = 13.8 − 0.6² = 13.44; σ ≈ 3.67.

</details>

**2.** A part passes QC with probability 0.8. A batch has n = 20 parts. X = number that pass. Find μ, σ, and P(X = 15).

<details><summary>Solution</summary>

μ = np = 16. σ = √(20 × 0.8 × 0.2) = √3.2 ≈ 1.79. P(X = 15) = binompdf(20, 0.8, 15) ≈ 0.1746.

</details>

**3.** Calls to a help line average λ = 4 per day (Poisson). Find P(X = 6) and P(X ≤ 3).

<details><summary>Solution</summary>

P(X = 6) = poissonpdf(4, 6) ≈ 0.1042. P(X ≤ 3) = poissoncdf(4, 3) ≈ 0.4335.

</details>

**4.** A population has μ = 100 and σ = 15. For an SRS of n = 100, find P(x̄ > 103) (intermediate rounding ok).

<details><summary>Solution</summary>

n ≥ 30, so x̄ ~ N(100, 15/√100) = N(100, 1.5). z = (103 − 100) / 1.5 = 2.0. P(x̄ > 103) = P(Z > 2.0) ≈ 0.0228.

</details>

### Multiple Choice

**5.** Let X be a Poisson random variable with rate λ = 3. The mean of X is:

- a) 3
- b) 9
- c) √3
- d) 1/3

<details><summary>Solution</summary>

For a Poisson distribution, the mean equals the rate λ. Mean = λ = 3.

**Final answer: a) 3**

</details>

**6.** A population has standard deviation σ = 20. For an SRS of size n = 25, the standard error of the sample mean is:

- a) 20
- b) 4
- c) 0.8
- d) 25

<details><summary>Solution</summary>

The standard error of the mean is σ/√n. Standard error = 20/√25 = 20/5 = 4.

**Final answer: b) 4**

</details>
