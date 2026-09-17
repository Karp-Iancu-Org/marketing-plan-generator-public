<!--
TEMPLATE: AVATARS.template.md
PURPOSE: Produce the avatar dossier document for a marketing plan — the single source of truth
  for WHO the ads target, WHO they must repel, and how each avatar maps to production assets.
  Every downstream doc (../02-strategy/MARKETING-STRATEGY.md, ../03-ads/ADS-PLAYBOOK.md,
  ../04-creative-production/CREATIVE-PRODUCTION-SPEC.md) keys off the avatar IDs defined here.

INPUTS REQUIRED before instantiating:
  1. PRD — product/offer definition, business model (lead-gen | app | ecom), pricing.
  2. User interview — especially §1 (business model & offer economics), §2 (avatar hypotheses),
     §5 (geography/scope), §8 (capture opportunities).
  3. Avatar research corpus — competitor reviews (own + competitor Google/Trustpilot/G2/app-store
     reviews), community mining (Reddit, Facebook groups, forums, Discord), and Meta Ad Library
     patterns for the niche. The distilled quotes live in ../01-avatars/language-bank.md — build
     that doc from the same corpus alongside this one.

MODEL VARIANTS: keep exactly one of each MODEL: lead-gen / app / ecom block and delete
  the rest, per intake §1.

QA CHECKLIST for the instantiated doc:
  [ ] 3–5 avatars, each with a distinct decision driver — no two avatars separable only by demographics.
  [ ] Every pain and objection traces to a quote in ../01-avatars/language-bank.md or an explicit
      interview answer (see EVIDENCE RULE below). Zero invented pains.
  [ ] Objective call-outs are attributes an ad can literally name under current Meta targeting-era
      norms (Andromeda: creative does the targeting) — no protected-category call-outs
      (race, religion, health conditions, etc.) per platform policy and intake §7 compliance notes.
  [ ] ANTI-AVATAR section names concrete repel signals AND the optimization gate that handles leakage.
  [ ] Production-mapping table covers every avatar, priorities are justified, slugs/angles match
      ../04-creative-production/CREATIVE-PRODUCTION-SPEC.md.
  [ ] No unreplaced {{PLACEHOLDERS}}, no leftover MODEL blocks, no template comments remain.
  [ ] Cross-avatar facts section states the dominant decision driver and any anti-signal explicitly.
-->

# Customer Avatars — {{BUSINESS_NAME}} <!-- source: PRD --> {{OFFER_SHORT_NAME}} <!-- source: PRD -->

Derived from {{RESEARCH_CORPUS_SUMMARY}} <!-- source: avatar research — e.g. "212 competitor reviews across 4 firms, 340 community threads, 58 Ad Library creatives, and the founder interview" --> plus the founder/operator interview. There is no customer-data mining behind this document — every claim below is sourced from the interview or the external research corpus, and each avatar's evidence is traceable to `../01-avatars/language-bank.md`.

**Cross-avatar facts every ad should respect**
- **Dominant decision driver:** {{PRIMARY_DECISION_DRIVER}} <!-- source: intake §2 + avatar research — what the best-fit customers say made them choose; from decision-language mining --> — and the corresponding **anti-signal**: {{ANTI_SIGNAL}} <!-- source: avatar research — the factor that predicts a bad-fit customer, e.g. "price-first shoppers" -->. Creative should lean into the driver and never appeal on the anti-signal.
- **Geography/scope:** {{GEOGRAPHIC_SCOPE}} <!-- source: intake §5 — service area, shipping regions, app store countries, or "global" -->. {{GEO_PRIORITY_NOTES}} <!-- source: intake §5 + avatar research — any sub-regions/markets that over-index for best-fit customers -->
- **Discovery channels:** {{DISCOVERY_CHANNELS}} <!-- source: intake §2 + avatar research — where best-fit customers say they found solutions like this (search, referrals, communities, app-store browse, social) -->. Note which channels the research suggests skew toward lower-fit customers.
- **Offer economics guardrail:** {{OFFER_ECONOMICS_NOTE}} <!-- source: intake §1 — e.g. "high-consideration $X purchase; long sales cycle is a feature not a bug" or "LTV concentrates in annual-plan subscribers" -->. This shapes which avatar gets budget first (see production map).
- {{ADDITIONAL_CROSS_AVATAR_FACT}} <!-- source: avatar research — optional: any pattern that holds across all avatars, e.g. a shared trigger event or seasonality; delete if none -->



---

<!-- REPEAT the dossier skeleton below for each avatar (3–5 total). ID them {{AVATAR_ID}} = A1, A2, A3…
     Order by expected value, highest first. -->

## {{AVATAR_ID}} — {{AVATAR_NAME}} <!-- source: intake §2 + avatar research — a vivid, situation-based name ("The Overwhelmed Ops Manager"), not a demographic label -->
*"{{AVATAR_ONE_LINE_QUOTE}}"* <!-- source: avatar research — a real or lightly-edited quote from the corpus that captures the avatar's core want -->

- **Objective call-outs (what the ad can name):** {{OBJECTIVE_CALLOUTS}} <!-- source: intake §2 + avatar research — concrete, nameable attributes: role/job title, life stage, situation trigger, tool they already use, business type, tenure ("10+ years in the house"), NOT protected categories. In the Andromeda era the creative IS the targeting: these call-outs go into hooks so the right person self-selects. -->
- **Situation:** {{AVATAR_SITUATION}} <!-- source: intake §2 + avatar research — 2–4 sentences: what is happening in their life/business that makes them a buyer now; the trigger event if one exists -->
- **Pains (their words, themed):** {{AVATAR_PAINS}} <!-- source: avatar research — 3–6 themed pains, each phrased close to corpus language; every one must map to a quote theme in ../01-avatars/language-bank.md -->
- **Objections/fears:** {{AVATAR_OBJECTIONS}} <!-- source: avatar research + intake §2 — why they hesitate: risk, price framing, past bad experience, switching cost, "will this work for MY case" -->
- **Decision driver:** {{AVATAR_DECISION_DRIVER}} <!-- source: avatar research — the ONE factor that closes this avatar (proof of expertise, speed, feeling heard, social proof volume, a guarantee). Must be distinct enough from other avatars to justify separate creative. -->
- **Value note:** {{AVATAR_VALUE_NOTE}} <!-- source: intake §1 + intake §2 — why this avatar matters economically: expected order value / LTV tier / retention behavior / strategic value (referrals, reviews). Hypothesis-labeled if not yet evidenced. -->



<!-- /REPEAT -->

---

## ANTI-AVATAR — who the creative must stop attracting

{{ANTI_AVATAR_PROFILE}} <!-- source: intake §2 + avatar research — 3–6 bullets describing the bad-fit lead/customer: the signals that predict refunds, churn, no-shows, price-only shopping, support burden, or zero LTV. Mine competitor 1-star reviews and the interview's "worst customer" answer. -->

- {{ANTI_SIGNAL_1}} <!-- source: avatar research — e.g. "leads with price before understanding the offer" -->
- {{ANTI_SIGNAL_2}} <!-- source: avatar research — e.g. "wants an outcome the product/service can't deliver" -->
- {{ANTI_SIGNAL_3}} <!-- source: avatar research + intake §2 — add/remove bullets as evidence dictates -->

**Handling — creative rule:** never write creative that appeals on {{ANTI_APPEAL_TO_AVOID}} <!-- source: avatar research — usually "cheap/fast/easy" framing, free-forever angles, or maximal promises -->. The repel work happens in the hooks (qualifying language that makes bad fits scroll past) and at the optimization gate:

<!-- MODEL: lead-gen -->
**Handling — optimization gate:** the qualification form (`../06-setup-walkthroughs/TRACKING-SETUP.md` §2) asks {{QUALIFYING_QUESTIONS_SUMMARY}} <!-- source: intake §2 + intake §8 — the 1–3 questions that separate real avatars from anti-avatars --> and only qualified submissions fire the conversion event, so the pixel optimizes toward fit, not volume. Intake/sales still treats unqualified leads politely — some are misclassified avatars, and the distinguishing question is {{DISAMBIGUATION_QUESTION}} <!-- source: intake §2 — the single question that tells a disguised good-fit lead from a true anti-avatar -->.
<!-- /MODEL -->

<!-- MODEL: app -->
**Handling — optimization gate:** never optimize campaigns on installs — anti-avatars install and churn, and install-optimized delivery finds more of them. Optimize on {{ACTIVATION_EVENT}} <!-- source: intake §1 + intake §6 — the in-app event that predicts retention/revenue: trial start, activation milestone, first purchase, subscription --> fired via {{EVENT_PIPELINE}} <!-- source: intake §6 — MMP/SDK path, e.g. "AppsFlyer → CAPI" -->. Store-listing copy carries the same qualifying language as the ads so bad fits bounce before installing.
<!-- /MODEL -->

<!-- MODEL: ecom -->
**Handling — optimization gate:** never optimize on add-to-cart or initiate-checkout — those events over-sample browsers and discount-hunters. Optimize on purchase ({{PURCHASE_EVENT_NOTE}} <!-- source: intake §1 + intake §6 — note any value-optimization or new-customer-only settings, e.g. "value optimization on, LTV-weighted" -->), and let product-page copy and price anchoring repel the {{ECOM_ANTI_PATTERN}} <!-- source: avatar research — e.g. "coupon-stacker / serial-returner" --> pattern before the click converts.
<!-- /MODEL -->

---

## How the avatars map to production

<!-- MODEL: lead-gen -->
| Avatar | Landing slug | Priority | First formats |
|---|---|---|---|
| {{AVATAR_ID}} {{AVATAR_SHORT_NAME}} | `/{{LANDING_SLUG}}` <!-- source: intake §6 + PRD --> | {{PRIORITY_RANK}} <!-- source: intake §1 — rank by value × evidence strength × asset readiness --> | {{FIRST_FORMATS}} <!-- source: intake §3 — statics, founder Q&A video, UGC, VSL — constrained by available creative faces --> |
<!-- one row per avatar; priority 1 = first budget -->
<!-- /MODEL -->

<!-- MODEL: app -->
| Avatar | Store/landing angle | Priority | First formats |
|---|---|---|---|
| {{AVATAR_ID}} {{AVATAR_SHORT_NAME}} | {{STORE_ANGLE}} <!-- source: intake §2 + avatar research — the positioning angle for custom store listing / custom product page / web landing --> | {{PRIORITY_RANK}} <!-- source: intake §1 --> | {{FIRST_FORMATS}} <!-- source: intake §3 — screen-capture demo, UGC hook + demo, statics --> |
<!-- one row per avatar -->
<!-- /MODEL -->

<!-- MODEL: ecom -->
| Avatar | Landing/collection angle | Priority | First formats |
|---|---|---|---|
| {{AVATAR_ID}} {{AVATAR_SHORT_NAME}} | {{PDP_OR_COLLECTION_ANGLE}} <!-- source: intake §2 + PRD — which product/collection page and which angle headline --> | {{PRIORITY_RANK}} <!-- source: intake §1 — margin × evidence × creative readiness --> | {{FIRST_FORMATS}} <!-- source: intake §3 — statics, UGC unboxing/demo, founder story --> |
<!-- one row per avatar -->
<!-- /MODEL -->

Hook quotas and per-avatar creative recipes: `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`. Measurement of per-avatar performance: `../05-measurement/MEASUREMENT.md`. Revisit this doc quarterly — or whenever a new research pass (fresh reviews, new communities, shifted Ad Library patterns) contradicts a dossier field.

---

## RESEARCH SOURCING — where each dossier field comes from

For the Claude instantiating this template. Fill fields only from these sources; when a source is silent, mark the field `(hypothesis — founder interview only)` rather than inventing evidence.

| Dossier field | Primary source | Secondary source |
|---|---|---|
| Avatar name, situation, value note | Interview §2 (avatar hypotheses) + §1 (economics) | Community mining (who's actually asking) |
| Objective call-outs | Interview §2 | Ad Library patterns (what call-outs competitors' long-running ads use) |
| Pains (their words) | Competitor-review mining + community mining | Interview §2 |
| Objections/fears | Competitor negative reviews + community "should I…" threads | Interview §2 (common sales objections) |
| Decision driver | Competitor positive reviews ("why I chose") + community recommendation threads | Interview §2 |
| Anti-avatar signals | Interview §2 (worst-customer answer) + competitor 1-star reviews | Ad Library (angles competitors run that attract complainers) |
| Cross-avatar facts | Interview §1, §5 | All research streams, triangulated |

**EVIDENCE RULE (non-negotiable):** every pain, objection, and decision driver in a dossier must be traceable to (a) a tagged quote in `../01-avatars/language-bank.md`, or (b) an explicit answer from the user interview. If neither exists, the item does not go in the dossier — flag the gap and either do more research or label the avatar as hypothesis-grade in its value note. Never write a plausible-sounding pain the corpus doesn't contain.

---

## Appendix — if you later have customer data

This document was built without customer data. If the business later accumulates a usable customer record (CRM, order history, subscription analytics), upgrade it: rank customers by lifetime value, profile the top ~20% against the rest (traits, sources, tenure, product mix), compute the lift of each trait in the top cohort vs. the rest (a trait at 1.5×+ lift is a call-out candidate; a trait under ~0.5× is an anti-signal), and re-mine any free-text fields for voice-of-customer language. Rebuild each avatar's objective call-outs and value notes from those lifts, keeping the research-sourced language where the data is silent. No tooling for this is included in the plan — it is a future analysis project.
