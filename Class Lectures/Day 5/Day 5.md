# Statistics I, Day 5: Conditional Probability, the Multiplication Rule, and Independence

## Overview
Day 4 handled **"OR"** (the addition rule). Today we handle **"AND"**: the probability that *two* events both happen, using the **multiplication rule**. The key new idea is **conditional probability** $P(B \mid A)$, the "given" notation, and the special case of **independent** events.

---

## Part A: Reviewing "OR"

### 1. Pick an integer from 1 to 10 at random

Sample space: $S = \{1, 2, 3, 4, 5, 6, 7, 8, 9, 10\}$ ($n=10$).

| Event | Favorable outcomes | Probability |
| :--- | :--- | :---: |
| Even | $\{2,4,6,8,10\}$ | $\frac{5}{10} = \frac{1}{2}$ |
| Exactly 5 | $\{5\}$ | $\frac{1}{10}$ |
| Multiple of 3 | $\{3,6,9\}$ | $\frac{3}{10}$ |
| Prime | $\{2,3,5,7\}$ | $\frac{4}{10} = \frac{2}{5}$ |
| Less than 7 | $\{1,2,3,4,5,6\}$ | $\frac{6}{10} = \frac{3}{5}$ |
| Even **or** 5 | $\{2,4,5,6,8,10\}$ | $\frac{6}{10} = \frac{3}{5}$ |
| Multiple of 3 **or** $<7$ | $\{1,2,3,4,5,6,9\}$ | $\frac{7}{10}$ |
| Prime **or** even | $\{2,3,4,5,6,7,8,10\}$ | $\frac{8}{10} = \frac{4}{5}$ |

### 2. Roll two standard 6-sided dice

The proper probability sample space is the **36 ordered pairs** $(\text{die}_1, \text{die}_2)$. The *sum* ranges from $2$ to $12$.

| Event | Count (out of 36) | Probability |
| :--- | :---: | :---: |
| Sum $< 6$ (sums $2,3,4,5$) | $10$ | $\frac{10}{36} = \frac{5}{18}$ |
| At least one odd | $27$ (all but the $9$ even–even pairs) | $\frac{27}{36} = \frac{3}{4}$ |
| Two of the same number (doubles) | $6$ | $\frac{6}{36} = \frac{1}{6}$ |
| Sum $<6$ **or** at least one odd | $28$ | $\frac{28}{36} = \frac{7}{9}$ |
| At least one odd **or** two of the same | $30$ | $\frac{30}{36} = \frac{5}{6}$ |

> Notice we can get "at least one odd" via the **complement**: $1 - P(\text{both even}) = 1 - \frac{9}{36} = \frac{27}{36}$. "At least one" almost always invites the complement trick.

---

## Part B: The Multiplication Rule for "AND"

### Conditional Probability

**Conditional probability** $P(B \mid A)$ is read *"the probability of $B$ **given** that $A$ has occurred."* It re-computes the odds of $B$ using the *reduced* sample space where $A$ is known to be true.

### The General Multiplication Rule

For two events $A$ and $B$:
$$\boxed{\;P(A \text{ and } B) = P(A)\cdot P(B \mid A)\;}$$

(Equivalently, $P(A \text{ and } B) = P(B)\cdot P(A \mid B)$; choose whichever "given" fits the situation.)

---

## Part C: Independence

Two events $A$ and $B$ are **independent** if knowing one occurred does **not** change the probability of the other:
$$P(A \mid B) = P(A) \quad \text{and} \quad P(B \mid A) = P(B)$$

If $A$ and $B$ are independent, the multiplication rule simplifies:
$$P(A \text{ and } B) = P(A)\cdot P(B)$$

> **Independent vs. mutually exclusive**: don't confuse them! *Independent* means one event doesn't affect the other's probability (they *can* both happen). *Mutually exclusive* means they *cannot* both happen.

---

## Part D: With and Without Replacement

A bag contains **4 blue** and **6 green** marbles (10 total). We draw two marbles.

### With replacement (each pick is independent)

You draw one marble, **put it back**, then draw again. The probabilities reset every time, so the two events are **independent** and we multiply the two individual probabilities.

- $P(\text{1st blue and 2nd green}) = \frac{4}{10}\cdot\frac{6}{10} = \frac{24}{100}$
- $P(\text{1st green and 2nd green}) = \frac{6}{10}\cdot\frac{6}{10} = \frac{36}{100}$

### Without replacement (picks are dependent)

You draw one marble and **keep it out**, then draw again. The totals change, so the second draw is **dependent** on the first and we use a *conditional* probability.

- $P(\text{1st blue and 2nd green}) = \frac{4}{10}\cdot\frac{6}{9} = \frac{24}{90}$
  (After removing a blue marble, 6 green remain out of 9 total.)
- $P(\text{1st green and 2nd green}) = \frac{6}{10}\cdot\frac{5}{9} = \frac{30}{90}$
  (After removing a green marble, only 5 green remain out of 9.)

> **Rule of thumb:** *With* replacement → independent. *Without* replacement → dependent.

---

## Part E: When We Treat Dependent Draws as Independent

If the population is **huge** compared with the small number we draw, the probabilities barely change, so we **approximate the draws as independent** for simplicity, even though we sample without replacement.

**Example.** At a university with tens of thousands of students, 15% are graduate students. Choose 3 students at random. What is the probability **all three** are graduate students?

Because the population is so large, treat each pick as independent:
$$P(\text{all 3 grad}) \approx (0.15)(0.15)(0.15) = 0.15^3 = 0.003375$$

---

## Key Formulas

| Rule | Formula | Plain / in words |
| :--- | :--- | :--- |
| Conditional probability | $P(B\mid A)=\dfrac{P(A\text{ and }B)}{P(A)}$ | probability of B within the "A happened" world |
| General multiplication | $P(A\text{ and }B)=P(A)\,P(B\mid A)$ | P(A) × "probability of B given A" |
| Independence (test) | $P(B\mid A)=P(B)$ | B's probability unchanged by knowing A |
| Independence (multiply) | $P(A\text{ and }B)=P(A)P(B)$ | valid only when independent |

---

## Practice Problems

**1.** Draw two cards from a shuffled deck. Find $P(\text{heart then spade})$ (a) with replacement and (b) without replacement.

<details><summary>Solution</summary>

(a) Independent (reset): $\frac{13}{52}\cdot\frac{13}{52}=\frac14\cdot\frac14=\frac{1}{16}=0.0625$.
(b) Dependent: $\frac{13}{52}\cdot\frac{13}{51}=\frac{169}{2652}\approx 0.0637$.

</details>

**2.** A bag has 5 red and 3 blue marbles. Draw two **without** replacement. Find $P(\text{both red})$, then compare with replacement.

<details><summary>Solution</summary>

Without: $\frac{5}{8}\cdot\frac{4}{7}=\frac{20}{56}=\frac{5}{14}\approx0.357$. With replacement (independent): $(\frac58)^2=\frac{25}{64}\approx0.391$, slightly higher because the first red is "put back," keeping the second draw's odds at $5/8$.

</details>

**3.** Events $A$ and $B$ have $P(A)=0.3$ and $P(A\mid B)=0.3$. Are they independent? Justify.

<details><summary>Solution</summary>

Yes. $P(A\mid B)=P(A)$ means knowing $B$ doesn't change the chance of $A$, the definition of independence.

</details>

**4.** In a shipment, 2% of items are defective. A quality inspector samples 3 items **with** replacement. Find $P(\text{all 3 defective})$.

<details><summary>Solution</summary>

Independent picks: $0.02\cdot0.02\cdot0.02=0.02^3=0.000008$.

</details>

**5.** Why might we treat draws made **without** replacement as independent?

<details><summary>Solution</summary>

When the population is very large compared with the small sample, removing one item barely changes the probabilities, so the independence assumption is a good approximation (and makes the math simple).

</details>

### Multiple Choice

**6.** Events $A$ and $B$ are independent, with $P(A) = 0.5$ and $P(B) = 0.4$. What is $P(A \text{ and } B)$?

- **a)** 0.10
- **b)** 0.20
- **c)** 0.45
- **d)** 0.90

<details><summary>Solution</summary>

- For independent events, $P(A \text{ and } B) = P(A) \times P(B)$.
- $P(A \text{ and } B) = 0.5 \times 0.4 = 0.20$.

**Final answer: (b) 0.20**

</details>

**7.** When two marbles are drawn in a row without replacement, the two draws are:

- **a)** Independent
- **b)** Dependent
- **c)** Both independent and dependent
- **d)** Probability does not apply

<details><summary>Solution</summary>

- Without replacement, removing the first marble changes the totals for the second draw.
- When the probabilities change between draws, the events are dependent.

**Final answer: (b) Dependent**

</details>
