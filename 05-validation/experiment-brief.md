# The Validation · FinWise

> Experiment Design · Testing the Monetization Bet

## Experiment brief

### Step 1 · Choose the method

| Field | FinWise decision |
| --- | --- |
| **Method** | **Standard user-level A/B test** with a 50/50 random assignment at the moment a user completes `personalized_cashflow_action_reviewed`. |
| **Justification** | FinWise is testing one discrete, reversible experience change—the contextual paid-plan continuation prompt—on independent users at a precise event in their journey. A standard A/B test gives the cleanest causal comparison and enough speed for a conversion readout. A multi-armed bandit is unnecessary because there is one treatment rather than competing variants; a holdout is designed for longer-term effects; Geo-testing and switchback testing do not fit a user-level in-product prompt. |

### Step 2 · Define the experiment

| Field | FinWise decision |
| --- | --- |
| **Experiment name** | Post-Aha Paid-Plan Continuation Prompt Test |
| **Objective** | Increase paid conversion after trial users experience FinWise’s core value, connecting the Module 2 Aha moment to the Module 1 Revenue bet. |
| **Hypothesis** | If FinWise shows eligible reverse-trial users a contextual paid-plan continuation prompt immediately after they review a recommended cash-flow action, then trial-to-paid conversion will increase because the offer follows a personalized financial insight rather than interrupting setup. |
| **Primary metric** | Trial-to-paid conversion rate among users randomized after completing `personalized_cashflow_action_reviewed`, measured through the end of their reverse trial. |
| **Success threshold** | At least a **20% relative lift** versus concurrent control. This is the approximate magnitude required to move the 1.99% overall trial-to-paid baseline toward the 2.4% Module 1 target, if the Aha-eligibility mix remains stable. |
| **Guardrail metric** | The seven-day cash-plan review rate among all randomized eligible users must not be more than **5% lower** than the concurrent control rate. |

### Step 3 · Define what is being tested

| Field | FinWise decision |
| --- | --- |
| **Current experience** | A trial user can review their first personalized cash-flow action and continue using the trial without a contextual paid-plan continuation prompt at that moment. |
| **What is being tested** | Immediately after `personalized_cashflow_action_reviewed`, show one concise screen that recaps the current forecast and recommended action, explains that paid access keeps the plan current, and offers **“Continue to paid plan”** plus **“Not now — continue my trial.”** |
| **Target segment** | New reverse-trial users who successfully import a primary business account, view a first financial-model output, and complete `personalized_cashflow_action_reviewed`. Exclude existing paid users and users who have already been shown the prompt. |

### Step 4 · Predict the outcome

| Field | FinWise decision |
| --- | --- |
| **Predicted outcome** | Eligible users who see the contextual prompt will convert to paid at least 20% more often than eligible control users, without a greater than 5% relative reduction in seven-day cash-plan review. |
| **If successful** | Ship the prompt to all eligible users, retain a small long-term holdout to measure paid retention, then test one variable at a time—such as the value recap, timing, or plan framing. |
| **If unsuccessful** | Do not expand the prompt. Review action-level evidence: whether users reached Aha, whether the recommendation was material, prompt dismissal behavior, and same-week return. Then test the value experience or recommendation quality before testing more prompt copy. |

---

## Measurement plan

### Why the primary metric is conversion, not prompt clicks

Module 4’s leading indicators—account import and personalized action review—are prerequisites for this test and determine experiment eligibility. They should be monitored as diagnostics, but they occur before the prompt and cannot establish whether the prompt itself drives Revenue. FinWise should not ship the treatment because it produces clicks; it should ship only if randomized users convert to paid more often.

| Stage | Event / metric | Role in this test |
| --- | --- | --- |
| Eligibility | `financial_data_imported` → `first_financial_model_output_viewed` → `personalized_cashflow_action_reviewed` | Confirms the user reached the Module 2 candidate Aha moment before randomization. |
| Exposure | `post_aha_paid_prompt_shown` | Verifies the assigned treatment was delivered. |
| Decision | `paid_plan_started` | Feeds the primary trial-to-paid conversion metric. |
| Guardrail | Seven-day `cash_plan_review_started` among all assigned eligible users | Detects whether the prompt disrupts ongoing trial engagement. |

### Readout rules

- Randomize once per eligible user and keep assignment fixed for that user.
- Analyze eligible users by assigned variant, including users who do not interact with the prompt after exposure.
- Do not stop the test based on early conversion movement; read the primary metric only after each enrolled cohort has completed its reverse-trial period and the pre-set sample threshold is met.
- Report the overall trial-to-paid rate and the Aha-eligibility rate alongside the primary eligible-user result, so changes in onboarding mix are not mistaken for prompt impact.

---

## Connection to prior modules

| Module | Connection |
| --- | --- |
| **M1 · The Bet** | Tests the chosen Revenue hypothesis: a paid-plan continuation prompt after demonstrated value can improve trial-to-paid conversion. |
| **M2 · The Solution** | Uses `personalized_cashflow_action_reviewed`—the candidate Aha event from the onboarding flow—as the experiment entry point. |
| **M3 · The Mechanic** | Protects the ongoing Cash Plan Freshness habit with a cash-plan review guardrail for users who remain on trial. |
| **M4 · The Signals** | Uses the instrumented import → model → action-review sequence as leading diagnostics and trial-to-paid conversion as the lagging proof metric. |
