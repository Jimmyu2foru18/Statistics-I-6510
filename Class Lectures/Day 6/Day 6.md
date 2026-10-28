# Statistics I, Day 6: Linear Combinations of Random Variables and the Binomial Distribution

Welcome to Day 6! So far we have summarized data. Now we start working with random variables and their distributions. Today covers two topics:

1. How the mean and variance behave when we add, subtract, or scale random variables, called the Rules for Means and Variances.
2. The binomial distribution, which models counting successes in a fixed number of yes-or-no trials.

---

## Part A: Rules for Linear Combinations of Random Variables

Let X and Y be random variables with means μₓ = E(X), μᵧ = E(Y) and variances σₓ² = Var(X), σᵧ² = Var(Y).

### Rules for Means

- Rule 1 (scale and shift): If a and b are fixed numbers, E(a + bX) = a + bμₓ
- Rule 2 (sum): E(X + Y) = μₓ + μᵧ
- Rule 3 (difference): E(X − Y) = μₓ − μᵧ

### Rules for Variances and Standard Deviations

- Rule 1 (scale and shift): Var(a + bX) = b²σₓ². A shift a does nothing; a scale b multiplies the variance by b².
- Rule 2 (independent X and Y): Var(X ± Y) = σₓ² + σᵧ²
- Rule 3 (with correlation ρ): Var(X ± Y) = σₓ² + σᵧ² ± 2ρσₓσᵧ

**Crucial takeaway 1:** For a difference X − Y, the means subtract but the variances still add (σₓ² + σᵧ²). Uncertainty grows when you combine random variables; it does not cancel.

**Crucial takeaway 2:** To get the standard deviation of a combination, take the square root of the summed variances:
sd(X ± Y) = √(σₓ² + σᵧ²), which is NOT equal to σₓ ± σᵧ. Standard deviations do not simply add or subtract.

Rule 3 generalizes Rule 2: when X and Y are independent, ρ = 0, so the cross-term 2ρσₓσᵧ vanishes and we recover σₓ² + σᵧ².

### Worked Example

Let X have mean μₓ = 10 and SD σₓ = 3. Let Y have mean μᵧ = 6 and SD σᵧ = 2. Suppose X and Y are independent. Find the mean and SD of (a) X + Y and (b) X − Y.

**(a) X + Y:**
Mean = 10 + 6 = 16. Variance = 3² + 2² = 9 + 4 = 13. SD = √13 ≈ 3.61.

**(b) X − Y:**
Mean = 10 − 6 = 4. Variance = 3² + 2² = 13. SD = √13 ≈ 3.61.

Notice the means differ (16 vs. 4) but the spread is identical because variances always add.

---

## Part B: The Binomial Distribution

A random variable X counts the number of successes in a fixed number of trials. It is binomial when all four conditions, remembered as BINS, hold:

| Letter | Condition | In plain terms |
| :---: | :--- | :--- |
| B | Binary | Each trial has exactly two outcomes: success (probability p) or failure (probability 1 − p). |
| I | Independent | Trials are independent; one result does not affect another. |
| N | Number | The number of trials n is fixed in advance. |
| S | Success | The probability of success p is the same on every trial. |

Notation: X ~ Binomial(n, p), taking whole-number values 0, 1, …, n.

### Formulas

**Probability of exactly k successes:**
P(X = k) = C(n,k) × pᵏ × (1 − p)ⁿ⁻ᵏ, where C(n,k) = n! / (k!(n − k)!)

C(n,k) counts the different arrangements of k successes among n trials, and 0! = 1.

**Mean (expected successes):** μ = np
**Variance:** σ² = np(1 − p)
**Standard deviation:** σ = √(np(1 − p))

**Note:** The mean and SD formulas μ = np and σ = √(np(1 − p)) work only for binomial variables. Do not apply them to other distributions.

On a graphing calculator: binompdf(n,p,k) = P(X = k), and binomcdf(n,p,k) = P(X ≤ k).

### Worked Example: Defective Lightbulbs

A machine produces lightbulbs. Each bulb has a 3% chance of being defective. Let X = number of defective bulbs in a batch of n = 200.

**Check BINS:**
- Binary: defective (success) or not (failure).
- Independent: one bulb's outcome does not affect another's.
- Number: fixed n = 200.
- Success: constant p = 0.03.

So X ~ Binomial(200, 0.03).

**(a) Mean and standard deviation:**
μ = np = 200(0.03) = 6
σ = √(np(1 − p)) = √(200 × 0.03 × 0.97) = √5.82 ≈ 2.41

**(b) Exactly 5 defective:**
P(X = 5) = C(200,5)(0.03)⁵(0.97)¹⁹⁵ = binompdf(200, 0.03, 5) ≈ 0.1623

**(c) 3 or fewer defective:**
P(X ≤ 3) = binomcdf(200, 0.03, 3) ≈ 0.1472

---

## Key Formulas

| Quantity | Formula | Plain meaning |
| :--- | :--- | :--- |
| Mean of a + bX | μ₍ₐ₊bX₎ = a + bμₓ | Start with μₓ, multiply by b, add a |
| Mean of X ± Y | μ₍X±Y₎ = μₓ ± μᵧ | Add or subtract the two means |
| Var of a + bX | σ²₍ₐ₊bX₎ = b²σₓ² | Multiply variance by b²; shift a is ignored |
| Var of X ± Y (indep.) | σ²₍X±Y₎ = σₓ² + σᵧ² | Add the two variances, even for a difference |
| SD of a combination | √(σₓ² + σᵧ²) | Square root of the summed variances |
| Binomial PMF | C(n,k)pᵏ(1−p)ⁿ⁻ᵏ | (n choose k) × pᵏ × (1−p)ⁿ⁻ᵏ |
| Binomial mean | np | Trials times success probability |
| Binomial SD | √(np(1−p)) | Square root of npq, where q = 1 − p |

---

## Practice Problems

**1.** Let A have mean 50 and SD 8. Let B have mean 30 and SD 5. Assume A and B are independent. Find the mean and SD of A − B.

<details><summary>Solution</summary>

Mean = 50 − 30 = 20. Variance = 8² + 5² = 64 + 25 = 89. SD = √89 ≈ 9.43.

</details>

**2.** A fair coin is flipped n = 40 times. Let X = number of heads. Find μ and σ.

<details><summary>Solution</summary>

p = 0.5. μ = np = 40(0.5) = 20. σ = √(np(1 − p)) = √(40 × 0.5 × 0.5) = √10 ≈ 3.16.

</details>

**3.** Using the fair-coin setup above, find P(X ≤ 15).

<details><summary>Solution</summary>

binomcdf(40, 0.5, 15) ≈ 0.0769, about 7.7%.

</details>

**4.** Why can't we compute the mean of X as np if X counts something that is not binomial, such as a Poisson count?

<details><summary>Solution</summary>

μ = np and σ = √(np(1 − p)) are valid only for binomial variables. Other distributions have their own mean formulas, for example the Poisson mean equals λ.

</details>

### Multiple Choice

**5.** X and Y are independent with Var(X) = 4 and Var(Y) = 9. What is Var(X + Y)?

- a) 5
- b) 13
- c) 6
- d) 36

<details><summary>Solution</summary>

For independent variables, variances add for any linear combination. Var(X + Y) = 4 + 9 = 13.

**Final answer: b) 13**

</details>

**6.** Let X be binomial with n = 10 trials and success probability p = 0.5. The mean of X is:

- a) 5
- b) 2.5
- c) 0.5
- d) 10

<details><summary>Solution</summary>

The binomial mean equals np. Mean = 10 × 0.5 = 5.

**Final answer: a) 5**

</details>
