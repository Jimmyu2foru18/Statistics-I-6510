# Statistics I, Day 4: Probability

Welcome to Day 4! We now move from describing data (Days 1 through 3) to modeling chance. Probability gives us a number from 0 to 1 for how likely an event is, and it is the foundation for all the statistical inference that follows.

**Probability** is a numerical measure of how likely something is to occur, written P(event) and always between 0 and 1.

---

## 1. Core Framework and Definitions

We build every probability problem on four building blocks:

- **Random experiment or process:** any process whose result is determined by chance.
- **Outcome:** any single possible result of the experiment.
- **Sample space (S):** the set of all possible outcomes.
- **Event:** any set of one or more outcomes, meaning a subset of S.

### Example 1: Rolling a 6-sided die
- Sample space: S = {1, 2, 3, 4, 5, 6}
- Event A = {odd numbers} = {1, 3, 5}
- Event B = {rolling a number less than 5} = {1, 2, 3, 4}

### Example 2: Flipping a coin 3 times
- Sample space: S = {HHH, HHT, HTH, HTT, THH, THT, TTH, TTT} (8 outcomes)
- Event A = {at least one head}: every outcome except TTT (7 outcomes)
- Event B = {2 of the same in a row} = {HHH, HHT, HTT, TTH, TTT} (5 outcomes)

---

## 2. Senses of Probability

There are three common ways to assign a probability:

| Sense | Definition | Formula |
| :--- | :--- | :--- |
| Classical (theoretical) | All outcomes equally likely; count favorable over total. | P(A) = n(A) / n(S) |
| Empirical (experimental) | Based on observed data or repeated trials. | P(A) = times A occurs / number of trials |
| Subjective | An educated guess from expert opinion or experience, with no counting or trials. | |

**Law of Large Numbers:** as the number of trials grows toward infinity, the empirical probability converges to the classical probability. In practice: the more you repeat an experiment, the closer the observed relative frequency gets to the true probability.

---

## 3. Rules for Probability

### A. Bounds
For any event A:
0 ≤ P(A) ≤ 1
- P(A) = 0 means impossible.
- P(A) = 1 means certain.
- The closer P(A) is to 1, the more likely A is to occur.

### B. Complement Rule
The complement Aᶜ (or A') is "event A does not happen":
P(A) + P(Aᶜ) = 1, which means P(Aᶜ) = 1 − P(A)

### C. Law of Total Probability
If events A₁, A₂, …, Aₙ are disjoint (mutually exclusive) and together cover all of S, their probabilities sum to 1:
P(A₁) + P(A₂) + … + P(Aₙ) = 1

### D. Addition Rule for "OR"

**General case** (events may overlap):
P(A or B) = P(A) + P(B) − P(A and B)

We subtract P(A and B) because the overlap would otherwise be counted twice.

**Special case, mutually exclusive or disjoint events** (cannot happen together, so P(A and B) = 0):
P(A or B) = P(A) + P(B)

**Memory aid:** "OR means add, but subtract the overlap you double-counted." "AND means multiply," which we develop on Day 5.

---

## 4. Worked Problems

Roll a standard six-sided die, S = {1, 2, 3, 4, 5, 6}.

**Problem 1: Find P(3 or Even).**
Rolling a 3 and rolling an even number cannot both happen, so they are mutually exclusive.
P(3 or Even) = P(3) + P(Even) = 1/6 + 3/6 = 4/6 = 2/3

**Problem 2: Find P(odd or > 2).**
A = odd = {1, 3, 5} and B = greater than 2 = {3, 4, 5, 6}. These overlap on {3, 5}, so use the general rule.
P(odd or > 2) = P(odd) + P(> 2) − P(odd and > 2)
= 3/6 + 4/6 − 2/6 = 5/6 ≈ 0.8333

---

## Key Formulas

| Rule | Formula | Plain meaning |
| :--- | :--- | :--- |
| Classical probability | P(A) = n(A) / n(S) | Favorable outcomes divided by total outcomes |
| Empirical probability | P(A) = times A / trials | Observed frequency divided by trials |
| Bounds | 0 ≤ P(A) ≤ 1 | Always between 0 and 1 |
| Complement | P(Aᶜ) = 1 − P(A) | One minus P(A) |
| Law of total probability | ΣP(Aᵢ) = 1 | Disjoint events covering S sum to 1 |
| Addition (general) | P(A or B) = P(A) + P(B) − P(A and B) | Add, then subtract the overlap |
| Addition (disjoint) | P(A or B) = P(A) + P(B) | Mutually exclusive, so just add |

---

## Practice Problems

**1.** Roll a die. Find P(even or prime).

<details><summary>Solution</summary>

Even = {2, 4, 6}, prime = {2, 3, 5}. Union = {2, 3, 4, 5, 6} (5 outcomes). They overlap only at 2. P = 3/6 + 3/6 − 1/6 = 5/6 ≈ 0.833.

</details>

**2.** Roll a die. Find P(not a 4) using the complement rule.

<details><summary>Solution</summary>

P(4) = 1/6, so P(not 4) = 1 − 1/6 = 5/6.

</details>

**3.** Given P(A) = 0.4, P(B) = 0.5, and P(A and B) = 0.15, find P(A or B).

<details><summary>Solution</summary>

P(A or B) = 0.4 + 0.5 − 0.15 = 0.75.

</details>

**4.** Flip two fair coins. State the sample space and find P(exactly one head).

<details><summary>Solution</summary>

S = {HH, HT, TH, TT} (4 outcomes). Exactly one head = {HT, TH}, so P = 2/4 = 1/2.

</details>

**5.** Are "rolling an odd number" and "rolling an even number" mutually exclusive? What is P(odd or even)?

<details><summary>Solution</summary>

Yes, they share no outcomes. So using the disjoint rule, P = 3/6 + 3/6 = 1, meaning one of them is certain.

</details>

### Multiple Choice

**6.** Roll one fair six-sided die. What is P(even or 6)?

- a) 1/6
- b) 1/3
- c) 1/2
- d) 2/3

<details><summary>Solution</summary>

The even numbers are {2, 4, 6}, so the outcome 6 is already counted in "even." P(even) = 3/6 = 1/2, and adding 6 changes nothing.

**Final answer: c) 1/2**

</details>

**7.** If P(A) = 0.6, what is the probability of the complement of A?

- a) 0.4
- b) 0.6
- c) 1.0
- d) 0.24

<details><summary>Solution</summary>

The complement rule gives P(Aᶜ) = 1 − P(A). P(Aᶜ) = 1 − 0.6 = 0.4.

**Final answer: a) 0.4**

</details>
