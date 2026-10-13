# Statistics I, Day 4: Probability (Chapter 4)

## Overview
We now move from *describing* data (Days 1–3) to modeling *chance*. Probability gives us a number from 0 to 1 for how likely an event is, and it is the foundation for all the statistical inference that follows.

**Probability** is a numerical measure of how likely something is to occur, written $P(\text{event})$ and always between 0 and 1.

---

## 1. Core Framework and Definitions

We build every probability problem on four building blocks:

- **Random experiment / process**: any process whose result is determined by **chance**.
- **Outcome**: any single possible result of the experiment.
- **Sample space ($S$)**: the set of **all possible outcomes**.
- **Event**: any **set of one or more outcomes** (a subset of $S$).

### Example 1: Rolling a 6-sided die
- Sample space: $S = \{1, 2, 3, 4, 5, 6\}$
- Event $A = \{\text{odd numbers}\} = \{1, 3, 5\}$
- Event $B = \{\text{rolling a number} < 5\} = \{1, 2, 3, 4\}$

### Example 2: Flipping a coin 3 times
- Sample space: $S = \{\text{HHH}, \text{HHT}, \text{HTH}, \text{HTT}, \text{THH}, \text{THT}, \text{TTH}, \text{TTT}\}$ (8 outcomes)
- Event $A = \{\text{at least one head}\}$: every outcome except $\text{TTT}$ (7 outcomes)
- Event $B = \{\text{2 of the same in a row}\} = \{\text{HHH}, \text{HHT}, \text{HTT}, \text{TTH}, \text{TTT}\}$ (5 outcomes)

---

## 2. Senses of Probability

There are three common ways to assign a probability:

| Sense | Definition | Formula |
| :--- | :--- | :--- |
| **Classical (theoretical)** | All outcomes equally likely; count favorable over total. | $P(A) = \dfrac{n(A)}{n(S)}$ |
| **Empirical (experimental)** | Based on observed data / repeated trials. | $P(A) = \dfrac{\text{times } A \text{ occurs}}{\text{number of trials}}$ |
| **Subjective** | An educated guess from expert opinion / experience (no counting or trials). |  |

**Law of Large Numbers:** as the number of trials grows toward infinity, the *empirical* probability converges to the *classical* probability. In practice: the more you repeat an experiment, the closer the observed relative frequency gets to the true probability.

---

## 3. Rules for Probability

### A. Bounds
For any event $A$:
$$0 \le P(A) \le 1$$
- $P(A) = 0$ → impossible; $P(A) = 1$ → certain. The closer $P(A)$ is to 1, the more likely $A$ is to occur.

### B. Complement Rule
The complement $A^c$ (or $A'$) is "event $A$ does **not** happen":
$$P(A) + P(A^c) = 1 \quad\Longrightarrow\quad P(A^c) = 1 - P(A)$$

### C. Law of Total Probability
If events $A_1, A_2, \dots, A_n$ are **disjoint** (mutually exclusive) and together cover all of $S$, their probabilities sum to 1:
$$P(A_1) + P(A_2) + \dots + P(A_n) = 1$$

### D. Addition Rule for "OR"

**General case** (events may overlap):
$$P(A \text{ or } B) = P(A) + P(B) - P(A \text{ and } B)$$

We subtract $P(A \text{ and } B)$ because the overlap would otherwise be **counted twice**.

**Special case, mutually exclusive (disjoint) events** (cannot happen together, so $P(A \text{ and } B) = 0$):
$$P(A \text{ or } B) = P(A) + P(B)$$

> **Memory aid:** "OR → add, but subtract the overlap you double-counted." "AND → multiply" (developed on **Day 5**).

---

## 4. Worked Problems

Roll a standard six-sided die, $S = \{1, 2, 3, 4, 5, 6\}$.

**Problem 1: Find $P(3 \text{ or Even})$.**
- Rolling a $3$ and rolling an even number cannot both happen → **mutually exclusive**.
$$P(3 \text{ or Even}) = P(3) + P(\text{Even}) = \frac{1}{6} + \frac{3}{6} = \frac{4}{6} = \frac{2}{3}$$

**Problem 2: Find $P(\text{odd or } > 2)$.**
- $A = \text{odd} = \{1, 3, 5\}$ and $B = {>}\,2 = \{3, 4, 5, 6\}$. These **overlap** on $\{3, 5\}$, so use the *general* rule.
$$P(\text{odd or } > 2) = P(\text{odd}) + P(> 2) - P(\text{odd and } > 2)$$
$$= \frac{3}{6} + \frac{4}{6} - \frac{2}{6} = \frac{5}{6} \approx 0.8333$$

---

## Key Formulas

| Rule | Formula | Plain / in words |
| :--- | :--- | :--- |
| Classical probability | $P(A)=\dfrac{n(A)}{n(S)}$ | favorable outcomes ÷ total outcomes |
| Empirical probability | $P(A)=\dfrac{\text{times }A}{\text{trials}}$ | observed frequency ÷ trials |
| Bounds | $0\le P(A)\le 1$ | always between 0 and 1 |
| Complement | $P(A^{c})=1-P(A)$ | 1 minus P(A) |
| Law of total probability | $\sum P(A_i)=1$ | disjoint events covering $S$ sum to 1 |
| Addition (general) | $P(A\text{ or }B)=P(A)+P(B)-P(A\text{ and }B)$ | add, then subtract the overlap |
| Addition (disjoint) | $P(A\text{ or }B)=P(A)+P(B)$ | mutually exclusive → just add |

---

## Practice Problems

**1.** Roll a die. Find $P(\text{even or prime})$.

<details><summary>Solution</summary>

Even $=\{2,4,6\}$, prime $=\{2,3,5\}$. Union $=\{2,3,4,5,6\}$ (5 outcomes); they overlap only at $2$. $P=3/6+3/6-1/6=5/6 \approx 0.833$.

</details>

**2.** Roll a die. Find $P(\text{not a }4)$ using the complement rule.

<details><summary>Solution</summary>

$P(4)=1/6$, so $P(\text{not }4)=1-1/6=5/6$.

</details>

**3.** Given $P(A)=0.4$, $P(B)=0.5$, and $P(A\text{ and }B)=0.15$, find $P(A\text{ or }B)$.

<details><summary>Solution</summary>

$P(A\text{ or }B)=0.4+0.5-0.15=0.75$.

</details>

**4.** Flip two fair coins. State the sample space and find $P(\text{exactly one head})$.

<details><summary>Solution</summary>

$S=\{\text{HH},\text{HT},\text{TH},\text{TT}\}$ (4 outcomes). Exactly one head $=\{\text{HT},\text{TH}\}$, so $P=2/4=1/2$.

</details>

**5.** Are "rolling an odd number" and "rolling an even number" mutually exclusive? What is $P(\text{odd or even})$?

<details><summary>Solution</summary>

Yes, they share no outcomes. So (disjoint rule) $P=3/6+3/6=1$, i.e., one of them is certain.

</details>

### Multiple Choice

**6.** Roll one fair six-sided die. What is $P(\text{even or } 6)$?

- **a)** $1/6$
- **b)** $1/3$
- **c)** $1/2$
- **d)** $2/3$

<details><summary>Solution</summary>

- The even numbers are $\{2, 4, 6\}$, so the outcome $6$ is already counted in "even".
- $P(\text{even}) = 3/6 = 1/2$, and adding $6$ changes nothing.

**Final answer: (c) $1/2$**

</details>

**7.** If $P(A) = 0.6$, what is the probability of the complement of $A$?

- **a)** 0.4
- **b)** 0.6
- **c)** 1.0
- **d)** 0.24

<details><summary>Solution</summary>

- The complement rule gives $P(A^c) = 1 - P(A)$.
- $P(A^c) = 1 - 0.6 = 0.4$.

**Final answer: (a) 0.4**

</details>
