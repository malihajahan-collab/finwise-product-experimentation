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

**[View Strategy Pitch →](https://malihajahan-collab.github.io/FinWise-analytics-Experimentation/Pitch.html)**  
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
