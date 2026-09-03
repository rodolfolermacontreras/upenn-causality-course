# A Crash Course in Causality: Inferring Causal Effects from Observational Data

**Institution:** University of Pennsylvania (Coursera)
**Instructor:** Jason A. Roy, Ph.D.
**Level:** Intermediate
**Format:** 5 modules, 16 assignments, ~2 weeks at 10 hours/week
**Language of instruction:** R
**Repo:** https://github.com/rodolfolermacontreras/upenn-causality-course
**Started:** September 2026

---

## Why I am taking this

"Correlation does not equal causation" is easy to say and hard to act on. This course
covers what actually equals causation: how causal effects are defined, what assumptions
are required, and which estimation strategies work when you cannot run an experiment.

Direct motivation: causal inference came up as a required skill in a Senior Data Scientist
role I am pursuing, and it is a genuine gap between my statistical foundations
(significance testing, effect size, distribution analysis) and the identification methods
used in product data science.

---

## Goals

1. Be able to state a causal question in the **potential outcomes framework** and name the
   assumptions required to answer it
2. Draw and read a **DAG**, and use it to decide what to control for and what not to
3. Know **when** to reach for matching, propensity scores, IPTW, or instrumental variables,
   and what breaks each one
4. Implement each method in R, and be able to translate the same approach to Python
5. Be able to defend a causal claim, including its assumptions and its failure modes

---

## Modules

### Module 1: Welcome and Introduction to Causal Effects
`module-1-intro-causal-effects/` | 8 videos, 3 assignments, ~4 hours

Defining causal effects using **potential outcomes**. The distinction between
**setting/manipulating** a variable and **conditioning** on it. Key causal identifying
assumptions introduced.

Core concepts: counterfactuals, `Y(1)` and `Y(0)`, ATE, ATT, SUTVA, ignorability, positivity.

### Module 2: Confounding and Directed Acyclic Graphs (DAGs)
`module-2-confounding-dags/` | 8 videos, 2 assignments, ~2 hours

Rules for reading causal graphs. How to identify whether a set of variables is
**sufficient to control for confounding**.

Core concepts: confounders, colliders, mediators, backdoor criterion, d-separation.

### Module 3: Matching and Propensity Scores
`module-3-matching-propensity-scores/` | 12 videos, 5 assignments, ~5 hours

Matching methods for estimating causal effects, both directly on confounders and on the
propensity score. Worked data analysis examples in R.

Core concepts: propensity score, nearest neighbor and caliper matching, balance
diagnostics (standardized mean differences), overlap.

### Module 4: Inverse Probability of Treatment Weighting (IPTW)
`module-4-iptw/` | 9 videos, 3 assignments, ~3 hours

IPTW as a method for estimating causal effects, illustrated with an IPTW analysis in R.

Core concepts: weighting instead of matching, stabilized weights, extreme weights and
truncation, marginal structural models.

### Module 5: Instrumental Variables Methods
`module-5-instrumental-variables/` | 9 videos, 3 assignments, ~4 hours

Causal effect estimation using instrumental variables, in both randomized trials with
non-compliance and in observational studies. IV analysis in R.

Core concepts: instrument validity, exclusion restriction, relevance, weak instruments,
two-stage least squares, LATE / complier average causal effect.

---

## Repo structure

```
upenn-causality/
├── README.md
├── module-1-intro-causal-effects/
├── module-2-confounding-dags/
├── module-3-matching-propensity-scores/
├── module-4-iptw/
├── module-5-instrumental-variables/
├── assignments/          # assignment work and solutions
└── notes/                # cross-module notes, summaries, cheat sheets
```

---

## Progress

| Module | Topic | Status | Notes |
|---|---|---|---|
| 1 | Intro to causal effects | Not started | |
| 2 | Confounding and DAGs | Not started | |
| 3 | Matching and propensity scores | Not started | |
| 4 | IPTW | Not started | |
| 5 | Instrumental variables | Not started | |

---

## Method selection cheat sheet (build this out as I go)

| Method | Use when | Key assumption | Breaks when |
|---|---|---|---|
| Randomization | You can assign treatment | Randomization worked | Not feasible or ethical |
| Matching | Observational, good covariates | Ignorability, overlap | Unobserved confounders |
| Propensity scores | Many covariates | Ignorability, overlap | Poor overlap, misspecified PS model |
| IPTW | Want to use full sample | Ignorability, positivity | Extreme weights |
| Instrumental variables | Unmeasured confounding | Relevance, exclusion restriction | Weak or invalid instrument |

---

## Notes to self

- The course is taught in **R**. Translate the key methods to Python as I go
  (`DoWhy`, `EconML`, `causalinference`, `statsmodels`) since Python is my working language.
- Reading alongside: *Causal Inference: The Mixtape* (Cunningham) for a second explanation
  of the same methods.
- The goal is not just to pass. It is to be able to **defend a causal claim under
  questioning**, including naming the assumption that would break it.
