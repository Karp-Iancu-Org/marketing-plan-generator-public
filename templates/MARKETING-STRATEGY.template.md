<!--
TEMPLATE: MARKETING-STRATEGY.template.md
PURPOSE: The spine of the generated marketing plan — position, avatars, the two
  engines, the funnel, phased rollout, deliberate exclusions, expansion paths,
  and risks. Every other generated doc hangs off this one; the operating detail
  lives in the sibling docs.
INPUTS:
  - PRD (business name, offer, market, proof assets)
  - Intake interview (§1 business model & offer economics, §2 avatar hypotheses,
    §3 creative faces, §4 budget, §5 geography/scope, §6 tech stack,
    §7 compliance, §8 capture opportunities)
  - Avatar research (customer-value segmentation, decision-factor data,
    voice-of-customer language — see ../01-avatars/AVATARS.md)
  - The lessons corpus (generator `lessons/`) for the doctrine each rule cites
GENERATOR ACTIONS:
  1. Fill every {{PLACEHOLDER}} from the source noted in its comment.
  2. Keep exactly ONE `<!- - MODEL: ... - ->` variant block per variant point
     (lead-gen | app | ecom) and delete the others, including the markers.
  3. Rewrite the worked-example blockquotes for the client's niche or delete them.
QA CHECKLIST (run before delivery):
  [ ] No {{...}} placeholders or `<!- - source: ... - ->` comments remain.
  [ ] Exactly one business-model variant survives at each variant point; no
      MODEL markers remain.
  [ ] Avatar table rows match ../01-avatars/AVATARS.md one-for-one.
  [ ] The anti-avatar is defined and the qualification/activation gate that
      excludes it from optimization is named.
  [ ] The decision-driver copy rule cites actual research numbers, not the
      template's illustrative ones.
  [ ] Phase A/B/C milestones are model-appropriate and dated.
  [ ] Compliance section names the client's real regulatory regime.
  [ ] All cross-references resolve to files that exist in the generated plan.
-->

# {{BUSINESS_NAME}} <!-- source: PRD --> — Marketing Strategy ({{FOCUS_NICHE}}-First) <!-- source: intake §5 -->

What we're doing, why, and in what order. The operating detail lives in the sibling docs; this is the spine.

## Position

**Niche down and be the biggest fish in a pond you can actually dominate.** The niching doctrine (the lessons corpus, generator `lessons/`) holds that a named specialist in a defined pond beats an everything-for-everyone generalist: "the #1 {{FOCUS_NICHE}} <!-- source: intake §5 --> provider in {{POND}}" <!-- source: intake §5 — the geography, category, or platform the business can plausibly dominate --> outperforms a broad-line brand competing everywhere at once. The niche is chosen where the business's value data is deepest, not where the founder's ambition is broadest: {{NICHE_SELECTION_RATIONALE}} <!-- source: avatar research — which segment concentrates revenue/LTV, with the numbers -->. Adjacent opportunities are not problems to solve now; they are recorded under Expansion paths.

Positioning statement to build all creative around — use the formula:

> **{{POND}}'s {{CATEGORY}} for {{AVATAR_COLLECTIVE}} — {{CREDIBILITY_STACK}}.**
>
> Where: *pond* = the market you'll dominate; *category* = the specific offer, named narrowly; *avatar collective* = who it's for, phrased so the right person self-identifies; *credibility stack* = 2–4 objective proof points (years, review count, install base, customers served, notable outcomes).

{{POSITIONING_STATEMENT}} <!-- source: PRD + intake §1 + avatar research, composed via the formula above -->



## Who we target (and stop targeting)

Full dossiers: `../01-avatars/AVATARS.md`. Summary of what the highest-value customer cohort looks like versus the rest ({{VALUE_COHORT_DEFINITION}} <!-- source: avatar research — e.g. "top 20% of N customers by revenue/LTV, cutoff $X, mean $Y" -->):

| Avatar | The call-out | Key lifts |
|---|---|---|
{{AVATAR_SUMMARY_ROWS}} <!-- source: avatar research — one row per avatar: name, the one-line objective situation the ad calls out, and the statistical lift(s) that earned it a dossier -->

**Anti-avatar** ({{ANTI_AVATAR_DEFINITION}} <!-- source: avatar research — the lowest-value cohort, with its median value and identifying traits -->): the customer whose acquisition looks like a win and whose economics are a loss — typically price-first, low-complexity, low-retention. We do not write creative that attracts them, and the qualification/activation gate keeps them from training the ad platform's optimization (they can still buy/be served — we just never optimize toward them).

**The decision-driver copy rule, which shapes ALL copy:** the high-value cohort chooses on {{PRIMARY_DECISION_DRIVER}} <!-- source: avatar research — the top-ranked decision factor in the high-value cohort, with its share and lift vs the base -->, not on {{ANTI_DRIVER}} <!-- source: avatar research — the factor that over-indexes in the anti-avatar (usually price) -->. Every hook, headline, and landing page leads with the primary driver and proof of it; nothing leads with the anti-driver.

## The two engines

### Engine 1 — The creative machine (Andromeda-native paid)

High-volume, narrow-call-out creative where **the creative is the targeting**: each ad names one avatar's objective situation + emotional pain in the customer's own words (`../01-avatars/language-bank.md`), lands on that avatar's dedicated page, qualifies with 3–5 objective questions (or the model's equivalent gate), and trains the pixel/SDK only on qualified events. Test with isolated budgets, scale winners into consolidated-budget angle campaigns; ship {{WEEKLY_CREATIVE_TARGET}} <!-- source: intake §4 — new creatives per week the budget supports --> new creatives/week at {{MONTHLY_AD_BUDGET}} <!-- source: intake §4 -->/month. Full rules: `../03-ads/ADS-PLAYBOOK.md`.

### Engine 2 — The capture flywheel (every customer becomes an ad)

Organic content posted at sustainable volume feeds paid with pre-validated winners (the ~1-in-10 outlier rule), and every customer journey is captured at set checkpoints so proof compounds: {{CAPTURE_CHECKPOINTS}} <!-- source: intake §8 — the journey moments where proof is captured, e.g. pre-purchase doubts → first win → milestone → resolution → review -->. The corpus's hardest-won creative lesson applies directly: customer-featuring ads ultimately beat founder-featuring ads — so the capture system is not a nice-to-have, it is the raw-material supply for the winning format. Where featuring real customers is constrained ({{CAPTURE_CONSTRAINT}} <!-- source: intake §7/§8 — privacy, anonymity, platform rules, or "none" -->), the production spec designs proof-safe formats (anonymized retells, review-screenshot ads, voice-over reconstructions, opt-in on-camera testimonials for the willing minority): `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`.

## The funnel (one conversation, end to end)

<!-- MODEL: lead-gen -->
```
Narrow ad (avatar + pain, their words)
  → avatar landing page (avatar-specific VSL, proof, no exit points)
    → qualification form ({{QUALIFICATION_QUESTIONS}})   <!-- source: intake §1 — the 3–5 objective questions that separate avatar from anti-avatar -->
      → qualified? pixel event ∙ both branches → intake
        → contact within {{SPEED_TO_LEAD_SLA}}           <!-- source: intake §1 — e.g. "60 seconds" -->
          → {{SALES_MEETING}} booked within {{BOOKING_WINDOW}}  <!-- source: intake §1 — the sales conversation and how fast it must land -->
            → PRE-MEETING VSL sent (the 10–15 most-asked questions, answered on video)
              → {{SALES_MEETING}} = discovery + plan (not a free advice session)
                → agreement + payment
                  → capture checkpoints → new proof → new ads
```
<!-- /MODEL -->
<!-- MODEL: app -->
```
Narrow ad (avatar + pain, their words)
  → store listing / web-to-app funnel page (avatar-specific screenshots, VSL, proof)
    → install
      → onboarding (avatar-aware; asks the {{QUALIFICATION_QUESTIONS}})  <!-- source: intake §1 — the onboarding answers that separate avatar from anti-avatar -->
        → ACTIVATION = {{ACTIVATION_EVENT}}              <!-- source: intake §1 — the in-app moment that predicts retention; this is the "qualified lead" of the app model, and the event the ad platform optimizes toward -->
          → onboarding/demo videos pre-frame each next step
            → trial → subscription ({{MONETIZATION_EVENT}})  <!-- source: intake §1 — trial start, paywall view, subscribe -->
              → capture checkpoints → new proof → new ads
```
<!-- /MODEL -->
<!-- MODEL: ecom -->
```
Narrow ad (avatar + pain, their words)
  → product / avatar landing page (product-demo VSL, proof, reviews, no exit points)
    → add to cart ({{CART_QUALIFIER}})                   <!-- source: intake §1 — what marks a high-intent cart: AOV threshold, hero-SKU, bundle -->
      → checkout → PURCHASE (the pixel's primary optimization event)
        → post-purchase flows (unboxing/how-to video pre-frames first use;
           review ask at {{REVIEW_ASK_TIMING}};          <!-- source: intake §8 -->
           replenishment/cross-sell at {{REPLENISHMENT_CADENCE}})  <!-- source: intake §1 -->
          → capture checkpoints → new proof → new ads
```
<!-- /MODEL -->

**The pre-purchase video principle:** pre-frame every consequential next step with video, so the prospect arrives pre-sold and pre-answered instead of needing the founder (or a sales rep, or a support queue) to do it live.
<!-- MODEL: lead-gen -->
For lead-gen that is the **pre-consult VSL**: it answers the most-asked questions before the sales meeting, moves that meeting toward discovery and commitment, and is the load-bearing asset for both show rate and non-founder sales leverage. It is the single highest-priority video in the production spec.
<!-- /MODEL -->
<!-- MODEL: app -->
For an app that is the **demo and onboarding video set**: the store-page/landing demo pre-sells the install, and step-scoped onboarding videos pre-answer the questions that otherwise stall users before activation. They are the highest-priority videos in the production spec.
<!-- /MODEL -->
<!-- MODEL: ecom -->
For ecommerce that is the **product-demo VSL**: it answers the objections that stall carts (fit, use, durability, comparison) before checkout, and its post-purchase sibling (unboxing/how-to) pre-frames first use so the product gets used, reviewed, and reordered. They are the highest-priority videos in the production spec.
<!-- /MODEL -->

## Phased rollout

**Phase A — Foundation + statics (weeks 1–4).**
Tracking + landing pages/funnel + ad account per `../06-setup-walkthroughs/*.md` (in that order). Record the priority pre-purchase video and the first on-camera shoot. Launch angle 1 (static avatar call-outs — 10+ statics per avatar) and begin the weekly {{WEEKLY_CREATIVE_TARGET}}-creative cadence. **Start ALL capture systems now** — proof footage takes months to accumulate, which is exactly why capture is Phase A, not Phase C.
<!-- MODEL: lead-gen -->
Intake SLAs live from day one: {{SPEED_TO_LEAD_SLA}} first contact, defined follow-up cadence, {{BOOKING_WINDOW}} booking, day-before confirmation touch.
<!-- /MODEL -->
<!-- MODEL: app -->
Activation instrumentation live from day one: {{ACTIVATION_EVENT}} defined, fired, and verified end-to-end from ad click through install to in-app event before spend scales.
<!-- /MODEL -->
<!-- MODEL: ecom -->
Purchase and post-purchase instrumentation live from day one: pixel + server-side purchase events verified to the order ledger, and the review-ask and replenishment flows switched on before spend scales.
<!-- /MODEL -->

**Phase B — Video angles + flywheel (months 2–3).**
Angle 2 (talking-head video from the monthly shoot, assembled hook × body × CTA). Organic posting cadence running; outliers promoted to paid with an appended CTA. Review/proof-screenshot statics live. Server-side {{DOWN_FUNNEL_EVENT}} <!-- source: intake §6 — the deepest-funnel conversion fed back to the ad platform: retained/closed-won for lead-gen, subscription for app, LTV-qualified purchase for ecom --> events flowing. First iteration cycles (roughly 70% proven / 20% variation / 10% wild) on real winners.

**Phase C — Proof compounding (months 4–12).**
Testimonial/customer-story angle activates as capture produces material; first life-cycle ads assembled from journey checkpoints; per-creative revenue attribution (`../05-measurement/MEASUREMENT.md`) reallocates budget toward the avatars and hooks that produce {{DOWN_FUNNEL_EVENT}}, not just cheap leads/installs/carts; spend escalates {{SCALING_RATE}} <!-- source: intake §4 — e.g. "+20–30%/month" -->/month while acquisition cost holds and {{CAPACITY_CONSTRAINT_SHORT}} <!-- source: intake §1 — the fulfillment/capacity system that must absorb growth --> absorbs.

## What we deliberately are NOT doing

- **No interest-targeted or "boosted post" advertising, and no generic category creative** ("{{GENERIC_AD_EXAMPLE}}" <!-- source: PRD — the generic near-you/category ad this niche defaults to -->) — generic creative recruits the anti-avatar and un-trains the optimization.
- **No leading with price or discounts for premium avatars, ever.** The value data says the high-value cohort under-indexes on price as a decision factor and the anti-avatar over-indexes on it; discounting selects precisely the customers we're structurally excluding. (Where the model has a legitimate promo mechanic — e.g. ecommerce offers — it is framed as value/bundle, never as "cheapest.")
- **No founder-dependence by design:** entity-trust language ("our team… we've handled…"), multiple faces from day one per intake §3, spokesperson formats specced — no single person on camera is a bottleneck or key-person risk.
- **No new offers or wrappers until the base machine runs.** The "new" lever (seasonal wrappers, workshops/webinars, product-line extensions) is documented in `../03-ads/ADS-PLAYBOOK.md` for later — it multiplies a working machine and distracts a non-working one.

## Expansion paths (post-dominance)

Derive these — do not invent them. For each, the generator should mine:

1. **Adjacent-offer cross-sell:** scan the customer data and interview for a second offer the existing base has already signaled demand for (survey "interested/not sure" answers, support requests, repeat-purchase adjacencies). A warm internal list beats a cold campaign. {{CROSS_SELL_CANDIDATE}} <!-- source: avatar research + intake §1 — the strongest adjacent-offer signal, with the number behind it -->
2. **A bordering avatar promoted to standalone:** the avatar whose creative already borders a neighboring segment. {{BORDER_AVATAR_CANDIDATE}} <!-- source: avatar research -->
3. **Geographic / market concentration:** the sub-markets that over-index in the high-value cohort, where spend can be tilted. {{GEO_CONCENTRATION_CANDIDATE}} <!-- source: avatar research + intake §5 -->
4. **A mid-funnel layer** (webinar, quiz, comparison hub, free tool) once cold-traffic volume justifies building one.



## Risks & watch items

- **{{CAPACITY_CONSTRAINT}} <!-- source: intake §1 — the specific capacity ceiling: sales-calendar saturation, fulfillment/inventory, support/onboarding load --> is the likely first constraint, not lead flow.** Watch its saturation metric weekly and apply the lead-scoring/routing rules in `../05-measurement/MEASUREMENT.md` before buying more demand.
- **Compliance — {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 — the governing rules: professional-advertising codes, platform policies (app-store, health, finance), FTC endorsement/claims rules, privacy law -->:** no misleading claims; testimonials and outcome claims must satisfy the regime's substantiation and expectation rules; the creative spec builds the constraints into format recipes; all customer-story assets require written consent or full anonymization.
- **Tracking fragility:** the qualified/unqualified (or activation, or purchase) event routing is the single point whose silent failure poisons the whole optimization loop; monthly end-to-end dry-runs are mandatory (`../06-setup-walkthroughs/*.md`).
- **Creative starvation:** the whole model dies if the weekly {{WEEKLY_CREATIVE_TARGET}} stops — which is exactly what the downstream asset-production project exists to prevent (see the README's handoff note).
