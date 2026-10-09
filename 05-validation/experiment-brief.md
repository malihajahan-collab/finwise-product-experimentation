# FinWise — Monetization Experiment & Decision Framework

> **Decision question:** Does introducing the paid relationship immediately after personalized value create enough incremental conversion to justify changing the product?

---

## Business Goal vs. Experiment Design

FinWise’s commercial ambition is to improve overall trial-to-paid conversion from:

**1.99% → 2.4%**

That represents a **+0.41 percentage-point absolute lift**, or roughly **20% relative improvement**.

However, a business target is not automatically a statistically feasible experiment threshold.

Using a conventional two-sided test with:

- **α = 0.05**
- **80% statistical power**
- baseline conversion = **1.99%**
- target conversion = **2.4%**

detecting that difference would require approximately:

**~20,000 eligible users per variant**  
**~40,000 eligible users total**

FinWise observed only **6,424 total trials across 13 months**, and the experiment would randomize only the subset who reach the candidate Aha moment.

Therefore:

> **2.4% remains the commercial ambition, but it should not be treated as the experiment’s MDE until eligible traffic proves the test can detect a lift of that size.**

---

## PM Decision

Before launching the experiment, I would separate three decisions:

### 1. Business Target
What improvement would materially matter to FinWise?

**Current ambition: 1.99% → 2.4% overall trial-to-paid conversion.**

### 2. Minimum Detectable Effect
What effect can the experiment realistically detect given:

- eligible user volume
- baseline conversion among Aha-qualified users
- test duration
- desired power
- acceptable false-positive risk

**MDE: TBD from actual eligible-user traffic before launch.**

### 3. Product Decision Threshold
What evidence would justify shipping?

This should combine:

- effect magnitude
- confidence interval
- guardrail performance
- commercial relevance

rather than relying only on whether a p-value crosses 0.05.

---

## Hypothesis

> **If FinWise shows eligible reverse-trial users a contextual paid-plan continuation prompt immediately after they review a personalized cash-flow action, then more users will convert to paid because the offer follows demonstrated financial value rather than interrupting setup.**

---

## Experiment Design

| Element | Decision |
|---|---|
| **Experiment** | Post-Aha Paid-Plan Continuation Prompt |
| **Method** | 50/50 user-level randomized A/B test |
| **Randomization point** | Immediately after `personalized_cashflow_action_reviewed` |
| **Population** | New reverse-trial users reaching the candidate Aha event |
| **Control** | Existing post-Aha trial experience |
| **Treatment** | Contextual paid-plan continuation screen |
| **Primary metric** | Trial-to-paid conversion among randomized eligible users |
| **Commercial baseline** | **1.99% overall trial-to-paid conversion** |
| **Commercial ambition** | Move overall conversion toward **2.4%** |
| **Experiment MDE** | **Pre-commit after measuring eligible traffic and eligible-user conversion baseline** |
| **Guardrail** | 7-day cash-plan review must not decline by more than **5% relative to control** |
| **Readout** | After enrolled users complete the reverse-trial period and the planned sample is reached |

---

## Why an A/B Test

The intervention is:

- discrete
- reversible
- delivered at a specific user-level moment
- measurable against a concurrent control

A standard user-level A/B test therefore provides the cleanest causal comparison.

More complex approaches are unnecessary for the first test:

- a multi-armed bandit adds little value because there is only one treatment
- geo-testing is poorly matched to an in-product user-level intervention
- switchback testing is unnecessary because treatment does not need to alternate over time
- a long-term holdout may become useful later for retention analysis

---

## Eligibility

A user enters the experiment only after completing:

```text
financial_data_imported
        ↓
first_financial_model_output_viewed
        ↓
personalized_cashflow_action_reviewed
        ↓
randomization
```

Exclude:

- existing paid users
- users who have already seen the treatment
- users who have not completed the candidate Aha event

This isolates the question:

> **Does the monetization prompt work better after demonstrated value?**

It does not mix the experiment with the separate question of whether users reached value in the first place.

---

## Treatment Experience

### Control

The user reviews the first personalized cash-flow recommendation and continues through the existing reverse-trial experience.

### Treatment

Immediately after `personalized_cashflow_action_reviewed`, the user sees one concise continuation screen that:

- recaps the financial insight just reviewed
- reinforces the recommended action
- explains that paid access keeps the cash plan current
- offers **“Continue to paid plan”**
- retains **“Not now — continue my trial”** as a clear secondary option

The treatment changes the **monetization moment**, not the activation journey before it.

---

## Measurement Plan

| Stage | Event / Metric | Purpose |
|---|---|---|
| **Eligibility** | `financial_data_imported` → `first_financial_model_output_viewed` → `personalized_cashflow_action_reviewed` | Confirms the user experienced the candidate Aha moment |
| **Exposure** | `post_aha_paid_prompt_shown` | Confirms treatment delivery |
| **Primary outcome** | `paid_plan_started` | Measures paid conversion |
| **Guardrail** | 7-day `cash_plan_review_started` | Detects damage to continued engagement |
| **Diagnostic** | Prompt dismissal / continuation behavior | Helps explain the result without replacing the primary metric |

---

## Power & Sample-Size Planning

The original business target implies:

**1.99% → 2.4%**

For a conventional two-sample proportion test at approximately:

- **95% confidence**
- **80% power**

the required sample is approximately:

**20,000 users per arm**

That is not feasible using the currently observed trial volume within a short product-development cycle.

### Pre-Launch Requirement

Before starting the experiment:

1. Measure the number of users reaching `personalized_cashflow_action_reviewed`.
2. Measure paid conversion within that eligible population.
3. Estimate weekly eligible traffic.
4. Calculate the smallest effect the available sample can detect in a practical test window.
5. Decide whether that detectable effect would be commercially meaningful.

Only then should FinWise lock:

**MDE + sample requirement + test duration + decision threshold**

---

## What I Would Not Do

I would not:

- call **2.4%** the experiment MDE simply because it is the business target
- run a two-week test without checking sample feasibility
- stop early when conversion looks positive
- extend the test indefinitely until significance appears
- redefine success after seeing results
- use prompt clicks as a substitute for paid conversion
- claim that an underpowered null result proves the idea does not work

---

## Readout Rules

- Randomize once per eligible user.
- Maintain assignment throughout the experiment.
- Analyze users by assigned treatment.
- Wait for the full reverse-trial outcome window.
- Use the pre-committed sample requirement.
- Report the estimated treatment effect and confidence interval.
- Report guardrails alongside the primary result.
- Report the share of all trials reaching Aha separately from the treatment effect.
- Do not change the primary metric or success criteria mid-test.

---

## Decision Framework

| Result | Decision |
|---|---|
| **Meaningful positive effect + sufficient evidence + guardrail healthy** | **SHIP** |
| **Positive effect but uncertainty remains too high** | **CONTINUE / RE-TEST** if the economics justify more evidence |
| **Positive conversion effect but engagement guardrail deteriorates materially** | **INVESTIGATE** |
| **Well-powered result shows little or no commercially meaningful effect** | **DO NOT EXPAND** |
| **Test is underpowered or traffic is insufficient** | **INCONCLUSIVE — do not claim win or failure** |

---

## If Traffic Is Too Low

If the eligible population cannot support a statistically credible test within a reasonable period, I would not force the experiment.

Instead, I would consider:

### Increase the Detectable Effect

Ask whether FinWise only wants to ship changes capable of producing a larger improvement.

A larger MDE requires fewer users.

### Improve Aha Reach First

If too few users become eligible, activation itself may be the higher-leverage problem.

Increase the share reaching:

`personalized_cashflow_action_reviewed`

before trying to optimize post-Aha monetization.

### Use the Test as Directional Evidence

If leadership chooses to run a smaller pilot, label the result appropriately:

> **Directional learning, not statistically conclusive causal evidence.**

This can support qualitative learning and instrumentation validation without overstating certainty.

---

## Connection to the Product Strategy

| Strategy Layer | Role |
|---|---|
| **Growth Bet** | Establishes trial-to-paid conversion as the commercial problem |
| **Activation Strategy** | Defines the candidate Aha moment and experiment entry point |
| **Engagement Strategy** | Provides the cash-plan-review guardrail |
| **Measurement Strategy** | Separates activity, value realization, and business outcomes |
| **Experimentation** | Tests the causal impact of changing the monetization moment |
| **Monetization Strategy** | Defines Cash Plan Continuity as the ongoing paid value |

---

## PM Judgment

The original strategy connected the right product behaviors:

**Aha → paid prompt → conversion**

The critical improvement is recognizing that:

> **A commercially desirable lift and a statistically detectable lift are not automatically the same thing.**

The business can still aspire to move conversion from **1.99% to 2.4%**.

But the experiment should only claim it can detect that improvement if the available eligible population supports the required sample.

---

## PM Takeaway

> **A strong experiment does not begin with “How long should we run this?” It begins with “What effect matters, what effect can we detect, and will the answer actually change the product decision?”**

For FinWise, experimentation should protect against two errors:

**shipping on weak evidence** and **rejecting a useful idea because an underpowered test failed to reach significance**.
