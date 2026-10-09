# Statistics I - Day 1 Class Notes

## 1. Introduction to Data and Variables

In statistics, a **case** (or observation/subject/individual) is an entity about which we collect data. **Variables** are the characteristics measured or recorded for each case.

### Student Data Example

Below is a sample dataset illustrating different types of cases and variables:

| ID # | GPA | Major | Full-time | 
| ----- | ----- | ----- | ----- | 
| 7005392 | 3.95 | History | Yes | 
| 7003415 | 3.71 | Bio | No | 
| 7002591 | 3.24 | Math | No | 
| 7003425 | 2.25 | History | Yes | 
| 7001573 | 3.75 | Business | No | 

---

## 2. Types of Quantitative Variables

Quantitative variables represent numerical amounts or counts. They can be further categorized into discrete and continuous types:

* **Discrete Variables:**
  * Variables that can only take on specific, distinct values which can be listed in order without skipping any possible values (typically whole numbers resulting from a counting process).
  * *Example Problems & Context:* 
    * Number of full-time students in a sample ($X \in \{0, 1, 2, 3, \dots\}$).
    * Number of classes a student is currently enrolled in.

* **Continuous Variables:**
  * Variables that can take on any real value within a specified finite or infinite range. Between any two possible values, there is always an infinite number of possible intermediate values (typically measurements requiring tools or precision).
  * *Example Problems & Context:*
    * Student Grade Point Average ($GPA$), where values can range continuously, e.g., $GPA \in [0.00, 4.00]$.
    * Exact study time measured in hours: $t = 3.456\text{ hours}$.

---

## 3. Levels of Measurement

An alternate way to categorize variables based on the mathematical properties and operations we can perform with their values:

1. **Nominal Level of Measure**
   * *Definition:* Values can be categorized or named, but there is no inherent mathematical order or ranking to the categories.
   * *Example:* Student Major (History, Bio, Math, Business) or Eye Color. No category is "greater than" another.

2. **Ordinal Level of Measure**
   * *Definition:* Values can be categorized and placed in a meaningful order or rank, but there is no consistent or measurable mathematical distance between the categories.
   * *Example:* Ratings on Yelp ($1$ star to $5$ stars) or letter grades ($A, B, C, D, F$). We know an $A$ grade is higher than a $B$, but the exact numerical difference in performance between an $A$ and a $B$ cannot be strictly quantified uniformly.

3. **Interval Level of Measure**
   * *Definition:* Values can be ordered and subtracted to determine exact numerical distances between them ($x_2 - x_1$). However, they *cannot* be compared multiplicatively (e.g., saying one value is "twice as much" as another) because there is no true or meaningful absolute zero point.
   * *Example:* Temperature in Fahrenheit or Celsius. If it is $40^\circ\text{F}$, it is not literally "twice as hot" as $20^\circ\text{F}$ because $0^\circ\text{F}$ does not mean a complete absence of thermal energy.

4. **Ratio Level of Measure**
   * *Definition:* Features all the mathematical properties of interval data, plus a **true, meaningful absolute zero** point ($0$ represents the complete absence of the quantity). Because of this, we can make valid multiplicative comparisons using ratios ($\frac{x_2}{x_1}$).
   * *Example:* Number of pages in a book, money in a bank account, or GPA. If a book has $400$ pages and another has $200$ pages, the first book literally has twice ($\frac{400}{200} = 2$) as many pages.

---

## 4. Graphical Displays: Stem-and-Leaf Plots

A **stem-and-leaf plot** is an exploratory data analysis tool used to display quantitative data while preserving the exact individual data values. The leading digit(s) form the "stem," and the trailing digit forms the "leaf."

### Slide 15: Stem Plot Example

| Stem | Leaves | | | | | 
| ----- | ----- | ----- | ----- | ----- | ----- | 
| **10** | $0$ | $6$ | | | | 
| **11** | $0$ | $0$ | $9$ | | | 
| **12** | $0$ | $0$ | $3$ | $8$ | | 
| **13** | $5$ | $9$ | | | | 
| **14** | | | | | | 
| **15** | $0$ | $2$ | | | | 
| **16** | $5$ | $5$ | $5$ | | | 
| **17** | $0$ | $0$ | $5$ | | | 
| **18** | $0$ | $5$ | $5$ | $5$ | $6$ | 
| **19** | $2$ | $5$ | | | | 
| **20** | $3$ | | | | | 
| **21** | $0$ | $2$ | | | | 
| **22** | | | | | | 
| **23** | | | | | | 
| **24** | | | | | | 
| **25** | | | | | | 
| **26** | $0$ | | | | | 

---

## 5. Distribution Shapes and Trends

When analyzing data distributions visually through histograms or stem-and-leaf plots, we classify their structural patterns:

* **Uniform Distribution:**
  * The frequency or probability of each value is evenly spread out across the range; the heights of the distribution maintain roughly flat continuity.

* **Bimodal Distribution:**
  * A distribution that features **two distinct peaks** (modes). This frequently suggests that the sampled dataset contains two distinct underlying subgroups or populations mixed together.

* **Multimodal Distribution:**
  * A distribution containing **more than two distinct peaks**, showing multiple common clustering points or modes within the data.

* **Time Plot (Time Series):**
  * A specialized sequential graph where data values are plotted in chronological order over time ($t$), with time mapped along the horizontal axis ($x$-axis) and the variable value along the vertical axis ($y$-axis). Its core objective is to analyze dynamic behavior, cycles, and **change over time**.