# Stratification and Standardization

## 1. What It Solves
Observational comparisons $E(Y \mid A=1) - E(Y \mid A=0)$ conflate the treatment effect with confounding. Patients receiving treatment often differ systematically from patients receiving control.

Standardization (the discrete G-formula) calculates what the outcome would be if *everyone* received treatment $a$, adjusting for observed confounders $X$.

---

## 2. The Two Steps

### Step 1: Stratification (Conditioning)
Split the dataset into homogeneous subgroups (strata) defined by the confounders $X$.
Compute the expected outcome within each stratum for treatment $a$:
$$E(Y \mid A=a, X=x)$$

### Step 2: Marginalization (Standardization)
Average those stratum-specific outcomes across the entire target population, weighted by the population distribution of $X$:
$$E(Y^a) = \sum_{x} E(Y \mid A=a, X=x) P(X=x)$$

The Average Treatment Effect (ATE) is:
$$ATE = E(Y^1) - E(Y^0) = \sum_{x} \Big( E(Y \mid A=1, X=x) - E(Y \mid A=0, X=x) \Big) P(X=x)$$

---

## 3. Assumptions Required
If any of these fail, standardization does not yield a causal effect:

1. **Exchangeability (Conditional Ignorability):**
   $$Y^0, Y^1 \perp A \mid X$$
   No unmeasured confounders within each stratum $X=x$.

2. **Positivity:**
   $$0 < P(A=a \mid X=x) < 1 \quad \text{for all } x \text{ with } P(X=x) > 0$$
   Every stratum must contain both treated and untreated units. If a stratum has zero treated units, $E(Y \mid A=1, X=x)$ is undefined.

3. **Consistency:**
   $$Y = A \cdot Y^1 + (1-A) \cdot Y^0$$
   An individual's observed outcome matches their potential outcome under the treatment received. No hidden versions of treatment.

4. **SUTVA (No Interference):**
   One unit's treatment status does not alter another unit's potential outcomes.

---

## 4. Why It Breaks: The Curse of Dimensionality
- With 1 or 2 discrete confounders (e.g., prior medication: yes/no, age group: young/old), strata are dense.
- With 10 covariates or continuous variables, the number of strata explodes. Most strata end up with zero observations or units of only one treatment status.
- This creates empirical positivity violations (empty cells), forcing us to move to modeling methods (propensity score matching, IPTW, parametric G-computation).

---

## 5. Python Implementation

```python
import numpy as np
import pandas as pd

# Example: Diabetes drug study with confounder X (prior medication)
np.random.seed(42)
n = 1000

# Confounder: 1 = prior medication, 0 = treatment naive
x = np.random.binomial(1, p=0.4, size=n)

# Treatment: sicker patients (x=1) more likely to get new drug (a=1)
prob_a = np.where(x == 1, 0.75, 0.25)
a = np.random.binomial(1, p=prob_a)

# True causal effect of a is +2.0, x adds +5.0
y = 10.0 + 2.0 * a + 5.0 * x + np.random.normal(0, 1, size=n)

df = pd.DataFrame({"X": x, "A": a, "Y": y})

# --- Method 1: Discrete Stratification and Standardization ---
# Population stratum weights P(X=x)
weights = df["X"].value_counts(normalize=True).to_dict()

# Stratum-specific means E(Y | A=a, X=x)
strata_means = df.groupby(["X", "A"])["Y"].mean().unstack()

# Standardized means: sum_x E(Y | A=a, X=x) * P(X=x)
ey1 = sum(strata_means.loc[x_val, 1] * weights[x_val] for x_val in weights)
ey0 = sum(strata_means.loc[x_val, 0] * weights[x_val] for x_val in weights)
ate_standardized = ey1 - ey0

# Unadjusted difference (naive)
ate_naive = df[df["A"] == 1]["Y"].mean() - df[df["A"] == 0]["Y"].mean()

print(f"Naive ATE (biased):       {ate_naive:.3f}")
print(f"Standardized ATE (causal): {ate_standardized:.3f}")
print(f"True Causal Effect:       2.000")
```
