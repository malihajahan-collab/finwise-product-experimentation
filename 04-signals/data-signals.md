# The Signals · FinWise

> Measurement Strategy · Signals That Matter

## Strategy context

FinWise’s experimentation strategy has one connected path:

**Content intent → account import → first financial model and cash-flow action review → contextual paid-plan prompt → paid conversion → recurring cash-plan review.**

Module 4 focuses the measurement system on the part of that path experiments can change quickly, while using paid conversion to prove the strategy created business value.

---

## Aim · Move · Prove

| Layer | Metric | Why |
| --- | --- | --- |
| **🎯 Aim · North Star** | **Number of new trial users who import financial data and reach their first financial-model output within seven days of sign-up.** | This is the complete early-value behavior: the user has supplied real data and received FinWise’s core financial insight. |
| **⚙ Move · Leading 1** | **Primary-account import rate within 24 hours of sign-up.** | Account import is the first required step toward the North Star and determines how many trial users can receive a personalized model or qualify for the Module 1 post-Aha experiment. |
| **⚙ Move · Leading 2** | **Personalized cash-flow action-review rate within seven days of account import.** | Reviewing the recommended action completes FinWise’s candidate Aha event and is the closest leading indicator of the value moment that should precede trial-to-paid conversion. |
| **✓ Prove · Lagging** | **Trial-to-paid conversion rate over the reverse-trial period.** | A sustained increase from the 1.99% baseline toward the 2.4% Module 1 target demonstrates that more users reaching value translates into commercial impact, not merely onboarding activity. |

### Metric definitions

| Metric | Numerator | Denominator | Time window |
| --- | --- | --- | --- |
| North Star | New trial users who complete both `financial_data_imported` and `first_financial_model_output_viewed`. | Report the count; also report the rate using all new trial users as denominator. | Within 7 days of trial start. |
| Leading 1 | New trial users who successfully connect or import one primary business account. | All new trial users. | Within 24 hours of trial start. |
| Leading 2 | Connected trial users who complete `personalized_cashflow_action_reviewed`. | Trial users who successfully imported a primary account. | Within 7 days of account import. |
| Lagging | Trial users who become paid. | All trial users assigned to the experiment at trial start. | Full reverse-trial period. |

---

## Signals in the available data

| Observed signal | What it means for this measurement plan |
| --- | --- |
| Trial-to-paid conversion averages **1.99%** and ranges narrowly from **1.87% to 2.08%** over 13 months. | Paid conversion is a persistent constraint and the right lagging measure for the Module 1 Revenue experiment. |
| Data-import usage averages **39.04%**; financial-modeling usage averages **36.73%**. | Fewer than half of users reach either observable prerequisite to FinWise’s candidate Aha behavior, making import and action review priority leading signals. |
| Sessions per user average **6.62**, while session duration averages **9.77 minutes**. | Return frequency exists, but time in product does not prove that a user reached core value; it should not replace behavior-based leading indicators. |

### Data limitation to fix

The current dataset contains aggregate import and modeling rates, not the user-level sequence. It cannot show how many users complete **both** actions or whether they subsequently convert. Instrument the event sequence below before drawing causal conclusions.

```text
trial_started
financial_data_imported
first_financial_model_output_viewed
personalized_cashflow_action_reviewed
post_aha_paid_prompt_shown
paid_plan_started
```

---

## Experiment priority

1. **Move Leading 1 first:** Test the lean, intent-aware onboarding flow that asks for one primary account and removes nonessential setup. Read account-import rate quickly.
2. **Move Leading 2 next:** Test whether the first forecast presents a clear enough, personalized action for connected users to review. This is the candidate Aha event.
3. **Prove with the lagging result:** Randomize trial users at assignment, show the Module 1 continuation prompt only after Aha in the treatment, and measure trial-to-paid conversion across the full assigned cohort.

This sequencing prevents FinWise from optimizing prompt clicks or session length before it has established that users reached the value event the prompt is meant to monetize.

---

## Readout cadence and guardrails

| Layer | Readout cadence | Guardrails |
| --- | --- | --- |
| Leading 1 | Daily during a live onboarding test. | Bank-connection failure and onboarding abandonment. |
| Leading 2 | Daily and weekly cohort view. | Time to Aha and action dismissal without review. |
| Lagging | Once each assigned cohort completes the reverse-trial period. | No decline in first-model output, trial continuation, or later paid-user retention. |

---

## Trend diagnosis

| Metric | Pattern | Evidence from the 13-month trend |
| --- | --- | --- |
| **Trial-to-paid conversion rate** | **Ceiling / low plateau** | It stays in a narrow 1.87%–2.08% band for all 13 months. The series shows small fluctuations, not sustained improvement, so the current product experience appears to be taking trial users only as far as this conversion level. |
| **Financial modeling feature usage** | **Two cliffs with recovery, not one clean pattern** | Usage falls from 31.17% in October 2023 to 10.78% in November 2023, then recovers to 58.26% in April and 58.06% in September 2024 before falling again to 36.04% in October. The discrete drops require date- and cohort-level investigation. |
| **Get Started import feature usage** | **Range-bound / no clean cliff, leak, or ceiling** | Import usage remains between 30.51% and 45.42%, with a March 2024 low followed by a recovery to above 41% from August through October. It does not show a sustained directional pattern. |
| **Average session duration** | **Cliff with partial recovery** | Duration falls from 12.11 minutes in June 2024 to 6.99 in July and 5.14 in August, then recovers to 8.95 in October. Session length alone is not a quality signal, so this is a diagnostic flag rather than evidence of value loss. |
| **Average sessions per user** | **Cliff with recovery** | Sessions per user fall from 8 in December 2023 to 3 in January 2024, then recover to 8 by April and 9 by September and October. The January change is the precise point to investigate. |

## Correlation check: modeling usage vs. trial-to-paid conversion

Financial-modeling usage is the available proxy for the chosen leading indicator; the true indicator—personalized cash-flow action review—has not yet been instrumented. Across the 13 monthly observations, the Pearson correlation between modeling usage and trial-to-paid conversion is **r = 0.26**, a weak positive association. The visual does not support treating feature usage as a reliable driver of conversion: November 2023 has the lowest modeling usage (10.78%) but an above-average 2.05% trial-to-paid rate, while large modeling swings also occur with little conversion movement.

**Decision:** retain the Module 1 hypothesis as a causal experiment to test, but revise the measurement premise. Aggregate modeling usage is not enough to validate the path to paid conversion. FinWise should measure the user-level sequence—import → first model → `personalized_cashflow_action_reviewed` → paid-plan prompt → paid conversion—and evaluate the randomized prompt treatment against control.
