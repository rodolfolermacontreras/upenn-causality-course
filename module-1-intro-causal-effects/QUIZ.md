# Module 1 Quiz: Introduction to Causal Effects

**Course:** A Crash Course in Causality (University of Pennsylvania)  
**Instructor:** Jason A. Roy, Ph.D.  

---

## Graded Quiz (2026-09-09)

### Question 1
The *Fundamental Problem of Causal Inference* is that:

- [ ] causal effects are only well defined for hypothetical interventions
- [x] we can only observe one potential outcome for each subject
- [ ] treatment is typically not randomly assigned

**Answer:** we can only observe one potential outcome for each subject

**Why:**  
For each individual at any given time, they either receive the treatment or they do not. We observe $Y = Y^A$, while the counterfactual outcome under the alternative condition is unobservable. Causal inference is therefore fundamentally a missing data problem.

---

### Question 2
Which of the following represents the causal effect of treatment on the treated?

- [ ] $E(Y^1|A=1) - E(Y^1|A=0)$
- [x] $E(Y^1|A=1) - E(Y^0|A=1)$
- [ ] $E(Y^1) - E(Y^0)$
- [ ] $E(Y|A=1) - E(Y|A=0)$

**Answer:** $E(Y^1|A=1) - E(Y^0|A=1)$

**Why:**  
This is the Average Treatment Effect on the Treated (ATT). It compares the average outcome the treated subjects experienced ($Y^1$) against the counterfactual outcome they would have experienced without treatment ($Y^0$), conditioned on having received treatment ($A=1$).

---

### Question 3
Which of the following represents the average causal effect for the population?

- [ ] $E(Y|A=1) - E(Y|A=0)$
- [ ] $E(Y^1|A=1) - E(Y^1|A=0)$
- [x] $E(Y^1) - E(Y^0)$
- [ ] $E(Y^1|A=1) - E(Y^0|A=1)$

**Answer:** $E(Y^1) - E(Y^0)$

**Why:**  
This is the Average Treatment Effect (ATE). It is the difference in expectations of the two potential outcomes across the entire target population, regardless of actual treatment received.

---

### Question 4
Which assumption would be violated if the effectiveness of treatment on an individual depended on the treatment status of other individuals?

- [ ] Consistency
- [x] SUTVA
- [ ] Ignorability
- [ ] Positivity

**Answer:** SUTVA (Stable Unit Treatment Value Assumption)

**Why:**  
SUTVA requires no interference between units. If one individual's outcome is altered by whether another person is treated (for example, infectious disease contagion, herd immunity, or network peer effects), SUTVA is violated.

---

### Question 5
Which assumption would be violated if we were interested in the causal effect of treatment for people age 40-80, but *everyone* over age 70 received the treatment?

- [x] Positivity
- [ ] Ignorability
- [ ] SUTVA
- [ ] Consistency

**Answer:** Positivity

**Why:**  
Positivity requires that within every covariate stratum, each individual has a non-zero probability of receiving both treatment and control ($0 < P(A=a \mid X=x) < 1$). If everyone over 70 is treated, $P(A=0 \mid \text{Age} > 70) = 0$. There are no untreated controls over age 70 to estimate the counterfactual $E(Y^0 \mid \text{Age} > 70)$.

---

### Question 6
If the consistency assumption holds, then the observed outcome for a treated subject is equal to their potential outcome under that treatment.

- [ ] False
- [x] True

**Answer:** True

**Why:**  
Consistency means $Y = A \cdot Y^1 + (1-A) \cdot Y^0$. If subject $i$ received treatment ($A_i = 1$), their observed outcome $Y_i$ is identical to their potential outcome $Y_i^1$.

---

### Question 7
Which of the following can most easily be thought of as an intervention?

- [ ] Changing blood pressure
- [ ] Changing weight
- [ ] Changing ethnicity
- [x] Changing medication

**Answer:** Changing medication

**Why:**  
Causal inference requires a well-defined manipulation ("no causation without manipulation"). You can directly prescribe or switch medication in an experiment. Blood pressure and weight are internal physiological states with many possible causes, and ethnicity is an immutable demographic attribute.

---

### Question 8
Treatment assignment being ignorable given confounders, X, means:

- [ ] Treatment assignment is independent from X.
- [ ] Treatment assignment is independent from the observed outcomes, given X.
- [x] Within levels of X, treatment assignment is independent from the potential outcomes.

**Answer:** Within levels of X, treatment assignment is independent from the potential outcomes.

**Why:**  
Ignorability (conditional exchangeability) is formally written as $(Y^0, Y^1) \perp A \mid X$. Within any stratum where covariates $X$ are held fixed, treatment assignment $A$ gives no additional information about what outcomes the subjects would experience under either treatment.

---

### Question 9
Computing means within levels of covariates and then combining these estimates is known as

- [ ] calibration
- [x] standardization
- [ ] factor analysis

**Answer:** standardization

**Why:**  
Standardization (the discrete G-formula) first stratifies on covariates $X$ to calculate conditional outcome means $E(Y \mid A=a, X=x)$, then computes a weighted average across all strata using the marginal distribution $P(X=x)$.

---

## Practice Quiz Items (2026-09-08 / 2026-09-09)

### Item A
Which of the following represents what the average outcome would have been had no one been treated?
* **Answer:** $E(Y^0)$
* **Why:** $Y^0$ is the potential outcome under control. Taking its expectation across the population yields the average outcome if no one received treatment.

### Item B
Which assumption is also referred to as the 'no unmeasured confounders' assumption?
* **Answer:** ignorability
* **Why:** Ignorability asserts that all variables affecting both treatment choice and outcome are captured in $X$, leaving treatment conditionally unconfounded.
