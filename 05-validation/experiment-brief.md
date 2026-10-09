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
