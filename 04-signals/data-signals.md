# FinWise — Measurement Strategy & Growth Signals

> **Measurement principle:** Separate product activity from evidence that users are actually reaching value.

---

## Measurement Context

The FinWise growth strategy follows one connected behavioral path:

**Content intent → account import → financial model → personalized action review → paid-plan prompt → paid conversion → recurring cash-plan review**

The measurement system therefore needs to answer three different questions:

**Are users reaching value?**  
**Can the team move the behaviors leading to value?**  
**Does reaching value translate into commercial impact?**

---

## Aim · Move · Prove

| Layer | Metric | Why It Matters |
| --- | --- | --- |
| **Aim** | New trial users who import financial data and reach their first financial-model output within 7 days | Shows whether users complete the minimum early-value journey |
| **Move 1** | Primary-account import rate within 24 hours | Measures whether users clear the first activation prerequisite |
| **Move 2** | Personalized cash-flow action-review rate within 7 days of import | Measures the candidate Aha behavior |
| **Prove** | Trial-to-paid conversion across the reverse-trial period | Tests whether more users reaching value translates into commercial impact |

---

## Metric Definitions

| Metric | Numerator | Denominator | Window |
| --- | --- | --- | --- |
| **Early-value completion** | New trials completing `financial_data_imported` + `first_financial_model_output_viewed` | All new trial users | Within 7 days |
| **Account import** | New trials successfully importing one primary account | All new trial users | Within 24 hours |
| **Action review** | Connected trial users completing `personalized_cashflow_action_reviewed` | Trials successfully importing a primary account | Within 7 days of import |
| **Paid conversion** | Trial users becoming paid | Relevant assigned trial cohort | Full reverse-trial period |

---

## What the Existing Data Shows

| Signal | Interpretation |
| --- | --- |
| Trial-to-paid averages **1.99%**, ranging from **1.87%–2.08%** | Conversion is persistently low rather than driven by one abnormal month |
| Data-import usage averages **39.04%** | Fewer than half of users use the observable import feature |
| Financial-modeling usage averages **36.73%** | Fewer than half use the observable modeling feature |
| Sessions per user average **6.62** | Users return, but return frequency alone does not prove value |
| Session duration averages **9.77 minutes** | Time in product should remain diagnostic rather than a success metric |

The current data suggests that **activity and commercial conversion are not moving together strongly enough to treat usage as proof of value**.

---

## Critical Data Limitation

The available dataset contains aggregate import and modeling rates.

It does **not** show the user-level sequence:

**import → model → action review → paid conversion**

That means we cannot currently determine how many users complete the full path or whether reaching a particular step predicts conversion.

Before making strong causal claims, FinWise should instrument:

```text
trial_started
financial_data_imported
first_financial_model_output_viewed
personalized_cashflow_action_reviewed
post_aha_paid_prompt_shown
paid_plan_started
