# Roadmap, PRD & Prototype (Module 4)

## Your strategic anchors
- **Persona (M2), who are you solving for?:** Lena, 32, a heavy BNPL user who wants money to leave her account only after she keeps the item, hits an unexplained decline at the till and falls back to her debit card. The data shows the decline friction, but nothing splits declines by segment, so this link to Lena is inference.
- **Primary success metric (M3), your leading indicator:** The in-store decline rate, 8.7% in Month 4 and 6.4% at its best in Month 3. A second option is the share of declined users who purchase again within 7 days, but that data is not in the pack today.
- **Moment of misery (M2), the specific friction blocking the goal:** They can’t see what they owe on the card and on regular pay later orders together (N-07). Balances sit on two screens (T-103), and two reminders for different amounts arrive in the same week (T-104).
- **Guardrail metric (M3), what must not drop or break:** Month-1 retention must stay at or above 64%, the lowest cohort value observed, so the fix does not cost the existing base.

## Scan the backlog & set a human baseline
- **My instinctive “quick wins” before touching the AI (2 to 3 feature IDs + why):** B1: Decline reason and retry hint shown in the app
B2: Add to phone wallet straight from the approval screen

## Audit, override & decide
- **Where did you override the AI? (feature + old vs. new score + why):** did not
- **Did the AI over-value a Sales/Eng request your M2 interviews don’t support?:** _(not filled in)_
- **Did it underweight something your M3 cohort/funnel data strongly supports?:** _(not filled in)_

## Generate your interactive roadmap
- **My “Now” lane (this sprint), the 2 to 3 quick wins I’ll build first:** - B1 Decline reason and retry hint in the app, It hits the primary metric and N-06’s churn moment directly (T-101, 8.7% in-store declines in Month 4). It assumes decline codes are available to the app, which I haven’t verified.
- B2 Add to phone wallet from the approval screen, 143 activated cards never reached the wallet (T-102, 66.8% baseline). No wallet means no in-store use, so it is a precondition for the in-store pitch.
- **What I cut, and the “no” I’m protecting the scope from:** - B5 Choose pay now or pay later per purchase, after paying, It fits Lena’s “money leaves after I keep it” need. But instalments are only 15-18% of purchases, T-105 shows confusion rather than demand, and it needs per-purchase credit decisioning plus approval.
- B6 Partner offers in the card app, It’s the merchant-side story (N-09), but not Lena’s friction, and it needs merchant integrations. Revisit it for brief Q3, not for this test.
- B7 Cashback on every purchase, N-12 says it drives a first try, not continued use. It costs margin and needs pricing approval. It does nothing for declines or retention.
- B8 Physical card, N-03 taps a bank card by habit. The wallet (B2) already covers in-store tapping, and a physical card adds production and logistics.
- **Prototype/roadmap screenshot link (paste into your deliverables):** bu-pay-credit-roadmap.html
