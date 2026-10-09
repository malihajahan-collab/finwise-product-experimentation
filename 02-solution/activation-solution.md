# FinWise — Activation Strategy & Aha Moment

> **Activation principle:** Get users to personalized financial value before asking them to pay.

---

## Strategy Context

FinWise is a financial-management SaaS product for small businesses using a product-led reverse-trial model.

Across 13 months, only **128 of 6,424 trials converted**, resulting in a **1.99% trial-to-paid conversion rate**.

The growth strategy therefore focuses on a specific question:

> **What is the shortest credible path from sign-up to a moment where the user clearly experiences personalized value?**

The monetization hypothesis is that presenting a contextual paid-plan continuation prompt **after that value moment** can improve trial-to-paid conversion from **1.99% to at least 2.4%**.

The activation strategy is designed around reaching that moment with as little setup friction as possible.

---

## Candidate Aha Moment

> **A trial user reviews a recommended cash-flow action from a first financial model generated using their connected business account.**

This is the first point where FinWise transforms raw financial data into a decision the user can act on.

Connecting an account is setup.

Viewing a forecast is insight.

Reviewing a personalized recommended action is the candidate moment where value becomes tangible.

**Candidate activation event:** `personalized_cashflow_action_reviewed`

This remains a hypothesis rather than a proven causal event. FinWise should later compare conversion and retention behavior between users who reach this event and comparable users who do not.

---

## Activation Journey

The onboarding path contains **three steps to Aha**.

The paid-plan prompt is deliberately separated from activation and shown only after the user has experienced personalized value.

| Stage | User Job | Primary Action | Friction Removed | Event / Output |
| --- | --- | --- | --- | --- |
| **1. Confirm first goal** | Establish the financial question FinWise should answer first. | Confirm **“See my upcoming cash flow.”** | Pre-fill the goal when intent is already known from the acquisition source. Avoid multi-question onboarding. | First goal confirmed |
| **2. Connect primary account** | Provide the minimum real data needed for the first model. | Select **“Connect account.”** | Ask for one primary business account only. Defer categorization, additional accounts, company details, and team setup. | Financial data imported |
| **3. Review personalized cash-flow action** | Understand an upcoming cash-flow risk and what to do next. | Select **“Review recommended action.”** | Focus the first result on one relevant forecast and one concrete action. | `personalized_cashflow_action_reviewed` |
| **Post-Aha monetization** | Decide whether continuing value is worth paying for. | Select **“Continue to paid plan.”** | Show the offer only after value is demonstrated. Keep **“Not now — continue my trial”** visible. | Monetization treatment / paid conversion |

---

## What I Deliberately Removed Before Aha

To reduce time-to-value, I would not ask the user to complete these tasks before receiving their first personalized insight:

- Product tours or feature exploration
- Additional account connections
- Team invitations
- Manual transaction categorization
- Notification preferences
- Company-profile configuration
- Pricing comparisons
- Upgrade prompts before personalized value is delivered

> **PM judgment:** Every additional onboarding step must earn its place by improving the first value experience. If it does not, defer it.

---

## Prototype Mapping

| Prototype View | Role in the Activation Strategy |
| --- | --- |
| **“Let’s get your cash flow clear.”** | Confirms the user's initial cash-flow goal. Acquisition intent can pre-fill this step when known. |
| **“Connect your primary business account.”** | Collects the minimum data required to generate a useful forecast. |
| **“Here’s your first cash-flow forecast.”** | Shows a 30-day forecast, identifies the projected buffer shortfall, and presents one recommended action. |
| **“Keep your cash flow working for you.”** | Introduces the paid-plan continuation prompt after the user has experienced the candidate Aha moment. |

---

## Designing the Aha Moment

The Aha is engineered on the personalized forecast experience—not on account connection or dashboard arrival.

```mermaid
flowchart LR
    A["Cash-flow goal confirmed"] --> B["Primary account connected"]
    B --> C["30-day financial model generated"]
    C --> D["Forecast reveals cash-flow risk"]
    D --> E["User reviews recommended action"]
    E --> F["Contextual paid-plan prompt"]

    style E fill:#d7f8eb,stroke:#0d6b4e,color:#101828
