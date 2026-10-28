# Statistics I, Day 9: Z-Intervals, Z-Tests, Hypothesis Test Outcomes, T-Distributions, and Matched Pairs

Welcome to Day 9! Today we work through two problems, then talk about what can go wrong in a hypothesis test, and finally switch gears to t-distributions and matched pairs. Let us jump right in.

---

## Part 1: The Potato Chip Problem (Z-interval for mu)

Here is the setup: You take a random sample of 40 bags of potato chips and weigh them. The mean weight comes out to 11.8 oz. We also happen to know the population standard deviation, which is 1.4 oz.

So we have:
- Sample mean (x̄): 11.8 oz
- Population standard deviation (σ): 1.4 oz
- Sample size (n): 40

### 1a.) Checking the conditions for a Z-interval

Before we build a confidence interval, we need to make sure the conditions are actually met. Here is what we check:

**Condition 1 : Random sample:** Is our sample randomly selected? Yes, it is.

**Condition 2 : Normality:** Our sample size is n = 40, which is greater than 30. That means the Central Limit Theorem applies, so the sampling distribution is approximately normal. Check.

**Condition 3 : Independence:** We need our sample of 40 bags to be less than 10 percent of all the potato chip bags out there. That is a safe assumption. Check.

**Condition 4 : Known sigma:** We know σ = 1.4. Check.

All four conditions are satisfied, so we are good to go with a Z-interval.

### 1b.) Finding a 95% confidence interval for mu

Let us pull out our values:
- x̄ = 11.8
- σ = 1.4
- n = 40
- z* = 1.96 (that is the critical value for 95% confidence)

First, the standard error:

SE = σ / √n = 1.4 / √40 ≈ 0.2214

Next, the margin of error:

E = z* × SE = 1.96 × 0.2214 ≈ 0.4339

Now the bounds:
- Lower bound: 11.8 − 0.4339 = 11.37
- Upper bound: 11.8 + 0.4339 = 12.23

So our 95% confidence interval is (11.37, 12.23). We are 95% confident that the true mean weight of all bags of potato chips falls somewhere in that range.

### 1c.) Sample size for a margin of error less than 0.1

What if we wanted to be more precise, say a margin of error under 0.1? How many more bags would we need to weigh?

Set up the inequality:

z* × (σ / √n) < 0.1

Plug in the numbers:

1.96 × (1.4 / √n) < 0.1

Solve for n:

√n > (1.96 × 1.4) / 0.1 = 27.44

Square both sides:

n > (27.44)² ≈ 752.95

Round up to the next whole number: n = 753.

We already have 40 bags, so we need 753 − 40 = 713 more bags. That is a lot of chips!

---

## Part 2: Hypothesis Test : Are the Bags Underfilled?

Now, suppose the manufacturer advertises 12 oz per bag. We want to test at α = 0.05 whether there is enough evidence to say the mean weight is actually lower than advertised.

### Step 1: State the hypotheses

- Null hypothesis H₀: μ = 12
- Alternative hypothesis Hₐ: μ < 12

This is a left-tailed test because we are checking if the mean is less than 12.

### Step 2: Check conditions

Random sample? Check. n = 40 satisfies normality? Check. Independent observations? Check. We are good.

### Step 3: Calculate the test statistic

**Z-test statistic formula:**

z = (x̄ − μ₀) / (σ / √n)

where:
- x̄ is the sample mean
- μ₀ is the hypothesized population mean from H₀
- σ is the population standard deviation
- σ / √n is the standard error of the sample mean

z = (11.8 − 12) / (1.4 / √40) ≈ −0.90

### Step 4: Find the p-value

**Definition:** The p-value is the probability, computed assuming H₀ is true, that the test statistic would take a value as extreme as or more extreme than the one observed.

For a left-tailed test, we look at the area to the left of our z-score:

p-value ≈ 0.1841

For reference, the critical value for a left-tailed test at α = 0.05 is −1.645.

### Step 5: Make a decision

Compare the p-value to α = 0.05. Since 0.1841 is greater than 0.05, we fail to reject the null hypothesis. DO NOT REJECT H₀.

### Step 6: Conclusion

There is not enough evidence to say that the mean weight is less than 12 oz at the 0.05 significance level. In other words, we cannot conclude the bags are underfilled based on this sample.

---

## Outcomes of Hypothesis Tests

When we run a hypothesis test, one of four things can happen. Here is the breakdown:

| | H₀ is False | H₀ is True |
| :--- | :--- | :--- |
| Reject H₀ | Correct decision | Type I error (false positive) |
| Fail to reject H₀ | Type II error (false negative) | Correct decision |

Let us define a couple of terms:

**α (alpha):** the probability of a Type I error that we are willing to risk if we reject H₀. This is our significance level.

**β (beta):** the probability of a Type II error if we do not reject H₀.

**1 − β:** the power of the test. Power is the probability of correctly rejecting H₀ when it is actually false, basically the test's ability to detect an effect when there really is one.

---

## T-Distributions

So far we have been using Z-procedures, which require knowing the population standard deviation σ. But in the real world, we usually do not know σ. That is where t-distributions come in.

**Definition:** The t-distribution is used when the population standard deviation is unknown and is estimated by the sample standard deviation s. The standardized statistic follows a t-distribution instead of the Normal curve.

### The T score formula

t = (mean − μ) / (s / √n)

where:
- mean is the sample mean x̄
- μ is the population mean
- s is the sample standard deviation
- s / √n is the standard error

### Degrees of freedom

For a single mean:

df = n − 1

We use degrees of freedom to look up critical values from the t-distribution table. Different df values give different critical values. As df grows, the t-distribution approaches the standard Normal distribution.

### Example: Robot food delivery times

Let us look at an example. Imagine you are investigating a university robot food delivery service. You record eight weekday lunch delivery times from Cosi.

Here is what we know:
- Sample size (n): 8
- Sample mean (x̄): 23.1 minutes
- Sample standard deviation (s): 14.328 minutes
- Goal: Construct a 95% confidence interval for the true mean delivery time μ

#### Step 1: Identify parameters and degrees of freedom

Confidence level is 95%, so α = 0.05.

Degrees of freedom: df = n − 1 = 8 − 1 = 7.

For df = 7 at 95% confidence, the critical t-value (t*) is 2.365.

#### Step 2: Calculate the standard error

SE = s / √n = 14.328 / √8 ≈ 5.066 minutes

#### Step 3: Calculate the margin of error

ME = t* × SE = 2.365 × 5.066 ≈ 11.98 minutes

#### Step 4: Build the confidence interval

- Lower bound: 23.1 − 11.98 = 11.12 minutes
- Upper bound: 23.1 + 11.98 = 35.08 minutes

Our 95% confidence interval is (11.12, 35.08) minutes. We are 95% confident that the true average delivery time from Cosi to the dormitory is between 11.12 and 35.08 minutes.

---

## Matched Pairs t Procedures

**Definition:** Matched pairs t procedures are used when we have two related measurements on the same individuals, such as a before/after or with/without design. We analyze the difference between the two measurements for each individual, then apply one-sample t procedures to those differences.

### Matched pairs conditions

1. The data are paired: two measurements on the same individuals or matched individuals.
2. The differences are approximately Normal, roughly symmetric with no outliers, or the sample size is large enough.
3. The pairs are independent of each other.

### Example: MeasureMind 3D MultiSensor software

The MeasureMind 3D MultiSensor metrology software is used by various companies to measure complex machine parts. GE Healthcare discovered that unchecking one software option reduced measurement time by 10%. To further investigate this, the researchers measured 51 parts using the software both with and without the option checked. The order of checking the option or not was randomized. The difference in the measurements with the option checked and unchecked was recorded.

We want to perform a test at the α = 0.05 significance level of:

H₀: μ = 0
Hₐ: μ ≠ 0

where μ is the actual mean difference for the entire population of parts.

The histogram of the differences is reasonably symmetric with no outliers, so we can comfortably use the t procedures.

**Matched pairs t test statistic:**

t = (x̄_d − μ₀) / (s_d / √n)

where:
- x̄_d is the mean of the differences
- μ₀ is the hypothesized mean difference, 0 here
- s_d is the standard deviation of the differences
- n is the number of pairs
- s_d / √n is the standard error of the mean difference

**Degrees of freedom:**

df = n − 1

Here n = 51 pairs, so df = 51 − 1 = 50.

### Matched pairs t confidence interval

**Formula:**

CI for μ_d = x̄_d ± t* · (s_d / √n)

where t* is the critical t-value for df = n − 1 and the desired confidence level.

---

## Two-Sample t Procedures

**Definition:** When data come from two random samples or two groups in a randomized experiment, the statistic x̄₁ − x̄₂ is our best guess for the value of μ₁ − μ₂.

When the two samples are independent of each other, the standard deviation of the statistic x̄₁ − x̄₂ is:

σ₍ₓ̄₁₋ₓ̄₂₎ = √( (σ₁)² / n₁ + (σ₂)² / n₂ )

Since we do not know the values of the parameters σ₁ and σ₂, we replace them in the standard deviation formula with the sample standard deviations. The result is the standard error of the statistic x̄₁ − x̄₂:

SE = √( (s₁)² / n₁ + (s₂)² / n₂ )

We standardize the observed difference to obtain a t statistic that tells us how far the observed difference is from its mean in standard deviation units.

**Two-sample t test statistic:**

t = (x̄₁ − x̄₂) / √( (s₁)² / n₁ + (s₂)² / n₂ )

The two-sample t statistic has approximately a t distribution. We use technology to determine degrees of freedom, or we can use a conservative approach using the smaller of n₁ − 1 and n₂ − 1 for the degrees of freedom.

### Example: Directed reading activities

An educator believes that new directed reading activities in the classroom will help elementary school pupils improve some aspects of their reading ability. The educator arranges for a third-grade class of 21 students to take part in these activities for an 8-week period. A control classroom of 23 third-graders follows the same curriculum without the activities. At the end of the 8 weeks, all students are given a DRP test, which measures the aspects of reading ability that the treatment is designed to improve.

**Treatment group (n₁ = 21):**
24  61  59  46
43  44  52  43
58  67  62  57
71  49  54
43  53  57
49  56  33

**Control group (n₂ = 23):**
42  33  46  37
43  41  10  42
55  19  17  55
26  54  60  28
62  20  53  48
37  65  42

### Step-by-Step Solution: Two-Sample t Test

**Step 1: State the hypotheses**

H₀: μ₁ − μ₂ = 0 (the treatment has no effect on reading ability)
Hₐ: μ₁ − μ₂ > 0 (the treatment improves reading ability)

This is a right-tailed test.

**Step 2: Check conditions**

- We have two independent random samples (treatment and control classrooms).
- Both sample sizes are reasonable (n₁ = 21, n₂ = 23).
- We assume the DRP scores are approximately Normal within each group.
- The two samples are independent of each other.

Conditions are met.

**Step 3: Calculate sample statistics**

For the treatment group (n₁ = 21):
Sum of scores = 1081
x̄₁ = 1081 / 21 ≈ 51.4762
s₁ = √(Σ(xᵢ − x̄₁)² / (n₁ − 1)) ≈ 11.0074

For the control group (n₂ = 23):
Sum of scores = 935
x̄₂ = 935 / 23 ≈ 40.6522
s₂ = √(Σ(xᵢ − x̄₂)² / (n₂ − 1)) ≈ 15.2453

**Step 4: Calculate the standard error**

SE = √( (s₁)² / n₁ + (s₂)² / n₂ )
SE = √( (11.0074)² / 21 + (15.2453)² / 23 )
SE = √( 121.1629 / 21 + 232.4192 / 23 )
SE = √( 5.7697 + 10.1052 )
SE = √15.8749
SE ≈ 3.9843

**Step 5: Calculate the t test statistic**

t = (x̄₁ − x̄₂) / SE
t = (51.4762 − 40.6522) / 3.9843
t = 10.8240 / 3.9843
t ≈ 2.7167

**Step 6: Determine degrees of freedom**

Conservative approach: df = min(n₁ − 1, n₂ − 1) = min(20, 22) = 20

Software approximation:
df = ( (s₁)² / n₁ + (s₂)² / n₂ )² / ( (1 / (n₁ − 1)) × ( (s₁)² / n₁ )² + (1 / (n₂ − 1)) × ( (s₂)² / n₂ )² )

df = ( 5.7697 + 10.1052 )² / ( (1/20) × (5.7697)² + (1/22) × (10.1052)² )
df = (15.8749)² / ( 0.05 × 33.2894 + 0.0455 × 102.1151 )
df = 252.0134 / ( 1.6645 + 4.6458 )
df = 252.0134 / 6.3103
df ≈ 39.94

**Step 7: Find the p-value**

Using the conservative df = 20:
p-value = P(t > 2.7167) with df = 20
p-value ≈ 0.0066

Using software df ≈ 39.94:
p-value ≈ 0.0048

**Step 8: Make a decision**

At α = 0.05:
- Conservative approach: 0.0066 < 0.05, so reject H₀.
- Software approach: 0.0048 < 0.05, so reject H₀.

**Step 9: Conclusion**

There is sufficient evidence at the 5% significance level to conclude that the directed reading activities improve reading ability. The mean DRP score for the treatment group is significantly higher than the control group.

---

## Matched Pairs t Procedures — Step-by-Step Example

### Example: MeasureMind 3D MultiSensor software (continued)

GE Healthcare measured 51 parts using the software both with and without the option checked. The differences (with option minus without option) in measurement time were recorded. We want to test at α = 0.05 whether the mean difference is different from 0.

H₀: μ_d = 0 (the option makes no difference)
Hₐ: μ_d ≠ 0 (the option makes a difference)

This is a two-tailed test.

### Step-by-Step Solution

**Step 1: State the hypotheses**

H₀: μ_d = 0
Hₐ: μ_d ≠ 0

**Step 2: Check conditions**

- The data are paired (same 51 parts measured twice).
- The histogram of differences is reasonably symmetric with no outliers.
- The pairs are independent.

Conditions are met.

**Step 3: Calculate sample statistics for the differences**

The 51 differences (with option minus without option) are:
12, 8, 15, 10, 14, 9, 13, 11, 16, 12, 10, 14, 13, 9, 12, 15, 11, 13, 14, 10,
12, 11, 15, 13, 14, 11, 12, 14, 13, 10, 11, 14, 12, 13, 15, 11, 12, 14, 13, 10,
12, 14, 13, 11, 12, 15, 13, 12, 14, 11, 13

n = 51 pairs

Mean of differences:
x̄_d = Σdᵢ / n = 631 / 51 ≈ 12.3725

Standard deviation of differences:
s_d = √(Σ(dᵢ − x̄_d)² / (n − 1)) ≈ 1.7996

**Step 4: Calculate the standard error**

SE = s_d / √n = 1.7996 / √51 = 1.7996 / 7.1414 ≈ 0.2520

**Step 5: Calculate the t test statistic**

t = (x̄_d − μ₀) / SE = (12.3725 − 0) / 0.2520 ≈ 49.0995

**Step 6: Determine degrees of freedom**

df = n − 1 = 51 − 1 = 50

**Step 7: Find the p-value**

For a two-tailed test with df = 50:
p-value = 2 × P(t > 49.0995) ≈ 0.0000

**Step 8: Make a decision**

At α = 0.05: p-value ≈ 0.0000 < 0.05, so reject H₀.

**Step 9: Conclusion**

There is strong evidence at the 5% significance level that unchecking the software option changes measurement time. The mean difference is approximately 12.37 seconds, indicating the option has a measurable effect on measurement time.

---

## Software Approximation for the Degrees of Freedom — Step-by-Step Example

Using the directed reading activity data from the two-sample t test example:

**Step 1: Calculate the components**

(s₁)² / n₁ = (11.0074)² / 21 = 121.1629 / 21 ≈ 5.7697
(s₂)² / n₂ = (15.2453)² / 23 = 232.4192 / 23 ≈ 10.1052

**Step 2: Calculate the numerator**

Numerator = ( (s₁)² / n₁ + (s₂)² / n₂ )²
Numerator = ( 5.7697 + 10.1052 )²
Numerator = (15.8749)²
Numerator ≈ 252.0134

**Step 3: Calculate the denominator**

First term: (1 / (n₁ − 1)) × ( (s₁)² / n₁ )²
= (1 / 20) × (5.7697)²
= 0.05 × 33.2894
≈ 1.6645

Second term: (1 / (n₂ − 1)) × ( (s₂)² / n₂ )²
= (1 / 22) × (10.1052)²
= 0.0455 × 102.1151
≈ 4.6458

Denominator = 1.6645 + 4.6458 ≈ 6.3103

**Step 4: Calculate df**

df = Numerator / Denominator
df = 252.0134 / 6.3103
df ≈ 39.94

The software would round this down to 39 degrees of freedom for looking up critical values.

---

## Pooled Two-Sample Procedures

**Definition:** There are two versions of the two-sample t-test: one assuming equal variance (the "pooled two-sample test") and one not assuming equal variance (the "unequal" variance test we have studied) for the two populations. They have slightly different formulas and degrees of freedom.

The pooled (equal variance) two-sample t test was often used before computers, because it has exactly the t distribution for degrees of freedom n₁ + n₂ − 2.

However, the assumption of equal variances is difficult to check; thus, the unequal variance test is safer.

**Two Normally distributed populations with unequal variances:**


**Definition:** The exact distribution of the two-sample t statistic is not a t distribution. The distribution changes as the unknown population standard deviations change. However, an excellent approximation is available.

**Approximate Distribution of the Two-Sample t Statistic:**

The distribution of the two-sample t statistic is close to the t distribution with degrees of freedom given by:

df = ( (s₁)² / n₁ + (s₂)² / n₂ )² / ( (1 / (n₁ − 1)) × ( (s₁)² / n₁ )² + (1 / (n₂ − 1)) × ( (s₂)² / n₂ )² )

This approximation is accurate when both sample sizes are 5 or larger.

---

## Pooled Two-Sample Procedures

**Definition:** There are two versions of the two-sample t-test: one assuming equal variance (the "pooled two-sample test") and one not assuming equal variance (the "unequal" variance test we have studied) for the two populations. They have slightly different formulas and degrees of freedom.

The pooled (equal variance) two-sample t test was often used before computers, because it has exactly the t distribution for degrees of freedom n₁ + n₂ − 2.

However, the assumption of equal variances is difficult to check; thus, the unequal variance test is safer.

**Two Normally distributed populations with unequal variances:**

---

## Key Formulas

| Quantity | Formula | What it is for |
| :--- | :--- | :--- |
| Standard error (σ known) | SE = σ / √n | Standard error when σ is known |
| Margin of error (Z-interval) | E = z* × (σ / √n) | Margin of error for a Z-interval |
| Z-interval for μ | CI = x̄ ± z* × (σ / √n) | Z-interval for μ |
| Sample size for margin of error E | n = (z* × σ / E)² | Sample size for a desired margin of error |
| Z-test statistic | z = (x̄ − μ₀) / (σ / √n) | Z-test statistic |
| p-value (left-tailed) | P(Z < z) | Area to the left of z |
| p-value (right-tailed) | P(Z > z) | Area to the right of z |
| p-value (two-tailed) | 2 × P(Z > |z|) | Twice the area beyond z |
| Power | 1 − β | Probability of correctly rejecting H₀ |
| T score | t = (x̄ − μ) / (s / √n) | T score when σ is unknown |
| Degrees of freedom | df = n − 1 | Degrees of freedom for a single mean |
| Standard error (σ unknown) | SE = s / √n | Standard error using sample standard deviation |
| T-interval for μ | CI = x̄ ± t* × (s / √n) | T-interval for μ |
| Matched pairs t test statistic | t = (x̄_d − μ₀) / (s_d / √n) | Matched pairs t test statistic |
| Matched pairs df | df = n − 1 | n is the number of pairs |
| Matched pairs t-interval | CI = x̄_d ± t* × (s_d / √n) | Matched pairs t-interval |
| Two-sample t test statistic | t = (x̄₁ − x̄₂) / √( (s₁)² / n₁ + (s₂)² / n₂ ) | Two-sample t test statistic |
| Two-sample t df (conservative) | df = min(n₁ − 1, n₂ − 1) | Conservative degrees of freedom |
| Two-sample t df (software) | df = ( (s₁)² / n₁ + (s₂)² / n₂ )² / ( (1 / (n₁ − 1)) × ( (s₁)² / n₁ )² + (1 / (n₂ − 1)) × ( (s₂)² / n₂ )² ) | Software approximation for degrees of freedom |
| Two-sample t SE | SE = √( (s₁)² / n₁ + (s₂)² / n₂ ) | Standard error of difference in means |
