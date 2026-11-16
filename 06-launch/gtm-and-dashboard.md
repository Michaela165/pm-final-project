# GTM Strategy & Success Dashboard (Module 6)

## Get your prior work ready
- **The feature you're launching from your M4 PRD, one feature, not a list:** Add to wallet” as the primary button on the approval screen (FR-1), with a “Skip for now” that never blocks approval (FR-3). Failure reasons, Retry and the “Add later” state (FR-4, FR-5) are part of the same flow.
- **What your M5 experiment will test your hypothesis, primary metric and ship / iterate rule, the evidence the launch rests on:** Hypothesis: Offering wallet add on the approval screen will get more approved cardholders to add the card to their phone wallet, which is the precondition for paying in-store.
Primary metric: share of approved people who add the card to a wallet within [window, your assumption]. The pack has no baseline for this. The only wallet baseline is 66.8% for activated to wallet (n=431), which doesn’t match a button placed before activation. Measure a baseline first, or move the button after activation.
Guardrail: in-store decline rate (declines ÷ in-store attempts), compared against the control arm. Baseline 8.7% in Month 4. The boundary of +2pp over control is my assumption.
Ship / iterate / kill: SHIP if the lift is ≥ +5pp (my assumption) at p < 0.05 and the guardrail stays within +2pp of control. ITERATE if the lift is positive but below 5pp, or ≥ 5pp but not significant. KILL if there is no lift, a negative lift, or a guardrail breach. The result is read once, on a fixed date.
- **Your persona pull your M2 persona, this anchors your audience:** Lena, 32, Cologne. She is salaried on a middling income with no real cushion, shops almost entirely on her phone, and uses BNPL on most non-trivial purchases. She wants money to leave her account only after she has decided to keep the item. She has Klarna and PayPal installed and uses whichever appears at checkout. She knows Riverty but doesn’t prefer it. Her moment of misery in this plan is a card that won’t work at the till, with no reason shown, so she falls back to her debit card. The persona comes from the case brief. Lena is a fictional archetype, and the heavy-BNPL-user notes (N-01, N-02, N-04) support her.

## Set your goal, then your audience
- **Primary GTM goal awareness · engagement · conversion, pick one:** Conversion: approved cardholders adding the card to their phone wallet, so they can pay in-store.
- **Why this goal? what makes this the right goal for this feature right now:** The feature lives inside the existing product, so awareness is the wrong goal, as the trap says. The audience is already Riverty users.
The pilot shows the leak is after approval, not before. 143 of 431 activated cards (33.2%) never reached the wallet (T-102). In-store payment depends on the wallet, and in-store is the reason for the card (N-03, N-04).
Engagement is the weaker pick. It can’t be reached until the card is usable in shops.
Caveat: the 66.8% baseline measures activated to wallet, while the button sits before activation. The goal is valid, but its measure is still unresolved.
- **Target audience the specific segment your goal implies, be precise:** Heavy BNPL users in Germany (4+ orders a month) who use the Riverty app monthly and have been approved for the card. They are the Lena-type segment.

## Size your launch
- **Launch tier S (minimal) · M (targeted) · L (multi-channel) · XL (full GTM):** S (minimal): in-product only, with no channel campaign.
- **Justification reach + revenue impact + what silence would risk:** Reach is narrow. Only people who have just been approved for the card see the button. In the pilot that was 586 of 1,200 invited (48.8%). The scaled number is unknown, and I won’t invent it. The audience sizing is an assumed practice figure and is a ceiling for the card, not for this feature.
Revenue impact is indirect and unproven. Wallet add enables in-store use, which is what drives interchange. The pack has no revenue per wallet card, so I can’t size it. The measured evidence is small: a +5pp lift (my MDE assumption) is about 22 more wallet cards per 431 activations. That is not a big-launch case. I’m not drafting a forecast, since that isn’t yours to own.
Silence risk is low. The button sits on the approval screen (FR-1), so every approved person sees it without any campaign. Skipping is safe, because “Skip for now” never blocks approval (FR-3). The cost of saying nothing is a slower lift, not a broken experience.
Over-investing is the bigger risk. The test can’t be read until there is scale, and the pilot is mostly employees (N-10). Spending on channels before the lift is proven would be premature.
- **Is this a launch or a release? does it need go-to-market, or can it just ship?:** A release. It is a flow change inside an existing product, for people who are already approved. It needs no external positioning, no merchant messaging and no new channel.

What it does need: a feature flag and a 50/50 split, as the experiment requires. Persisted, arm-tagged events (FR-7 today is an in-memory list), a short note to support and operations, and a help article. The credit score article (T-107) is a related gap.
Caveat: the card itself is a launch, and your GTM plan covers it. This feature is one release inside that launch. State that, so the S tier isn’t read as the size of the whole card.

## Choose your top three channels and plan assets
- **Channel 1 owned / earned / paid, and why it reaches your audience:** The “Add to wallet” button itself (FR-1). Everyone who is approved sees it at the moment of intent, so it reaches 100% of the audience at no cost. It is also the variant under test, so it doubles as the channel.
- **Channel 2 owned / earned / paid, and why:** A reminder to people who tapped “Skip for now” or reached “Add later” (FR-3, FR-5). They are the people the feature missed. Reach is limited: only 250,000 of the assumed 1,000,000 base allow push and 400,000 opted in to marketing email (both assumed practice figures, not facts). Use push first, and email as a fallback for people who haven’t allowed push.

Experiment conflict: your isolation check holds notifications constant in both arms. Send no nudge during the test, or send it identically to both arms. Otherwise it contaminates the result. Start the nudge after the read date.
Known risk: push timing is unreliable (T-108, notifications arrive late), so a wallet reminder could arrive after the person has already paid another way.
- **Channel 3 owned / earned / paid, and why:** A wallet help article, covering the three failure reasons (FR-4), is the channel for people who contact support. It also closes the credit score gap (T-107), where no article exists yet. It reaches people at the point of failure.

Not used, on purpose

Paid: no case at S tier. The audience is already inside the product, so paid media would spend money to reach people we already reach for free.
Earned: a button inside an existing flow gives press and reviews nothing to report. If your template requires one of each, I’d write “none planned” rather than invent a plan.
- **Enablement & assets what Sales / CS / Support need, plus the assets to build (one-pager, demo, etc.):** Support and CS:
A one-pager: what the button does, the three failure reasons and what to tell the customer for each, and when to escalate.
Macros for “card won’t add to wallet” and “can I skip”.
A help article, including the credit score answer (T-107).
Risk and operations: a short note that approval and activation status don’t change (FR-3), so credit policy is untouched. Confirm this with them rather than assuming it.
Engineering and QA: persisted, arm-tagged events (FR-7 is an in-memory list today), plus the feature flag and the 50/50 split.
Product and analytics: a read-date calendar hold, and a rule that nobody reviews results before that date.
Internal release note: one paragraph explaining what changed and what is being tested, so nobody reports a wallet lift before the read.
Not needed: a sales deck, merchant messaging or a demo. This feature has nothing for merchants.

## Make it executable
- **Ownership named owner per key activity, individual, not department:** Activity	Owner (replace with a name)
Overall release and the read-date decision	[You, Senior PM Payments]
Wallet provisioning build, feature flag, 50/50 split	[Engineering lead, card issuing gateway]
Persisted, arm-tagged events (FR-7 gap)	[Engineering lead or data engineer]
Experiment analysis and the single read	[Analyst or data owner]
Guardrail check (in-store decline rate vs control)	[Risk analyst]
Confirmation that approval and credit policy are untouched (FR-3)	[Risk owner]
Support one-pager, macros, help article incl. credit score answer (T-107)	[Support lead]
Post-read nudge (push and email)	[CRM or lifecycle owner]
Regulatory and PCI check on the wallet flow	[Compliance owner]
- **Budget & resource gaps what costs extra, and any asset you can't currently build:** No costs in the data pack. I can’t give a budget figure, so state “no paid spend planned” (from Step 3) and mark the rest as unestimated.
Costs to flag before you lock the plan:
Engineering and QA capacity. The brief says the card platform is shared and capacity is limited.
Event persistence. FR-7 is an in-memory list today, so a real pipeline is extra work. This is the biggest gap.
Wallet provider certification or provisioning terms. I don’t know if any apply, so check it.
Analyst time for the read.
Assets you may not be able to build now:
The help article’s credit score answer needs a legal or risk review (T-107).
The experiment needs a scaled rollout (~1,330 per arm, ~2,660 activations in total). The pilot had 431 in four months, so the test can’t run before the card reaches volume.
Approval lead time. The case says every new proposition needs regulatory approval, which adds months (N-11). Check whether a wallet-add flow counts as a proposition change. If it does, it gates everything. I don’t know, so it’s a question for compliance.
- **Timeline Phase 1 beta → Phase 2 launch moment → Phase 3 post-launch:** Timeline (relative, no dates)

Phase	Work	Exit condition
1. Beta	Build behind the flag. Persist events. Internal and pilot cohort only. Support assets ready. Baseline measured for the chosen metric definition	Events verified per arm. Baseline known. Compliance sign-off
2. Launch moment	Switch the 50/50 split on for newly approved cardholders. No nudges or other notification changes during the test. Fixed read date set before start	Sample reached or the fixed read date arrives. No results reviewed before
3. Post-launch	One read, then SHIP, ITERATE or KILL. If SHIP: roll out to 100% and start the push and email nudge for people who skipped. Re-check the guardrail	Decision recorded. Retro on the decline guardrail

## Define how you'll know it worked
- **Success metrics 2 to 3 metrics that match your GTM goal:** Primary: wallet add rate. Share of newly approved cardholders who add the card to a phone wallet within [window, your assumption]. The only baseline in the pack is 66.8% for activated to wallet (n=431), which doesn’t match a button placed before activation. Measure a baseline for your chosen definition first. Target: ≥ +5pp vs control at p < 0.05 (my assumption).
Secondary: in-store use. In-store share of purchases among wallet cards, compared with the Month 4 baseline of 17.0% (1,107 purchases). This shows whether wallet add leads to the in-store behaviour that earns interchange. The pack doesn’t split it by wallet vs non-wallet cards, so you need that cut in the new event data.
Guardrail: in-store decline rate (declines ÷ in-store attempts). It is measured against the control arm, not a fixed number. The baseline is 8.7% and the boundary is +2pp over control (my assumption). Also watch the approved-to-activated rate (73.5% in the pilot), since FR-3 says it must not change.
- **Bad signal to watch for e.g. high reach, zero signups = message-market mismatch:** Bad signals to watch for

Signal	What it tells you	Next step
Many taps, few successes	Provisioning fails, so the feature is blocked, not unwanted	Check the FR-7 reason codes. Fix the failure first
Wallet add up, in-store use flat	Wallet add is a vanity metric. People add the card but still pay with debit (N-03)	Don’t ship on wallet add alone. Look at what the card offers in shops
High skip rate on “Skip for now”	The button is at the wrong moment or the value is unclear	Iterate on timing and copy
Decline rate higher than control by more than 2pp	The flow adds a broken path, or more attempts expose old problems	Investigate before reading the primary metric
Approval or activation rate drops in the variant	The step blocks the flow, which contradicts FR-3	Treat the test as compromised
Arm sizes or events missing	Persistence or randomisation is broken (FR-7 gap)	Void the read
- **Most likely post-launch decision double-down · iterate · pivot · deprioritize, and what would trigger it:** Most likely post-launch decision: iterate.

This is my judgement, not a prediction with data behind it. The pack has no revenue per wallet card, and the pilot is mostly employees (N-10).
Trigger for iterate: the lift is positive but below 5pp, or ≥ 5pp but not significant, or wallet add rises while in-store use stays flat.
Double-down if the lift is ≥ 5pp at p < 0.05 and the guardrail holds. Roll out to 100% and start the post-read nudge from Step 3.
Deprioritise or kill if there is no lift, a negative lift, or a guardrail breach. A pivot is only worth discussing if the decline reason, not the button, turns out to be the real problem.
The read date is fixed, and nobody reviews results before it.
