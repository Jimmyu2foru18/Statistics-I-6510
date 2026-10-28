# Statistics I, Day 1: Data, Variables, and Distributions

Welcome to Day 1! Today we are starting at the very beginning. We will look at what a data set actually is, the different kinds of variables we measure, how precisely we can measure them, and our first tool for visualizing a distribution: the stem-and-leaf plot. Everything today falls under descriptive statistics, which means organizing, summarizing, and displaying data so we can make sense of it.

---

## 1. Data Basics: Cases and Variables

A data set is organized like a spreadsheet or matrix:

- A **case** (also called an observation, subject, or individual) is one row. It is the single entity we are describing.
- A **variable** is one column. It is a characteristic we record for every case.

Think of a case as the "who" or "what" in your data, and a variable as the "what we know about them."

### Student Data Example

| ID # | GPA | Major | Full-time |
| :---: | :---: | :---: | :---: |
| 7005392 | 3.95 | History | Yes |
| 7003415 | 3.71 | Bio | No |
| 7002591 | 3.24 | Math | No |
| 7003425 | 2.25 | History | Yes |
| 7001573 | 3.75 | Business | No |

In this table there are **5 cases** (one per student) and **4 variables** (ID, GPA, Major, Full-time). Each row tells us something about one student, and each column tells us one characteristic measured across all students.

---

## 2. Two Broad Types of Variables

Variables come in two broad families: quantitative and categorical.

| Type | Also called | Describes | Examples here |
| :--- | :--- | :--- | :--- |
| Quantitative | Numerical | A numeric amount or count | GPA |
| Categorical | Qualitative | A category or label | Major, Full-time |

### A. Quantitative Variables (Numerical)

A quantitative variable records a number that represents an amount or a count. These split into two families based on the values they can take:

**Discrete variables** can take on only specific, listable values. They usually come from counting, and there are gaps between possible values. You cannot have 2.5 classes, for example.
- Examples: number of classes a student is enrolled in, number of full-time students in a sample.
- Notation: X takes values like 0, 1, 2, 3, ... (whole numbers only).

**Continuous variables** can take on any value within a range. Between any two possible values, there are always infinitely many more possible values. They usually come from measuring.
- Examples: GPA (values from 0.00 to 4.00), study time such as 3.456 hours.

**How to tell them apart:** Ask yourself, "Did I count this, or did I measure this?" If you counted it, it is discrete. If you measured it, it is continuous.

---

## 3. Levels of Measurement (NOIR)

A second, finer way to classify any variable is by asking what mathematical operations are meaningful on its values. The four levels, from least to most informative, are Nominal, Ordinal, Interval, and Ratio. Each level builds on the one before it.

**1. Nominal:** Values are just names or categories. There is no inherent order.
- Example: Major (History, Bio, Math, Business) or eye color. No major is "greater than" another.

**2. Ordinal:** Values can be ordered or ranked, but the distance between categories is not meaningful or uniform.
- Example: Yelp star ratings (1–5 stars) or letter grades (A, B, C, D, F). We know A is better than B, but the gap between A and B is not necessarily the same as the gap between B and C.

**3. Interval:** Values can be ordered and subtracted to get exact differences, but there is no true or meaningful zero. Ratios like "twice as much" are not valid.
- Example: Temperature in degrees Fahrenheit or Celsius. 40°F is not "twice as hot" as 20°F because 0°F does not mean "no heat."

**4. Ratio:** Has everything interval data has, plus a true, meaningful zero where 0 means the complete absence of the quantity. Ratios are valid.
- Example: number of pages in a book, money, age. A 400-page book has exactly twice as many pages as a 200-page book (400 divided by 200 equals 2).

### Cheat Sheet

| Level | Order? | Equal spacing? | True zero? | Ratios OK? |
| :--- | :---: | :---: | :---: | :---: |
| Nominal | No | No | No | No |
| Ordinal | Yes | No | No | No |
| Interval | Yes | Yes | No | No |
| Ratio | Yes | Yes | Yes | Yes |

**Memory aid:** The levels are cumulative. Each one adds a new ability. "NOIR" also reminds you of the order, from weakest (N) to strongest (R).

---

## 4. Stem-and-Leaf Plots

A stem-and-leaf plot (also called a stemplot) is an exploratory tool for quantitative data. It shows the shape of the distribution while preserving the exact data values. The leading digit or digits become the stem, and the final digit becomes the leaf.

### Worked Example (from class slide 15)

| Stem | Leaves |
| :---: | :--- |
| 10 | 0, 6 |
| 11 | 0, 0, 9 |
| 12 | 0, 0, 3, 8 |
| 13 | 5, 9 |
| 14 | |
| 15 | 0, 2 |
| 16 | 5, 5, 5 |
| 17 | 0, 0, 5 |
| 18 | 0, 5, 5, 5, 6 |
| 19 | 2, 5 |
| 20 | 3 |
| 21 | 0, 2 |
| 22 | |
| 23 | |
| 24 | |
| 25 | |
| 26 | 0 |

**Key:** 10 | 6 means 106. The stem row "14" has no data, so it is left blank.

Reading the leaves lets you reconstruct the exact original data. A histogram cannot do that because it only shows counts per bin.

---

## 5. Distribution Shapes

When we look at a histogram or stemplot, we describe the shape of the distribution:

| Shape | Description |
| :--- | :--- |
| Uniform | Every value or bin occurs with roughly equal frequency, so the profile is flat. |
| Unimodal | One clear peak (the mode). |
| Bimodal | Two distinct peaks. This is often a sign that two different subgroups are mixed in the data. |
| Multimodal | More than two peaks. |

### Time Plot (Time Series)

A time plot graphs each value in chronological order, with time on the x-axis and the variable on the y-axis. Its purpose is to study change over time, such as trends and cycles, rather than looking at a single snapshot.

---

## 6. Quick Reference: Classifying a Variable

| Question | Answer | Type or Level |
| :--- | :--- | :--- |
| Is it a number you count? | Yes | Quantitative, discrete |
| Is it a number you measure? | Yes | Quantitative, continuous |
| Is it just a label or category? | Yes | Categorical, nominal |
| Can it be ranked, but distances are unclear? | Yes | Categorical, ordinal |
| Equal spacing but no true zero? | Yes | Interval (ratios invalid) |
| Has a true zero, so ratios are valid? | Yes | Ratio |

---

## 7. Practice Problems

**1.** Classify each variable as categorical or quantitative (and if quantitative, discrete or continuous):
(a) number of siblings, (b) blood type, (c) commute time in minutes, (d) jersey number.

<details><summary>Solution</summary>

(a) Quantitative discrete: you count siblings in whole numbers.
(b) Categorical and nominal: blood type is a label with no order.
(c) Quantitative continuous: commute time is measured and can be 24.7 minutes.
(d) Categorical and nominal: jersey numbers are labels, not quantities you can meaningfully average or rank.

</details>

**2.** Give the level of measurement (NOIR) for each: (a) type of cuisine, (b) satisfaction rating 1–5, (c) temperature in °C, (d) height in cm.

<details><summary>Solution</summary>

(a) Nominal: type of cuisine is just a label.
(b) Ordinal: satisfaction ratings are ranked 1 to 5, but the gaps between ratings are not guaranteed to be equal.
(c) Interval: temperature in °C. Differences are meaningful, but there is no true zero, so 40 °C is not "twice as hot" as 20 °C.
(d) Ratio: height in cm. There is a true zero, so 180 cm is twice 90 cm.

</details>

**3.** From the class stem-and-leaf plot, what are the minimum and maximum values, and where do the data cluster?

<details><summary>Solution</summary>

Minimum equals 10 | 0 = 100. Maximum equals 26 | 0 = 260. Most values cluster in the 170s to 180s (the long rows 16, 17, 18), suggesting a peak around there with a long right tail.

</details>

**4.** True or False: because a stemplot shows individual data values, it reveals the exact data set, unlike a histogram.

<details><summary>Solution</summary>

True. A stemplot preserves every observation given the key, while a histogram only shows counts per bin.

</details>

### Multiple Choice

**5.** Temperature measured in degrees Celsius is best described as which level of measurement?

- a) Nominal
- b) Ordinal
- c) Interval
- d) Ratio

<details><summary>Solution</summary>

Differences (subtraction) are meaningful, so it is at least interval. There is no true zero because 0 °C is not "no heat," so ratios like "twice as hot" are invalid.

**Final answer: c) Interval**

</details>

**6.** The number of songs on a phone is which type of variable?

- a) Continuous, because you can always add more
- b) Discrete, because it is counted in whole numbers
- c) Ordinal, because songs can be ranked
- d) Nominal, because songs have names

<details><summary>Solution</summary>

The value comes from counting, and only whole numbers are possible. Counted whole numbers are discrete, not continuous.

**Final answer: b) Discrete, because it is counted in whole numbers**

</details>
