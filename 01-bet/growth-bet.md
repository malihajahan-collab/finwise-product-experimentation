# FinWise — Growth Bet & PLG Strategy

> **Growth principle:** Improve monetization after users experience meaningful value before spending more to acquire additional traffic.

---

## Growth Problem

Across 13 months, FinWise generated **6,424 trials and 128 paid conversions**, producing a **1.99% trial-to-paid conversion rate**.

Monthly conversion remained consistently low, ranging from approximately **1.87% to 2.08%**.

That stability matters.

The problem does not appear to be one anomalous month. FinWise has a persistent challenge converting existing trial users into paying customers.

---

## Strategic Question

> **Where should FinWise intervene first to create the highest-leverage growth learning?**

There are multiple places the company could invest:

- acquire more visitors
- improve visit-to-trial conversion
- increase feature usage
- create referral loops
- improve trial-to-paid conversion

I prioritized **trial-to-paid conversion** because it sits closest to the commercial outcome and allows FinWise to test whether the existing trial experience creates enough value to justify payment.

---

## The Product Bet

> **If FinWise presents a contextual paid-plan continuation prompt after a trial user has experienced personalized financial value, more users will convert to paid.**

The strategy deliberately moves the monetization boundary **after the Aha moment**, rather than placing payment pressure during setup.

### Hypothesis

If eligible trial users:

1. import their financial data,
2. receive a personalized financial model, and
3. review a recommended cash-flow action,

then showing a contextual paid-plan continuation prompt at that moment should increase trial-to-paid conversion from:

**1.99% → at least 2.4%**

The underlying belief is that users are more likely to pay after FinWise has demonstrated a concrete financial outcome rather than after generic feature exposure.

---

## Why This Bet Comes First

Trial-to-paid is the first growth constraint I would test because the existing data suggests meaningful leverage.

At the observed trial volume:

**+1 percentage point in trial-to-paid conversion ≈ 64 additional paid customers**

By comparison, a one-percentage-point improvement in visit-to-trial conversion would produce approximately **19 additional paid customers** if the existing trial-to-paid rate remained unchanged.

This does not mean acquisition is unimportant.

It means the existing trial base provides a more immediate opportunity to test whether FinWise can convert demonstrated value into revenue.

---

## Strategic Pressure Test

| Question | Finding |
| --- | --- |
| **Is trial-to-paid weak because of one unusual month?** | No. Conversion remains between approximately **1.87% and 2.08%** across all 13 observed months. |
| **Where is the sharpest percentage drop?** | Trial → paid. Only **128 of 6,424 trials** converted. |
| **Should FinWise simply acquire more traffic first?** | Not yet. Increasing acquisition before improving monetization risks sending more users into the same low-converting experience. |
| **Is feature usage enough evidence of value?** | No. Product activity must be separated from a meaningful user-value event. |
| **What should be tested first?** | Whether monetization performs better when payment is introduced immediately after personalized value is demonstrated. |

---

## What I Would Not Prioritize First

I would defer:

- increasing paid-acquisition spend
- a broad homepage redesign
- referral mechanics
- collaboration-driven growth loops
- pricing discounts
- broad feature expansion

None of those directly answers the immediate strategic question:

> **Can FinWise convert more of the users it already brings into the product once they experience meaningful value?**

---

## Validation Plan

| Element | Decision |
| --- | --- |
| **Method** | Randomized A/B experiment |
| **Population** | Eligible reverse-trial users who reach the candidate Aha moment |
| **Control** | Existing post-Aha experience |
| **Treatment** | Contextual paid-plan continuation prompt |
| **Primary metric** | Trial-to-paid conversion |
| **Baseline** | **1.99%** |
| **Target** | **≥2.4%** |
| **Guardrail** | Core activation / engagement behavior must not materially deteriorate |
| **Readout** | After users complete the reverse-trial window |

> **Decision principle:** Do not optimize for prompt clicks. The treatment earns rollout only if more eligible users become paying customers without damaging the value experience that got them there.

---

## Acquisition Loop — Content-Driven Growth

The monetization bet addresses conversion, but FinWise also needs a scalable way to bring qualified users into the product.

The first acquisition loop I would develop is **content-driven growth**.

```mermaid
flowchart LR
    A["Small-business owner has a financial task"]
    B["Finds a FinWise template or guide"]
    C["Starts trial and applies it to their own data"]
    D["Experiences personalized financial value"]
    E["Converts and continues the workflow"]
    F["Creates a reusable data-free template"]
    G["FinWise publishes useful templates"]

    A --> B --> C --> D --> E --> F --> G --> A
