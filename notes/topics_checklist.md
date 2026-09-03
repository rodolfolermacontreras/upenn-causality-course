# Topics Checklist: A Crash Course in Causality

Check items off as I can explain them **without notes**. That is the bar, not "watched the video."

---

## Module 1: Welcome and Introduction to Causal Effects

- [ ] Define a causal effect using potential outcomes `Y(1)` and `Y(0)`
- [ ] Explain the fundamental problem of causal inference (we never see both outcomes)
- [ ] Distinguish **setting** a variable from **conditioning** on it
- [ ] Define ATE, ATT, and ATU, and say when each is the right target
- [ ] State SUTVA and give an example of when it is violated
- [ ] State the ignorability / no unmeasured confounding assumption
- [ ] State the positivity assumption and give an example of a violation
- [ ] State consistency and explain why it is not trivial

## Module 2: Confounding and Directed Acyclic Graphs (DAGs)

- [ ] Draw a DAG for a real problem from my own work
- [ ] Identify a **confounder** and explain why controlling for it is required
- [ ] Identify a **collider** and explain why controlling for it creates bias
- [ ] Identify a **mediator** and explain why controlling for it blocks the effect
- [ ] Apply the **backdoor criterion** to find a sufficient adjustment set
- [ ] Explain d-separation in plain language
- [ ] Explain why "control for everything you have" is wrong

## Module 3: Matching and Propensity Scores

- [ ] Define the propensity score and state its balancing property
- [ ] Fit a propensity score model (logistic regression) in R
- [ ] Perform nearest-neighbor matching
- [ ] Perform caliper matching and explain what the caliper protects against
- [ ] Assess balance using standardized mean differences
- [ ] Read a love plot / balance table and judge whether matching worked
- [ ] Assess overlap and explain what to do when it is poor
- [ ] Explain why matching on the propensity score is not the same as matching on covariates

## Module 4: Inverse Probability of Treatment Weighting (IPTW)

- [ ] Explain the intuition for IPTW (creating a pseudo-population)
- [ ] Compute IPTW weights from a propensity score
- [ ] Explain why extreme weights are a problem
- [ ] Apply stabilized weights and explain what they fix
- [ ] Apply weight truncation and state the bias/variance tradeoff
- [ ] Run a full IPTW analysis in R and interpret the estimate
- [ ] Explain a marginal structural model at a high level
- [ ] Compare IPTW to matching: when would I pick each

## Module 5: Instrumental Variables Methods

- [ ] Define an instrumental variable
- [ ] State the three IV assumptions: relevance, exclusion restriction, independence
- [ ] Explain the exclusion restriction in plain language and why it is untestable
- [ ] Diagnose a **weak instrument** and explain the consequence
- [ ] Run two-stage least squares in R
- [ ] Define compliers, always-takers, never-takers, and defiers
- [ ] Explain LATE / CACE and why it is not the ATE
- [ ] Apply IV to a randomized trial with non-compliance
- [ ] Apply IV to an observational study

---

## Cross-cutting outcomes

- [ ] Given a business question, choose an appropriate identification strategy and justify it
- [ ] Name the single assumption most likely to break my analysis, and how I would probe it
- [ ] Translate each method from R to Python (`DoWhy`, `EconML`, `statsmodels`)
- [ ] Write a one-page causal analysis I would be willing to defend in a design review
