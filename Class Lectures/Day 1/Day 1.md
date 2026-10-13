# Statistics I, Day 1: Data, Variables, and Distributions

## Overview
Today's focus is on the **language of data**: what a data set is made of, the different kinds of variables we measure, how precisely we can measure them, and the first tools we use to *visualize* a distribution (stem-and-leaf plots). Everything here is **descriptive statistics**: organizing, summarizing, and displaying data.

---

## 1. Data Basics: Cases and Variables

A data set is organized as a **matrix**:

- A **case** (also called an *observation*, *subject*, or *individual*) is one row: the entity we describe.
- A **variable** is one column: a characteristic we record for every case.

### Student Data Example

| ID # | GPA | Major | Full-time |
| :---: | :---: | :---: | :---: |
| 7005392 | 3.95 | History | Yes |
| 7003415 | 3.71 | Bio | No |
| 7002591 | 3.24 | Math | No |
| 7003425 | 2.25 | History | Yes |
| 7001573 | 3.75 | Business | No |

In this table there are **5 cases** (one per student) and **4 variables** (ID, GPA, Major, Full-time).

---

## 2. Two Broad Types of Variables

| Type | Also called | Describes | Examples here |
| :--- | :--- | :--- | :--- |
| **Quantitative** | Numerical | A numeric **amount** or **count** | GPA |
| **Categorical** | Qualitative | A **category** or **label** | Major, Full-time |

### A. Quantitative Variables (Numerical)

Quantitative variables are split into two families by the values they can take:

- **Discrete variables**: can take on only *specific, listable* values, typically from **counting**. There are "gaps" between possible values.
  - Examples: number of classes a student is enrolled in, number of full-time students in a sample.
  - $X \in \{0, 1, 2, 3, \dots\}$ (whole numbers only).

- **Continuous variables**: can take on *any* value within a range; between any two possible values there are always **infinitely many** more possible values, typically from **measuring**.
  - Examples: GPA ($GPA \in [0.00, 4.00]$), study time $t = 3.456\text{ hours}$.

> **How to tell them apart:** Ask yourself: *"Did I count this or measure this?"* Counting → discrete. Measuring → continuous.

---

## 3. Levels of Measurement (NOIR)

A second, finer way to classify *any* variable is by asking **what mathematical operations are meaningful** on its values. The four levels, from least to most informative, are **N**ominal, **O**rdinal, **I**nterval, **R**atio.

1. **Nominal**: Values are just *names/categories*; there is **no inherent order**.
   - Example: Major (History, Bio, Math, Business) or eye color. No major is "greater than" another.

2. **Ordinal**: Values can be *ordered/ranked*, but the **distance between categories is not meaningful or uniform**.
   - Example: Yelp star ratings (1–5 stars) or letter grades ($A, B, C, D, F$). We know $A > B$, but the "gap" between $A$ and $B$ isn't necessarily the same as between $B$ and $C$.

3. **Interval**: Values can be *ordered* and *subtracted* to get exact differences ($x_2 - x_1$), but there is **no true/meaningful zero**, so ratios ("twice as much") are not valid.
   - Example: Temperature in $^\circ\text{F}$ or $^\circ\text{C}$. $40^\circ\text{F}$ is **not** "twice as hot" as $20^\circ\text{F}$ because $0^\circ\text{F}$ is not "no heat."

4. **Ratio**: Has everything interval data has **plus a true, meaningful zero** ($0$ = complete absence of the quantity). Ratios are valid.
   - Example: number of pages in a book, money, age. A 400-page book has exactly **twice** as many pages as a 200-page book ($\frac{400}{200} = 2$).

### Cheat Sheet

| Level | Order? | Equal spacing? | True zero? | Ratios (×) OK? |
| :--- | :---: | :---: | :---: | :---: |
| Nominal | No | No | No | No |
| Ordinal | Yes | No | No | No |
| Interval | Yes | Yes | No | No |
| Ratio | Yes | Yes | Yes | Yes |

> **Memory aid:** The levels are **cumulative**: each one adds a new ability. "NOIR" also reminds you the order, from weakest (N) to strongest (R).

---

## 4. Stem-and-Leaf Plots

A **stem-and-leaf plot** (a.k.a. *stemplot*) is an exploratory tool for **quantitative** data that shows the shape of the distribution **while preserving the exact data values**. The **leading digit(s)** become the *stem*; the **final digit** becomes the *leaf*.

### Worked Example (class Slide 15)

| Stem | Leaves | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **10** | 0 | 6 | | | |
| **11** | 0 | 0 | 9 | | |
| **12** | 0 | 0 | 3 | 8 | |
| **13** | 5 | 9 | | | |
| **14** |  | | | | |
| **15** | 0 | 2 | | | |
| **16** | 5 | 5 | 5 | | |
| **17** | 0 | 0 | 5 | | |
| **18** | 0 | 5 | 5 | 5 | 6 |
| **19** | 2 | 5 | | | |
| **20** | 3 | | | | |
| **21** | 0 | 2 | | | |
| **22** |  | | | | |
| **23** |  | | | | |
| **24** |  | | | | |
| **25** |  | | | | |
| **26** | 0 | | | | |

**Key:** $10 \mid 6 = 106$. (The stem row "14" has no data, so it is left blank.)

Reading the leaves lets you reconstruct the *exact* original data, something a histogram cannot do.

---

## 5. Distribution Shapes

When we look at a histogram or stemplot, we describe the **shape** of the distribution:

| Shape | Description |
| :--- | :--- |
| **Uniform** | Every value (or bin) occurs with roughly *equal* frequency, so the profile is flat. |
| **Unimodal** | One clear peak (the *mode*). |
| **Bimodal** | **Two** distinct peaks, often a sign that two different subgroups are mixed in the data. |
| **Multimodal** | **More than two** peaks. |

### Time Plot (Time Series)

A **time plot** graphs each value in **chronological order**, with *time* on the $x$-axis and the variable on the $y$-axis. Its purpose is to study **change over time**, such as trends and cycles, rather than a single snapshot.

---

## 6. Quick Reference: Classifying a Variable

| Question | Answer | Type/Level |
| :--- | :--- | :--- |
| Is it a number you **count**? | Yes | Quantitative (discrete) |
| Is it a number you **measure**? | Yes | Quantitative (continuous) |
| Is it just a **label/category**? | Yes | Categorical (nominal) |
| Can it be **ranked** but distances unclear? | Yes | Categorical (ordinal) |
| Equal spacing but **no true zero**? | Yes | **Interval** (ratios invalid) |
| Has a **true zero** (ratios valid)? | Yes | **Ratio** |

---

## 7. Practice Problems

**1.** Classify each variable as categorical or quantitative (and if quantitative, discrete or continuous):
(a) number of siblings, (b) blood type, (c) commute time in minutes, (d) jersey number.

<details><summary>Solution</summary>

(a) quantitative discrete (you count siblings); (b) categorical and nominal (a label); (c) quantitative continuous (measured time can be 24.7 min); (d) categorical and nominal, since jersey numbers are labels rather than quantities you can average or rank.

</details>

**2.** Give the level of measurement (NOIR) for each: (a) type of cuisine, (b) satisfaction rating 1–5, (c) temperature in °C, (d) height in cm.

<details><summary>Solution</summary>

(a) Nominal; (b) Ordinal (ranked, but the "gaps" aren't guaranteed equal); (c) Interval, since differences are meaningful but there is no true zero, so 40 °C isn't "twice as hot" as 20 °C; (d) Ratio, since there is a true zero, so 180 cm is twice 90 cm.

</details>

**3.** From the class stem-and-leaf plot, what are the minimum and maximum values, and where do the data cluster?

<details><summary>Solution</summary>

Minimum $= 10\mid0 = 100$; maximum $= 26\mid0 = 260$. Most values cluster in the 170s–180s (the long rows 16, 17, 18), suggesting a peak around there with a long right tail.

</details>

**4.** True or False: because a stemplot shows individual data values, it reveals the exact data set, unlike a histogram.

<details><summary>Solution</summary>

**True.** A stemplot preserves every observation (given the key), while a histogram only shows counts per bin.

</details>

### Multiple Choice

**5.** Temperature measured in degrees Celsius is best described as which level of measurement?

- **a)** Nominal
- **b)** Ordinal
- **c)** Interval
- **d)** Ratio

<details><summary>Solution</summary>

- Differences (subtraction) are meaningful, so it is at least interval.
- There is no true zero ($0^\circ\text{C}$ is not "no heat"), so ratios like "twice as hot" are invalid.

**Final answer: (c) Interval**

</details>

**6.** The number of songs on a phone is which type of variable?

- **a)** Continuous, because you can always add more
- **b)** Discrete, because it is counted in whole numbers
- **c)** Ordinal, because songs can be ranked
- **d)** Nominal, because songs have names

<details><summary>Solution</summary>

- The value comes from counting, and only whole numbers are possible.
- Counted whole numbers are discrete, not continuous.

**Final answer: (b) Discrete, because it is counted in whole numbers**

</details>
