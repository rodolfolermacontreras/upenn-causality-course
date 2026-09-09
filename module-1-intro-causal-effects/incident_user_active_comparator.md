# Incident User and Active Comparator Study Designs

## 1. The Core Problem in Observational Studies
When evaluating real-world treatments using observational data (like electronic health records or claims), naive comparisons suffer from two major biases:
1. **Prevalent User Bias:** Comparing ongoing users of a treatment against non-users.
2. **Confounding by Indication:** Comparing treated patients against untreated patients who were never considered for treatment because they were either too healthy or too sick.

---

## 2. Incident User Design (New User Cohort)

### The Concept
Instead of taking a cross-sectional snapshot of anyone currently on a treatment, restrict the study exclusively to **new initiators** (incident users).

### How It Works
1. Define a "washout period" (e.g., 6 to 12 months with no record of using the treatment).
2. Set the baseline index date ($T_0$) to the exact day the patient starts the treatment.
3. Measure all baseline covariates ($X$) strictly *before* or *at* $T_0$.
4. Follow patients forward from $T_0$ to observe outcomes.

### What Biases It Prevents
* **Depletion of susceptibles:** Prevalent users are survivors who tolerated the drug without early adverse events. Incident design captures early side effects.
* **Selection bias from dropouts:** Patients who stopped the treatment because it failed or caused side effects are missed in prevalent samples.
* **Immortal time bias:** Aligning time zero ($T_0$) for all patients ensures no unexposed person-time is mistakenly misclassified.
* **Covariate distortion:** Long-term treatment alters health markers (like blood pressure or cholesterol). Measuring covariates before initiation ensures they are true confounders, not mediators on the causal path.

---

## 3. Active Comparator Design

### The Concept
Instead of comparing treatment ($A=1$) to doing nothing or standard care ($A=0$), compare the treatment of interest to an **alternative active treatment** used for the same clinical indication.

### Example
* **Naive comparison:** New diabetes drug vs no drug. (Severely confounded: untreated patients might have mild diet-controlled diabetes, while treated patients have severe disease).
* **Active comparator:** New diabetes drug (Drug A) vs Established diabetes drug (Drug B) among patients failing first-line metformin.

### Why It Works
* **Mitigates confounding by indication:** Both groups reached the threshold where a physician decided active intervention was necessary.
* **Controls for health-seeking behavior:** Both groups regularly visit clinics, fill prescriptions, and adhere to medical care (avoids healthy-user bias).
* **Improves positivity:** Because both drugs are realistic clinical alternatives for the same patient profile, propensity scores have strong overlap across covariate strata.

---

## 4. The Gold Standard: New-User Active Comparator Design
Combining both approaches:
1. Identify patients who are new initiators of Treatment A.
2. Identify patients who are new initiators of Treatment B for the same condition.
3. Align follow-up from initiation day $T_0$.
4. Measure baseline confounders before $T_0$.

This closely mimics a randomized active-controlled trial using observational data (target trial emulation).
