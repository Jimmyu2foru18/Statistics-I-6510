# Statistics I - Chapter 4 Notes: Probability

## 1. Core Framework and Definitions
Probability is a numerical measure of how likely something is to occur[cite: 4].

* **Random Experiment / Process**: Any process in which the result is determined by chance[cite: 4].
* **Outcome**: Any single possible result of the random experiment or process[cite: 4].
* **Sample Space ($S$)**: The set of all possible outcomes to a random experiment or process[cite: 4].
* **Event**: Any set of one or more outcomes[cite: 4].

### Worked Examples: Sample Spaces and Events
* **Example 1: Rolling a 6-sided die**[cite: 4]
  * Sample Space: $S = \{1, 2, 3, 4, 5, 6\}$[cite: 4]
  * Event $A$ (Odd numbers): $A = \{1, 3, 5\}$[cite: 4]
  * Event $B$ (Rolling a number $< 5$): $B = \{1, 2, 3, 4\}$[cite: 4]

* **Example 2: Flipping a coin 3 times**[cite: 4]
  * Sample Space: $S = \{\text{HHH}, \text{HHT}, \text{HTH}, \text{HTT}, \text{THH}, \text{THT}, \text{TTH}, \text{TTT}\}$[cite: 4]
  * Event $A$ (At least one head): $A = \{\text{HHH}, \text{HHT}, \text{HTH}, \text{HTT}, \text{THH}, \text{THT}, \text{TTH}\}$[cite: 4]
  * Event $B$ (2 of the same in a row): $B = \{\text{HHH}, \text{HHT}, \text{HTT}, \text{TTH}, \text{TTT}\}$[cite: 4]

---

## 2. Senses of Probability
* **Classical / Theoretical Probability**: The probability $P(A)$ for an event $A$ is the number of outcomes in $A$ divided by the total number of outcomes in the sample space $S$[cite: 4].
  $$P(A) = \frac{\text{# of outcomes in } A}{\text{# of outcomes in } S} = \frac{n(A)}{n(S)}$$[cite: 4]
* **Empirical / Experimental Probability**: The probability $P(A)$ of an event $A$ is the number of times $A$ occurs divided by the total number of trials[cite: 4].
  $$P(A) = \frac{\text{# of times } A \text{ Occurs}}{\text{Number of Trials}}$$[cite: 4]
* **Subjective Probability**: An estimate of probability based on expert opinion[cite: 4].
* **Law of Large Numbers**: As the number of trials approaches infinity, the limit of the empirical probability approaches the classical probability[cite: 4].

---

## 3. Rules for Probability
* **Bounds**: For any event $A$:
  $$0 \le P(A) \le 1$$[cite: 4]
  * If $P(A) = 0$, the event is impossible[cite: 4].
  * If $P(A) = 1$, the event is certain[cite: 4]. The closer $P(A)$ is to $1$, the more likely it is to occur[cite: 4].

* **Complement Rule**: For a complement event $A^c$ (or $A'$):
  $$P(A) + P(A^c) = 1 \quad \text{or} \quad P(A^c) = 1 - P(A)$$[cite: 4]

* **Law of Total Probability**: If $A_1, A_2, \dots, A_n$ are disjointed (mutually exclusive) events such that every outcome in $S$ is in exactly one of them:
  $$P(A_1) + P(A_2) + \dots + P(A_n) = 1$$[cite: 4]

* **Addition Rule for "OR"**:
  * **In General**: For any two events $A$ and $B$:
    $$P(A \text{ or } B) = P(A) + P(B) - P(A \text{ and } B)$$[cite: 4]
  * **Special Case (Mutually Exclusive)**: If $A$ and $B$ cannot happen simultaneously:
    $$P(A \text{ or } B) = P(A) + P(B)$$[cite: 4]

---

## 4. Worked Problem Set
**Problem 1**: You roll a standard six-sided die ($S = \{1, 2, 3, 4, 5, 6\}$). Find $P(3 \text{ or Even})$[cite: 4].
* Note: Rolling a $3$ and rolling an even number are **mutually exclusive** events[cite: 4].
* Calculation:
  $$P(3 \text{ or Even}) = P(3) + P(\text{Even}) = \frac{1}{6} + \frac{3}{6} = \frac{4}{6} = \frac{2}{3}$$[cite: 4]

**Problem 2**: Using the same standard six-sided die, find $P(\text{odd or } > 2)$[cite: 4].
* Let $A = \text{odd} = \{1, 3, 5\}$ and $B = > 2 = \{3, 4, 5, 6\}$. These events are not mutually exclusive (they share $\{3, 5\}$).
* Using the general addition rule:
  $$P(\text{odd} \text{ or } > 2) = P(\text{odd}) + P(> 2) - P(\text{odd and } > 2)$$[cite: 4]
  $$P(\text{odd} \text{ or } > 2) = \frac{3}{6} + \frac{4}{6} - \frac{2}{6} = \frac{5}{6} \approx 0.8333$$[cite: 4]
```[cite: 4]
