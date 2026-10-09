# FinWise — Engagement Strategy & Cash Plan Freshness

> **Engagement principle:** Give users a reason to return when their financial situation changes—not simply because the product wants another app open.

---

## The Engagement Problem

FinWise needs repeat usage after the first personalized cash-flow insight.

But increasing session frequency alone would not necessarily create value.

A useful engagement mechanism should bring the user back when there is a meaningful financial decision to review.

That led to **Cash Plan Freshness**.

---

## Cash Plan Freshness

Cash Plan Freshness is a status mechanism that tells users whether their 30-day financial plan still reflects current conditions.

After a user reviews a personalized cash-flow recommendation, FinWise marks the plan:

**Current**

When a material change affects the forecast—for example:

- a projected cash-buffer breach
- a meaningful invoice change
- a significant change in upcoming outgoings

the status changes to:

**Needs Review**

FinWise then surfaces one relevant recommended action.

Once the user reviews that action, the plan returns to:

**Current**

---

## Experience

<img width="647" height="427" alt="FinWise Cash Plan Freshness concept" src="https://github.com/user-attachments/assets/9f82eb06-c883-4ea8-998b-78e6e7490684" />

| Moment | User Experience |
| --- | --- |
| **After first Aha** | “Your cash plan is current.” The user sees the forecast horizon and the action just reviewed. |
| **Normal weekly cycle** | No unnecessary prompt if nothing material has changed. |
| **Material forecast change** | Status becomes **“Needs Review”** and identifies one relevant action. |
| **After action review** | FinWise confirms the plan is current again and shows what changed. |

---

## Why This Mechanic

The mechanism reinforces the same behavior underlying the candidate Aha moment:

> **Reviewing a personalized financial recommendation when it matters.**

It does not reward:

- arbitrary clicks
- daily logins
- points
- badges
- artificial streaks
- time spent in the product

Instead, it gives the user a practical reason to return:

**Keep my financial decisions aligned with changing cash-flow conditions.**

---

## Natural Cadence, Not Artificial Frequency

Small-business cash management has a natural operating rhythm.

FinWise should therefore earn engagement when:

**new information changes the financial plan**

rather than demanding daily interaction.

The primary behavioral motivation is grounded in a real risk: an outdated plan can allow a cash-buffer problem or delayed invoice to go unnoticed.

This is a more defensible use of loss aversion than creating an artificial streak the user is afraid to lose.

> **PM judgment:** Engagement should follow the cadence of the customer's problem, not the cadence of the product team's notification calendar.

---

## Relationship to the Growth Strategy

Cash Plan Freshness extends the value demonstrated during activation.

**First personalized action**  
↓  
**User understands FinWise's value**  
↓  
**Cash conditions change**  
↓  
**FinWise identifies a new material action**  
↓  
**User returns to review it**  
↓  
**The cash plan becomes current again**

This creates repeated opportunities for FinWise to demonstrate useful personalized value.

It supports the monetization strategy but does not replace the post-Aha paid-plan experiment.

If the recommendations are generic, inaccurate, or irrelevant, the status mechanism itself will not create retention.

The underlying recommendation must remain useful.

---

## Engagement Measurement

The original available metrics included session duration and sessions per user.

I would not use either as the primary definition of engagement.

Longer sessions could indicate value—or friction.

The measurement model therefore focuses on meaningful financial behaviors.

| Dimension | Preferred Metric | Weight | Current Data Proxy | Proxy Score | Weighted |
| --- | --- | ---: | --- | ---: | ---: |
| **Depth** | Eligible users reviewing a personalized cash-flow action after a material forecast change | 50% | Financial-modeling usage: **36.73%** | 3 | 1.50 |
| **Breadth** | Users completing account import → model → recommended-action review | 30% | Average of import **39.04%** and modeling **36.73%** = **37.89%** | 3 | 0.90 |
| **Frequency** | Weekly cash-plan reviews per eligible user | 20% | Sessions per user: **6.62** | 7 | 1.40 |
| **Cash Plan Engagement KPI** | `0.50 × depth + 0.30 × breadth + 0.20 × frequency` | **100%** | Proxy-based until event instrumentation exists |  | **3.80 / 10** |

### Interpretation

The current score is **directional only** because the available data uses aggregate feature metrics as proxies.

It should not be treated as evidence that 37.89% of users actually complete the full workflow.

The strongest observable signal is return frequency, while fewer than 40% of users use either of the current core feature proxies.

Once event-level instrumentation exists, the proxy score should be replaced with actual user-level cohorts.

---

## Experiment Design

| Element | Decision |
| --- | --- |
| **Population** | Trial and paid users with a connected primary business account |
| **Control** | Existing forecast experience |
| **Treatment** | Cash Plan Freshness status + one material-change review prompt |
| **Evaluation window** | Four weeks after first personalized action review |
| **Primary engagement readout** | Change in meaningful cash-plan review behavior versus control |
| **Trial-user outcome** | Trial-to-paid conversion |
| **Paid-user outcome** | Four-week return rate and longer-term retention |
| **Guardrails** | Notification opt-outs, dismissed prompts, connection failures, and low-quality / non-material recommendations |

---

## Required Instrumentation

```text
material_forecast_change_detected
cash_plan_freshness_status_viewed
cash_plan_review_started
personalized_cashflow_action_reviewed
cash_plan_action_completed_or_dismissed
cash_plan_freshness_restored
