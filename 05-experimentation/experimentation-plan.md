# Experimentation Plan (Module 5)

## Get your documents ready
- **From M3, your hypothesis sentence:** Based on N-06’s unexplained bakery decline, after which they went back to their debit card that week, and the Month 4 in-store decline rate of 8.7% (T-101: 48 in-store declines), I believe that showing a decline reason and retry hint for Lena, a heavy BNPL user who pays with whichever option she trusts, will keep her using the card after a failed payment, as measured by a [X]% relative reduction in the in-store decline rate from 8.7% to [6.4% or lower]. I will protect month-1 retention at or above 64% and will make a go/no-go decision after two full monthly cohorts post-fix.
- **From M3, your primary success metric & guardrail metric:** Month-1 retention must stay at or above 64%, the lowest cohort value observed, so the fix does not cost the existing base.
- **From M4, the feature you scoped in your PRD this is what you're testing:** Every approved Riverty cardholder can pay with the card at the till within a minute of being approved, without typing a card number

## Define your experiment parameters
- **Feature under test pull from your M4 PRD:** Every approved Riverty cardholder can pay with the card at the till within a minute of being approved, without typing a card number
- **Persona pull your M2 persona:** Lena, 32, a heavy BNPL user who wants money to leave her account only after she keeps the item, hits an unexplained decline at the till and falls back to her debit card. The data shows the decline friction, but nothing splits declines by segment, so this link to Lena is inference.
- **Expected outcome the behaviour change you expect, from your M3 hypothesis:** Showing a decline reason and retry hint should keep people using the card after a failed payment, lifting month-1 and month-2 retention (now 64-69% and 51-57%) and in turn interchange revenue, though the size of the effect is unproven.
- **Primary success metric the one number that defines success, from M3:** Month-1 retention must stay at or above 64%, the lowest cohort value observed, so the fix does not cost the existing base.
- **Baseline rate today's rate of your primary metric, from your M3 data:** Activated to added to phone wallet: 66.8% (n=431 activated cards, 4-month pilot). The pilot is mostly employees, so this may differ for real users.
- **Guardrail metric & boundary what must not break, and how far it can move before you investigate:** In-store decline rate, baseline 8.7% (Month 4, 206 attempts). Investigate if it rises above ~10.7% (+2pp, my assumption). The metric is noisy: it was 12.1% in Month 1 and 6.4% in Month 3.
- **Minimum Detectable Effect (MDE) the smallest improvement worth shipping, your floor:** +5pp absolute (66.8% to 71.8%), my assumption. That is roughly 143 fewer stuck cards per 431 activations, so it is worth shipping.
- **Sample size per arm use the calculator in the builder, baseline + MDE:** ~1,330 (two-sided, α=0.05, 80% power, calculated by hand). Check it against the builder’s calculator. At a +10pp MDE it is ~315 per arm.
- **Traffic split & test duration 50/50 standard · cover ≥ 2 weekly cycles:** 50/50. Duration is the sample size ÷ weekly activations per arm, and at least 2 weekly cycles.
- **Significance threshold p < 0.05 is standard, explain any deviation:** p < 0.05, two-sided, with no deviation.

## Define your control and variant
- **Control (A) the current experience, reference your M2 moment of misery and M3 funnel/workflow data:** Today, after approval and card activation, the person must add the card to their phone wallet on their own. In the pilot, 143 of 431 activated cards (33.2%) never reached the wallet (T-102, M3 baseline 66.8%). This matters because in-store payment depends on the wallet, and the M2 notes show people default to their bank card in shops (N-03). The M3 funnel stops at activation (431 of 586 approved, 73.5%). Wallet add is tracked separately and sits after it.
- **Variant (B) your single change, copy the relevant screens & functional requirements from your M4 PRD:** Exactly one change: an “Add to phone wallet” action on the approval screen (backlog B2), which starts wallet provisioning directly from there. 

FR-1 The approval screen shows “Add to wallet” as the primary button, visible without scrolling at 375 x 667 px.
FR-2 The path from screen 1 to screen 3 takes 3 taps or fewer on success.
FR-3 “Skip for now” reaches the card home in 1 tap, with approval and activation status unchanged. The step never blocks approval.
FR-4 Every failure shows one reason from a fixed list of 3 (connection lost, wallet app declined the request, device not supported) plus a Retry button. No other reason text exists.
FR-5 After 3 failed retries the screen shows “Add later” and stops offering Retry.
FR-6 If the card is already in the wallet or the device is unsupported, the button is hidden and replaced by a one-line explanation.
FR-7 Six events are written to an in-memory list: shown, tapped, started, succeeded, failed (with reason code), abandoned. A debug panel can display them.
FR-8 Only the last 4 digits of the card appear anywhere in the UI or event list.
- **Isolation check, what has NOT changed? list everything identical between arms (app version, eligibility rules, notifications, onboarding). If something changed inadvertently, your test is compromised.:** App version and release build (feature-flagged, same build for both arms)
Eligibility, approval rules, credit policy, pricing and terms
Identity check flow (T-106) and activation flow
Notifications and reminders (T-104, T-108), including timing
In-app wallet prompts after activation, if any exist today
Decline messaging (B1), balance view (B3) and due dates (B8), none of which ship in either arm
Randomisation unit (per person, at approval), with the same invitees and the same period for both arms

## Formalize your hypothesis & shipping criteria
- **Your hypothesis (filled in):** I believe that an “Add to wallet” primary button on the approval screen (FR-1 to FR-6) for Lena-type users (heavy and regular BNPL users, 25-44) will result in more cards reaching the phone wallet, and so more in-store use, as measured by a +5pp absolute change (66.8% to 71.8%, about +7.5% relative) in wallet add rate within [N weeks = 2,660 activations ÷ weekly activations, minimum 2 weekly cycles].
We will protect in-store decline rate (declines ÷ in-store attempts) throughout the test.
- **Your shipping criteria (filled in):** We will SHIP if wallet add rate improves by ≥ 5pp at p < 0.05 (two-sided, 80% power, ~1,330 per arm) and in-store decline rate does not reach 10.7% (baseline 8.7% + 2pp) after [N weeks].

We will ITERATE if direction is positive but lift is below 5pp.

We will KILL if wallet add rate shows no improvement or moves negatively.

The read date is fixed at the end of [N weeks], no results reviewed before this date.

Sources and assumptions

Proven (data pack): the 66.8% baseline (n=431) and the 8.7% decline baseline (206 attempts, Month 4).
My assumptions, not data: the 5pp MDE, the +2pp guardrail boundary, and α=0.05 with 80% power.
Calculated: ~1,330 per arm, by hand, so check it against the builder’s calculator.
- **Hardest parameter to define, and did it change your hypothesis? quick debrief:** Hardest parameter: the primary metric’s definition (baseline and denominator), not the MDE. Yes, it changed the hypothesis.

Why the metric was hardest

The only wallet baseline in the data pack (66.8%) measures activated cards to wallet. FR-1 puts the button on the approval screen, before activation, so the variant changes who is eligible to add. The baseline no longer matches the test.
I introduced that mismatch in my first draft by assuming a metric you hadn’t confirmed. That one choice drives the baseline, sample size, isolation check and shipping rule.
