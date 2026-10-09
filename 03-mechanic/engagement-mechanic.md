# The Mechanic · FinWise

> Engagement Strategy · Building a Valuable Return Loop

## Chosen gamification mechanic: Cash Plan Freshness

**Cash Plan Freshness** is a weekly status mechanism that makes the user’s forecast freshness visible. After a user has reviewed a personalized cash-flow action, FinWise marks their 30-day cash plan as **Current**. When a material change affects the forecast—for example, a projected cash-buffer breach, a material invoice change, or a meaningful change in upcoming outgoings—the status becomes **Needs review** and shows one recommended action. Reviewing that action restores the Current status for the week.

Cash Plan Freshness mockup
<img width="647" height="427" alt="image" src="https://github.com/user-attachments/assets/9f82eb06-c883-4ea8-998b-78e6e7490684" />

### What the user sees and when

| Moment | Experience |
| --- | --- |
| After first Aha | A simple status: **“Your cash plan is current.”** The user sees the forecast horizon and the action they just reviewed. |
| Weekly operating cycle | A quiet in-product reminder appears only if the plan has new, material information to review. |
| Material forecast change | The status changes to **“Your cash plan needs review”** and names the single relevant action, such as reviewing invoices that affect the projected buffer. |
| After review | FinWise confirms that the plan is current again and shows what changed in the forecast. |

### Intrinsic motivation and cadence

The primary motivation is **loss aversion**, grounded in a real loss: allowing a cash plan to become stale can mean discovering a buffer risk or delayed invoice too late. This is deliberately **not a streak**. Small-business cash management has a natural **weekly** cadence, so FinWise earns a return when the forecast has changed materially instead of demanding a daily check-in or penalizing a missed app open.

### Rationale

Cash Plan Freshness reinforces the same behavior that defines FinWise’s candidate Aha moment—reviewing a personalized cash-flow recommendation—rather than rewarding arbitrary clicks, points, or time in the product. The mechanism gives users a practical reason to return each week: keep their financial plan current when conditions change. It supports Module 1 and Module 2 by creating more repeat occasions for users to experience personalized value; it does not replace the post-Aha paid-plan experiment. If FinWise’s recommendations are generic, inaccurate, or do not lead to useful decisions, the status alone will not prevent churn, so each review must show the specific forecast change and the outcome of the recommended action.

---

## Engagement Weighted Scorecard

The original scorecard used average session duration as a depth proxy. For this mechanic, that is too indirect: longer sessions can reflect friction rather than value. This mechanic-specific scorecard tracks the user behaviors that Cash Plan Freshness is designed to move.

| Dimension | Mechanic-specific metric | Weight | Baseline proxy from available data | Current score | Weighted |
| --- | --- | ---: | --- | ---: | ---: |
| **Depth** | Share of eligible users who review a personalized cash-flow action after a material forecast change. | 50% | Financial-modeling usage: **36.73%** (until action-review tracking exists). | 3 | 1.50 |
| **Breadth** | Share of users completing the core workflow: account import → first financial model → recommended-action review. | 30% | Average of data import (39.04%) and modeling (36.73%): **37.89%**. This is a proxy, not a user-level completion rate. | 3 | 0.90 |
| **Frequency** | Average weekly cash-plan reviews per eligible user. | 20% | Sessions per user: **6.62** (until weekly review events are tracked). | 7 | 1.40 |
| **Cash Plan Engagement KPI** | `0.50 × depth score + 0.30 × breadth score + 0.20 × frequency score` | **100%** |  |  | **3.80 / 10** |

**Baseline interpretation: Needs improvement.** The strongest observable signal is return frequency, but fewer than 40% of users reach either core workflow action. The mechanic should improve meaningful action completion and repeat review—not simply create longer sessions or more notification opens.

### What each metric must move

- **Depth:** More eligible users should review the action tied to a material forecast change. This is the direct repeat of `personalized_cashflow_action_reviewed`.
- **Breadth:** More users should progress through the complete value chain: account data → financial model → recommended action. This protects against “engagement” that never reaches core product value.
- **Frequency:** More eligible users should return on a weekly cadence when their cash plan changes materially, rather than being prompted to open FinWise every day.

### Measurement plan

| Item | Definition |
| --- | --- |
| Unit of analysis | Eligible trial and paid users with a connected primary business account. |
| Treatment | Cash Plan Freshness status plus a single material-change review prompt. |
| Control | Existing forecast experience without the Freshness status or weekly material-change prompt. |
| Evaluation window | Four weeks after the first personalized cash-flow action review. |
| Primary engagement readout | Change in the Cash Plan Engagement KPI versus control. |
| Product outcomes | Trial-to-paid conversion for trial users; four-week return rate and later retention for paid users. |
| Guardrails | Notification opt-outs, dismissed prompts, bank-connection failure, and evidence that recommendations were not material or useful. |

### Instrumentation required

```text
material_forecast_change_detected
cash_plan_freshness_status_viewed
cash_plan_review_started
personalized_cashflow_action_reviewed
cash_plan_action_completed_or_dismissed
cash_plan_freshness_restored
```

Replace the baseline proxies with these event-level cohorts once instrumentation is live. In particular, measure the intersection of account import, modeling, and action review at the user level; do not infer it from separate aggregate feature-adoption rates.

---

## Design stress test

| Principle | How Cash Plan Freshness meets it |
| --- | --- |
| Meaningful behavior | It rewards reviewing a personalized cash-flow action, the candidate behavior that predicts retention. |
| Natural cadence | It appears weekly or when a material forecast change occurs, not daily by default. |
| Real motivation | The plan becoming stale represents a genuine loss of financial visibility, not a fake lost streak. |
| Earned return | A prompt is tied to a concrete forecast change and one relevant action. |
| Core value | The mechanism brings users back to an updated financial model and recommended action, not to points or badges. |
