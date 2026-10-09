# FinWise — Monetization Experiment & Decision Framework

> **Decision question:** Does introducing payment immediately after personalized value increase conversion without damaging continued engagement?

---

## Hypothesis

> **If FinWise shows eligible reverse-trial users a contextual paid-plan continuation prompt immediately after they review a personalized cash-flow action, trial-to-paid conversion will increase because the offer follows demonstrated financial value rather than interrupting setup.**

---

## Experiment Design

| Element | Decision |
| --- | --- |
| **Experiment** | Post-Aha Paid-Plan Continuation Prompt |
| **Method** | 50/50 user-level randomized A/B test |
| **Randomization point** | Immediately after `personalized_cashflow_action_reviewed` |
| **Population** | New reverse-trial users reaching the candidate Aha event |
| **Control** | Existing trial experience without the contextual prompt at that moment |
| **Treatment** | Contextual paid-plan continuation screen |
| **Primary metric** | Trial-to-paid conversion among randomized eligible users |
| **Overall baseline** | **1.99%** |
| **Target direction** | Toward **2.4%** overall conversion |
| **Decision threshold** | Approximately **20% relative lift** versus concurrent control |
| **Guardrail** | 7-day cash-plan review cannot decline by more than **5% relative to control** |
| **Readout** | After enrolled users complete the reverse-trial period |

The 20% relative-lift threshold approximates the magnitude required to move the observed **1.99%** conversion baseline toward **2.4%**, assuming the eligibility mix remains comparable.

---

## Why an A/B Test

The product is changing one discrete, reversible experience:

**whether an eligible user sees the paid-plan continuation prompt immediately after the Aha event.**

A user-level A/B test provides the clearest causal comparison.

More complex methods are unnecessary for this decision:

- there is only one treatment, so a multi-armed bandit adds little value
- the intervention happens at the individual-user level, making geo or switchback testing poorly matched
- longer-term holdouts may be useful later for retention, but are not required to test the immediate conversion hypothesis

---

## Treatment Experience

### Control

The user reviews the first personalized cash-flow action and continues through the existing trial experience.

### Treatment

Immediately after `personalized_cashflow_action_reviewed`, the user sees a concise screen that:

- recaps the forecast just reviewed
- reinforces the recommended action
- explains that paid access keeps the cash plan current
- offers **“Continue to paid plan”**
- preserves **“Not now — continue my trial”** as a clear secondary option

The treatment changes the monetization moment—not the preceding activation experience.

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
