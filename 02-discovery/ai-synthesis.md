# AI Synthesis, Product Health & Insights Summary (Module 2)

## Responses
- **Assumption to validate #1:** Afraid of credit
- **Assumption to validate #2:** the customer wants to stay in control
- **Assumption to validate #3:** It needs to be more than a regular credit card
- **Moment of misery / red flag #1 (e.g., “user gave up after 3 tries”):** User gave up after not seeing why he was declined
- **Moment of misery / red flag #2:** To many cards, don't want another one
- **Moment of misery / red flag #3:** where can I use it, needs to be everywhere
- **Product Health & Insights Summary (Claude's output):** Product Health & Insights Summary: Riverty Consumer Card, Friends-and-Family Test Launch

Source: fictional practice data (12 interview notes, 8 tickets, pilot metrics). Severity ratings are my judgment, not recorded in the source.

Executive Summary

The card is stable enough to transact: overall decline rate is 2.2-3.5% and purchase volume grew each month. However, the failures that remain sit at the moments that decide habit formation, namely in-store payment, wallet setup and balance clarity, and they are largely silent to the user. Participants who hit one unexplained failure revert to their debit card, so the gap between technical uptime and user trust is the main health risk.

Thematic Synthesis
1. Technical Stability (In-Store Acceptance & Wallet)

In-store is where the card’s core promise (acceptance everywhere) is tested, and it is where it underperforms. The in-store decline rate (8.7% in Month 4) is roughly three times the overall rate and worsened from Month 3 (6.4%). Wallet provisioning is a second structural weakness, since in-store use depends on it.

Critical: In-store declines show no reason in the app. 48 declines are logged, and one participant abandoned the card after a bakery decline.
Critical: Wallet provisioning fails or is abandoned. 143 of 431 activated cards (about one third) never reached the wallet, which blocks in-store use for them.
High: Purchase push notifications arrive late in some shops. Participants assume the payment failed and pay again with another card, causing double payment.
2. Onboarding & Activation

The funnel loses the most people after approval. Only 73.5% of approved applicants activate, against 93.3% approval of completed identity checks. Later steps hold up better, with 81.2% of activated cards making a first purchase in the activation month.

High: Identity check re-requests a document photo after a failed upload, and some applicants give up. The identity-check step loses about 12% of applicants. That this ticket explains the drop is inference, not measured.
High: The activation-to-wallet handoff is not connected to the approval flow (see Theme 1), so setup stalls after the user has already committed.
3. Trust & Clarity

This is the most consistent qualitative theme. Participants cannot tell what they owe, when, or why the product behaves as it does. The card is layered on top of existing pay later orders without a unified financial picture.

High: Card balance and regular pay later orders are on separate screens, and participants ask which total is real.
High: Statement date and pay later due dates differ, so two reminders with different amounts can arrive in the same week.
Medium: The post-purchase instalment option appears only for some categories, and participants read this as random behavior.
4. Proposition & Adoption (Value Clarity)

Technical issues compound a weak habit case. Interviewees already juggle several BNPL apps, default to their bank card in shops, and are wary of anything resembling interest-bearing credit. Retention is middling: 51-57% of early cohorts were still active two months after activation, and the latest cohort is both small (39) and weaker at month 0 (74.4%). Engagement is strongly skewed to heavy BNPL users (5.82 purchases a month, 82.6% activation) over light users (2.46 purchases, 62.0%).

High: There is no clear reason to switch. Cashback was cited as a trial trigger, but the same interviewee separated trying from keeping.
Medium: Merchant value is unproven. An enterprise merchant asked what they gain, and an SME merchant would welcome referral offers but not traffic steering toward marketplaces.
Medium: Messaging risk. Instalment wording triggers a “credit card with interest” reaction in lighter BNPL users.
5. Support Load

No ticket volumes were provided, so load cannot be quantified. The pattern is nonetheless clear: unexplained declines, duplicate reminders and unclear totals all generate “why did this happen” questions that the app does not answer.

High (inferred): Silent failures (declines, late notifications) push users to support, or to abandonment.
Minor Technical Debt

No help article exists on whether card use affects credit score (T-107), and participants are already asking.

Evidence Quality (Context for the Above)
Sample bias: 639 of 1,200 invitees (53%) were employees, and internal risk flagged that approval and repayment results will look better than real customers.
Not measurable: Churn and adoption among existing users cannot be read from an invite-only test, and the annual spend figure (about EUR 2,595) is a 12x extrapolation of four months.
Small base: Interview findings rest on 12 notes, so treat them as directional.
- **Did the AI catch the specific moment of misery / pain point you found in Step 1?:** yes
- **Did it smooth over a critical frustration into a generic bullet point?:** no
- **Did the AI try to suggest features or a roadmap despite the constraints?:** no
- **Logic leak / hallucination #1 (e.g., “AI suggested a new search bar feature, roadmap leak”):** _(not filled in)_
- **Logic leak / hallucination #2:** _(not filled in)_
