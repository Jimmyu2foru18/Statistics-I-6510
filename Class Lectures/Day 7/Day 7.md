# Statistics I, Day 7: Expected Value, Poisson, Continuous Distributions & Sampling

## Overview
Day 7 gathers several bridging ideas between descriptive statistics and inference:
1. **Expected value** and **standard deviation** of a discrete distribution.
2. More **binomial** probability calculations.
3. The **Poisson** distribution (counting events in an interval).
4. **Continuous** distributions and **density curves** (PDFs).
5. The **normal approximation** to the binomial.
6. **Sampling distributions** and the **Central Limit Theorem (CLT)**.

*Source cross-checked against the course slides (Moore/McCabe/Craig, "Sampling Distributions").*

---

## Part A: Expected Value and Standard Deviation

The **expected value** of a discrete random variable is its *long-run average* outcome:

$$E(X) = \sum\, x \cdot P(x) \qquad\qquad \sigma^{2} = E(X^{2}) - [E(X)]^{2}, \quad E(X^{2}) = \sum\, x^{2}\,P(x)$$

### Worked Example: A Raffle

100 tickets are sold. First prize $= \$500$; four second prizes of $\$50$ each; each ticket costs $\$10$. Let $X$ = your **profit or loss** if you buy one ticket.

**(a) Probability distribution of $X$** (subtract the \$10 cost from any prize):

| $X$ | $-10$ | $40$ | $490$ |
| :---: | :---: | :---: | :---: |
| $P(X)$ | $\frac{95}{100}$ | $\frac{4}{100}$ | $\frac{1}{100}$ |

**(b) Expected value and standard deviation:**

| Quantity | $x=-10$ | $x=40$ | $x=490$ | **Total** |
| :--- | ---: | ---: | ---: | ---: |
| $x\,P(x)$ | $-9.5$ | $1.6$ | $4.9$ | **$-3.0$** |
| $x^{2}\,P(x)$ | $95$ | $64$ | $2401$ | **$2560$** |

$$E(X) = -3.0$$
$$\sigma^{2} = 2560 - (-3)^{2} = 2560 - 9 = 2551, \qquad \sigma = \sqrt{2551} \approx 50.51$$

**(c) Is buying a ticket a good idea? No.** $E(X)$ is **negative**: on average you lose about $\$3$ per ticket. That outcome favors the organizer, not the buyer.

---

## Part B: A Binomial Application on College Degrees

In a large city, **30%** of adults have a college degree. For a random sample of $n = 150$ adults, let $X$ = the number who have a degree.

**(a) Is $X$ binomial?** Check **BINS**:
- **B**inary: has a degree (success) or not (failure).
- **I**ndependent: the population is large, so responses are ~independent.
- **N**umber: fixed $n = 150$.
- **S**uccess: constant $p = 0.30$.

**Yes, $X \sim \text{Binomial}(150,\, 0.30)$.**

**(b) Mean and standard deviation:**
$$\mu = np = 150(0.30) = 45, \qquad \sigma = \sqrt{np(1-p)} = \sqrt{150(0.30)(0.70)} = \sqrt{31.5} \approx 5.61$$

**(c) Exactly 50 have a degree:** $P(X = 50) = \texttt{binompdf}(150, 0.30, 50) \approx 0.0467$

**(d) More than 30 have a degree:** $P(X > 30) = 1 - \texttt{binomcdf}(150, 0.30, 30) \approx 1 - 0.0038 = 0.9962$

**(e) Fewer than 35 have a degree:** $P(X < 35) = P(X \le 34) = \texttt{binomcdf}(150, 0.30, 34) \approx 0.0283$

---

## Part C: The Poisson Distribution

Use the **Poisson** distribution to count the events in a fixed interval of time or space when they occur at an average rate and independently. (The rate is written $\mu$ or $\lambda$; either way it is also the **mean**.)

$$P(X = k) = \frac{e^{-\lambda}\,\lambda^{k}}{k!}, \qquad \text{mean} = \text{variance} = \lambda \;(\mu), \qquad SD = \sqrt{\lambda}$$

- Calculator: `poissonpdf(λ,k)` for a point value, `poissoncdf(λ,k)` for a cumulative value.

### Worked Example: Coffee Shop Customers

A coffee shop averages **7 customers per hour**. Let $X$ = number of customers in the next hour, Poisson with $\lambda = 7$.

**(a) Exactly 10 customers:** $P(X = 10) = \texttt{poissonpdf}(7, 10) \approx 0.0710$

**(b) 8 or fewer customers:** $P(X \le 8) = \texttt{poissoncdf}(7, 8) \approx 0.7291$

**(c)** If $X$ counts customers in the **next 10 hours**, the rate scales to $\lambda = 7 \times 10 = 70$, so $E(X) = 70$.

---

## Part D: Continuous Probability Distributions

A **continuous** random variable can take *any* value in an interval. Because there are uncountably many possible values:
$$P(X = a) = 0 \quad \text{for any specific value } a.$$

So we compute the probability of falling **within an interval** using a **probability density function (PDF)** $f(x)$. Here probability equals **area**:
$$P(a \le X \le b) = \int_{a}^{b} f(x)\,dx = \text{area under } f(x) \text{ from } a \text{ to } b$$

**Properties of a PDF:**
1. $f(x) \ge 0$ for all $x$ (never negative).
2. Total area under $f(x)$ equals $1$: $\int_{-\infty}^{\infty} f(x)\,dx = 1$.

*(On a **histogram**, height = count/frequency. On a **density curve**, height is scaled so that **area**, not height, equals probability.)*

---

## Part E: The Normal Distribution (recap)

A **normal** random variable $X$ has a symmetric, unimodal, bell-shaped PDF centered at mean $\mu$ with SD $\sigma$:
$$X \sim N(\mu, \sigma)$$

The **standard normal** $Z \sim N(0,1)$ has mean 0 and SD 1; convert with the $z$-score (Day 3):
$$z = \frac{x - \mu}{\sigma}$$

---

## Part F: Normal Approximation to the Binomial

When $n$ is large, a binomial distribution is roughly bell-shaped, so we approximate it with a normal distribution **provided** (course rule of thumb):
$$np \ge 10 \quad \text{and} \quad n(1-p) \ge 10,$$

using
$$X \approx N\big(\mu, \sigma\big), \qquad \mu = np, \quad \sigma = \sqrt{np(1-p)}.$$

Because the binomial is **discrete** and the normal **continuous**, apply a **continuity correction**:

| Binomial (discrete) | Normal (continuous) approximation |
| :--- | :--- |
| $P(X = a)$ | $P(a - 0.5 < X < a + 0.5)$ |
| $P(X \le a)$ | $P(X < a + 0.5)$ |
| $P(X < a)$ | $P(X < a - 0.5)$ |
| $P(X \ge a)$ | $P(X > a - 0.5)$ |
| $P(X > a)$ | $P(X > a + 0.5)$ |

### Worked Example (using the college-degree binomial)

$X \sim \text{Binomial}(150, 0.30)$: $\mu = 45$, $\sigma = \sqrt{31.5} \approx 5.61$, and $np = 45$, $n(1-p) = 105$ are both $\ge 10$, so the approximation is valid.

Approximate $P(X > 30)$:
1. **Continuity correction:** $X > 30 \rightarrow X > 30.5$.
2. **Standardize:** $\displaystyle z = \frac{30.5 - 45}{\sqrt{31.5}} \approx \frac{-14.5}{5.61} \approx -2.58$.
3. **Normal probability:** $P(X > 30) \approx P(Z > -2.58) \approx 0.9951$.

*(Exact binomial result was $0.9962$, a very close match.)*

---

## Part G: Sampling Distributions and the Central Limit Theorem

**Sampling distribution:** the distribution of a *statistic* (e.g., a mean $\bar{x}$ or proportion $\hat{p}$) across **all possible** random samples of size $n$ from a population.

**Central Limit Theorem (CLT):** as $n$ grows, the sampling distribution of a statistic becomes approximately **normal**, whatever the population's shape (finite SD).

### CLT for the Sample Mean $\bar{X}$

If $X$ has mean $\mu$ and SD $\sigma$, then for an SRS of size $n$, the sample mean $\bar{X}$ is approximately normal when $X$ is normal **or** $n$ is large ($n \ge 30$):
$$\bar{X} \approx N\left(\mu,\ \frac{\sigma}{\sqrt{n}}\right), \qquad \mu_{\bar{X}} = \mu, \qquad \sigma_{\bar{X}} = \frac{\sigma}{\sqrt{n}}$$

Here $\sigma_{\bar{X}} = \sigma/\sqrt{n}$ is the **standard error of the mean**: averages are less variable than individuals.

### Worked Example (course slide)

Technician maintenance time is **strongly right-skewed** with $\mu = 1$ hour and $\sigma = 1$ hour. Your company services an SRS of $n = 70$ units and budgets $1.1$ hours per unit. Is that enough?

- By the CLT, $\bar{X}$ is approximately $N\!\left(1,\ \frac{1}{\sqrt{70}}\right) = N(1,\, 0.12)$ since $n = 70 \ge 30$.
- $P(\bar{X} < 1.1) = P\!\left(Z < \frac{1.1 - 1}{0.12}\right) \approx P(Z < 0.84) \approx 0.80$.
- So there's about a **20% chance the average time exceeds the budget**, even though the population is skewed, because the *average* is nearly normal.

> *(The class notes reference the same idea with "50 realizations". The method is identical: $\bar{X} \approx N(\mu, \sigma/\sqrt{n})$; just swap $n = 50$.)*

### CLT for the Sample Proportion $\hat{p}$

Let $\hat{p} = x/n$ be the sample proportion, with population success rate $p$ and $q = 1-p$. If $np \ge 10$ and $nq \ge 10$:
$$\hat{p} \approx N\left(p,\ \sqrt{\frac{p\,q}{n}}\right), \qquad \mu_{\hat{p}} = p, \qquad \sigma_{\hat{p}} = \sqrt{\frac{p(1-p)}{n}}$$

Here $\sigma_{\hat{p}} = \sqrt{p(1-p)/n}$ is the **standard error of the proportion**.

---

## Key Formulas

| Quantity | LaTeX | Plain / in words |
| :--- | :--- | :--- |
| Expected value | $\sum x\,P(x)$ | sum of (each value × its probability) |
| Variance (shortcut) | $E(X^{2}) - [E(X)]^{2}$ | mean of squared values minus mean squared |
| Binomial mean / SD | $np \; / \; \sqrt{np(1-p)}$ | trials×p ; √(npq) |
| Poisson PMF / mean | $\dfrac{e^{-\lambda}\lambda^{k}}{k!} \; / \; \lambda$ | e^(−λ)·λᵏ / k! ; mean = variance = λ |
| PDF probability | $\int_{a}^{b} f(x)\,dx$ | area under $f(x)$ from $a$ to $b$ |
| $z$-score | $\dfrac{x-\mu}{\sigma}$ | (value − mean) ÷ SD |
| Normal approx. condition | $np \ge 10,\; n(1-p) \ge 10$ | enough expected successes & failures |
| CLT mean (standard error) | $\mu, \; \sigma/\sqrt{n}$ | mean stays μ; SD shrinks by √n |
| CLT proportion (SE) | $p, \; \sqrt{p(1-p)/n}$ | mean = p; SD = √(pq/n) |

---

## Practice Problems

**1.** Values $X = -2, 0, 3, 10$ with probabilities $0.5, 0.2, 0.2, 0.1$. Find $E(X)$ and $\sigma$ (round to 2 dp).

<details><summary>Solution</summary>

$E(X) = (-2)(0.5) + (0)(0.2) + (3)(0.2) + (10)(0.1) = -1 + 0 + 0.6 + 1.0 = 0.6$. $E(X^2) = 4(0.5) + 0 + 9(0.2) + 100(0.1) = 2 + 0 + 1.8 + 10 = 13.8$. $\sigma^2 = 13.8 - 0.6^2 = 13.44$; $\sigma \approx 3.67$.

</details>

**2.** A part passes QC with probability $0.8$; a batch has $n = 20$ parts, $X$ = number that pass. Find $\mu$, $\sigma$, and $P(X = 15)$.

<details><summary>Solution</summary>

$\mu = np = 16$; $\sigma = \sqrt{20(0.8)(0.2)} = \sqrt{3.2} \approx 1.79$; $P(X=15) = \texttt{binompdf}(20,0.8,15) \approx 0.1746$.

</details>

**3.** Calls to a help line average $\lambda = 4$ per day (Poisson). Find $P(X = 6)$ and $P(X \le 3)$.

<details><summary>Solution</summary>

$P(X=6) = \texttt{poissonpdf}(4,6) \approx 0.1042$; $P(X\le3) = \texttt{poissoncdf}(4,3) \approx 0.4335$.

</details>

**4.** A population has $\mu = 100$ and $\sigma = 15$. For an SRS of $n = 100$, find $P(\bar{X} > 103)$ (intermediate rounding ok).

<details><summary>Solution</summary>

$n \ge 30$, so $\bar{X} \approx N(100, 15/\sqrt{100}) = N(100, 1.5)$. $z = (103 - 100)/1.5 = 2.0$. $P(\bar{X} > 103) = P(Z > 2.0) \approx 0.0228$.

</details>

### Multiple Choice

**5.** Let $X$ be a Poisson random variable with rate $\lambda = 3$. The mean of $X$ is:

- **a)** 3
- **b)** 9
- **c)** $\sqrt{3}$
- **d)** $1/3$

<details><summary>Solution</summary>

- For a Poisson distribution, the mean equals the rate $\lambda$.
- Mean $= \lambda = 3$.

**Final answer: (a) 3**

</details>

**6.** A population has standard deviation $\sigma = 20$. For a SRS of size $n = 25$, the standard error of the sample mean is:

- **a)** 20
- **b)** 4
- **c)** 0.8
- **d)** 25

<details><summary>Solution</summary>

- The standard error of the mean is $\sigma/\sqrt{n}$.
- Standard error $= 20/\sqrt{25} = 20/5 = 4$.

**Final answer: (b) 4**

</details>
