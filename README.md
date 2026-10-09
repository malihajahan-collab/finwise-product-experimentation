# FinWise — Product-Led Growth & Experimentation

### Fintech · PLG · Activation · Experimentation · Monetization

> **Help users experience personalized financial value before asking them to pay.**

FinWise is a financial-management SaaS product for small businesses.

Across 13 months, **6,424 trials produced only 128 paid conversions — a 1.99% trial-to-paid rate**.

My product question was not simply:

**How do we increase conversion?**

It was:

> **What value must a trial user experience before FinWise has earned the right to ask for payment?**

---

## Executive Recommendation

Move the monetization moment **after the first personalized financial action**, then validate the change through a user-level A/B experiment.

| **1.99%** | **≥2.4%** | **6,424** | **128** |
|---:|---:|---:|---:|
| Trial-to-paid baseline | Conversion target | Trials observed | Paid conversions |

**[View Strategy Pitch →](https://malihajahan-collab.github.io/finwise-product-experimentation/Pitch.html)**  
**[Try Live Prototype →](https://finwise-onboarding-p-7fon.bolt.host)**

> **Product thesis:** Users should pay to continue receiving value they have already experienced—not to discover whether that value exists.

---

## The Growth Problem

Trial-to-paid conversion remained consistently low at approximately **2%**, while broad product usage did not clearly explain why some users converted and others did not.

One analytical signal was especially important:

**Financial-modeling usage showed only a weak correlation with paid conversion (`r = 0.26`).**

That challenged a simple assumption:

> **Feature usage ≠ experienced value.**

The strategy therefore moved away from optimizing generic activity and toward identifying the specific user event where FinWise becomes meaningfully useful.

---

## The Aha Moment

I defined the candidate value moment as:

> **The user connects a business account, sees a personalized 30-day cash-flow risk, and reviews one recommended action.**

The distinction matters:

**Account connection = setup**  
**Forecast viewing = insight**  
**Recommended action review = candidate Aha**

The activation event becomes:

```text
personalized_cashflow_action_reviewed
```

---

## The Product Decision

Instead of placing payment friction before users understand the product's value, I moved the monetization boundary:

**Setup → Personalized Insight → Recommended Action → Paid Offer**

### Trial Value

Users can:

- connect one primary business account
- receive a 30-day cash-flow forecast
- identify a projected financial risk
- review one personalized recommended action

### Paid Value

The subscription continues that value through **Cash Plan Continuity**:

- automatic forecast refreshes
- material cash-flow alerts
- recurring action reviews
- additional connected accounts
- ongoing personalized recommendations

---

## Activation Strategy

The onboarding experience is deliberately reduced to three steps:

**1. Confirm the financial goal**  
Identify the first question FinWise should answer.

**2. Connect one primary account**  
Collect only the minimum data required for the first useful forecast.

**3. Review one personalized action**  
Turn financial data into a decision the user can act on.

> **PM judgment:** Every onboarding step must earn its place by improving time-to-value.

---

## Experiment

### Hypothesis

If FinWise shows a contextual paid-plan continuation prompt immediately after a user reviews a personalized cash-flow action, more eligible users will convert to paid.

| Element | Decision |
|---|---|
| **Method** | 50/50 user-level randomized A/B test |
| **Randomization point** | After `personalized_cashflow_action_reviewed` |
| **Control** | Existing post-Aha trial experience |
| **Treatment** | Contextual paid-plan continuation prompt |
| **Primary metric** | Trial-to-paid conversion |
| **Overall baseline** | **1.99%** |
| **Target direction** | **≥2.4%** |
| **Decision threshold** | ~**20% relative lift** vs. control |
| **Guardrail** | 7-day cash-plan review cannot decline >5% vs. control |

> **Decision discipline:** Do not optimize for prompt clicks. Ship only if the treatment produces meaningful incremental paid conversion without damaging continued engagement.

---

## Engagement Strategy

### Cash Plan Freshness

FinWise should give users a reason to return **when their financial situation changes**, not simply because the product wants another session.

A cash plan remains:

**Current**

until new information materially changes the forecast.

It then becomes:

**Needs Review**

and FinWise surfaces one relevant recommended action.

After the action is reviewed, the plan returns to **Current**.

> **Engagement principle:** Follow the cadence of the customer's problem, not the cadence of the notification calendar.

---

## Measurement Strategy

The growth system is measured as one connected path:

**Account Import → Financial Model → Personalized Action → Paid Prompt → Paid Conversion → Recurring Review**

### Leading Signals

- Primary-account import within 24 hours
- Personalized cash-flow action review within 7 days

### Business Outcome

- Trial-to-paid conversion

### Critical Data Decision

The available dataset contained aggregate feature-usage rates but not the user-level sequence.

So rather than inferring a funnel from separate metrics, I defined the instrumentation required to measure the actual journey:

```text
trial_started
financial_data_imported
first_financial_model_output_viewed
personalized_cashflow_action_reviewed
post_aha_paid_prompt_shown
paid_plan_started
```

> **PM judgment:** The useful metric is not always the easiest metric already available in the dashboard.

---

## Monetization Strategy

Keep the existing **subscription + reverse-trial model**, but package the paid relationship around:

### Cash Plan Continuity

The commercial boundary becomes:

**First realized financial insight → Trial**

**Ongoing refreshed financial value → Paid**

I would validate this value boundary before testing:

- price increases
- discounts
- complex packaging
- broad freemium
- increased acquisition spend

The immediate problem is not yet proving how much FinWise can charge.

It is proving **what value users are willing to continue paying for**.

---

## Product Strategy Flow

```text
Qualified Intent
      ↓
Fast Activation
      ↓
Personalized Aha
      ↓
Monetization Experiment
      ↓
Recurring Cash-Plan Value
      ↓
Retention
```

The goal is not to optimize six independent tactics.

It is to build **one coherent growth system around the moment the user experiences value**.

---

## Case Study Artifacts

| Area | Product Decision | Artifact |
|---|---|---|
| **Growth Strategy** | Where should FinWise intervene first? | [`01-bet/growth-bet.md`](01-bet/growth-bet.md) |
| **Activation** | What is the shortest path to value? | [`02-solution/activation-solution.md`](02-solution/activation-solution.md) |
| **Engagement** | Why should users return? | [`03-mechanic/engagement-mechanic.md`](03-mechanic/engagement-mechanic.md) |
| **Measurement** | Which signals actually matter? | [`04-signals/data-signals.md`](04-signals/data-signals.md) |
| **Experimentation** | How do we test the monetization hypothesis? | [`05-validation/experiment-brief.md`](05-validation/experiment-brief.md) |
| **Monetization** | What should users pay to continue receiving? | [`06-model/pricing-model.md`](06-model/pricing-model.md) |

---

## PM Takeaway

> **Growth becomes more coherent when activation, engagement, experimentation, and monetization are organized around the same definition of user value.**

The most important product decision in this case was moving from:

**“Which features do converting users use?”**

to:

**“What happened that made the user understand why FinWise is worth paying for?”**
