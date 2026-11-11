# PRD & Prototype Sprint (Module 4)

## Pick & scope with MoSCoW
- **The “Now” feature I’m scoping (name + one-line core description):** Add to phone wallet straight from the approval screen
- **My finalized Must-Haves (after overriding the AI):** Add to wallet button on the approval screen (Apple Pay and Google Pay) that provisions the card in-app. Lena should not re-enter card details. Without it the feature doesn’t exist.
Skippable step. It must never block approval or activation. Online purchases don’t need the wallet, and approved → activated (73.5%) is already a leak.
Failure state with a reason and a retry. T-102 says the add “fails or is abandoned”. A silent failure repeats the N-06 pattern (unexplained error, back to debit).
State check. If the card is already in the wallet, or the device can’t take it, hide the button.
Funnel events: button shown, tapped, provisioning started, succeeded, failed (with error code), abandoned. The pack can’t tell failure from abandonment, so you can’t fix the 33% gap without this.
Security and compliance baseline: the identity step required by the wallet providers, and no card data in logs. PCI scope needs a check (your area).
- **What I demoted from Must → Should/Won’t, and why:** nothing

## Generate your Simplified PRD
- **One thing my PRD makes explicit that a vague brief would have missed:** _(not filled in)_

## Prompt-to-prototype sprint
- **Where did the prototype reveal a gap in my PRD logic? (what I had to update):** did not
- **My prototype: save Claude's HTML as prototype.html in 04-roadmap/, open it in your browser, and add a screenshot:** _(not filled in)_
