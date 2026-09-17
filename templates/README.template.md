<!--
TEMPLATE: README.template.md
PURPOSE: The front door of the generated marketing plan — what the plan was
  built from, the scope decisions that bound it, a map of every folder, the
  one-paragraph strategy, and the handoff note for the downstream
  asset-production project.
INPUTS:
  - PRD (business name, offer, model)
  - Intake interview (§1 business model & offer economics, §2 avatar hypotheses,
    §3 creative faces, §4 budget, §5 geography/scope, §6 tech stack,
    §7 compliance, §8 capture opportunities)
  - Avatar research (data sources, snapshot provenance)
  - The lessons corpus (generator `lessons/`) — the doctrine source; note it
    ships in the generator package, NOT in the generated plan folder
GENERATOR ACTIONS:
  1. Fill every {{PLACEHOLDER}} from the source noted in its comment.
  2. Keep exactly ONE `<!- - MODEL: ... - ->` variant block per variant point
     (lead-gen | app | ecom) and delete the others, including the markers.
  3. Rewrite or delete the worked-example blockquote.
  4. Date the scope-decisions block with the generation date.
QA CHECKLIST (run before delivery):
  [ ] No {{...}} placeholders or `<!- - source: ... - ->` comments remain.
  [ ] Exactly one business-model variant survives; no MODEL markers remain.
  [ ] Every folder named in the Map table exists in the generated plan and
      contains the files the row describes.
  [ ] Scope decisions match the intake answers verbatim (budget, cadence,
      focus, formats, data provenance).
  [ ] The one-paragraph strategy agrees with 02-strategy/MARKETING-STRATEGY.md
      (same avatars, same engines, same optimization event).
  [ ] The downstream-project handoff names the correct requirements doc.
-->

# {{BUSINESS_NAME}} <!-- source: PRD --> Marketing Plan

Built from two inputs: the **lessons corpus** (generator `lessons/`, `01..09.md` + `INDEX.md` — the doctrine every rule in this plan cites) and the business's **own customer data** ({{DATA_SOURCES_SUMMARY}} <!-- source: intake §6 + avatar research — the systems and datasets mined: CRM(s), analytics, surveys, reviews, support logs, with record counts -->).

Scope decisions (made {{GENERATION_DATE}} <!-- source: generation run date -->):

- **{{FOCUS_DECISION}}** <!-- source: intake §5 + avatar research — the niche-first scope call and why: which segment/offer/geography the plan targets, where the data is deepest; note that expansion paths live in the strategy doc -->
- **Ad budget: {{MONTHLY_AD_BUDGET}} <!-- source: intake §4 -->/month** → ~{{WEEKLY_CREATIVE_TARGET}} <!-- source: intake §4 --> new creatives/week, isolated-budget testing + consolidated-budget angle campaigns on {{PRIMARY_AD_PLATFORM}} <!-- source: intake §4/§6 -->.
- **Creative formats: {{FORMAT_SCOPE}}** <!-- source: intake §3 + §8 — which format recipes are in scope (on-camera faces, customer testimonial, faceless/static, spokesperson) and which capture systems start immediately because their footage takes months to accumulate -->
- **Avatar analysis uses the {{DATA_SNAPSHOT_REF}} <!-- source: avatar research — snapshot name/date and the script or query that regenerates it on demand --> data snapshot.**

## Map

| Folder | What it holds | Read it when |
|---|---|---|
| `01-avatars/` | `AVATARS.md` (the avatar dossiers), `language-bank.md` (verbatim customer language for hooks), plus the segment numbers and raw voice-of-customer exports | Writing any ad, hook, script, or landing page |
| `02-strategy/` | `MARKETING-STRATEGY.md` — the overall strategy and phased rollout | Deciding what to do next quarter |
| `03-ads/` | `ADS-PLAYBOOK.md` — campaign structure, budgets, qualification, nurture | Running the ad account week to week |
| `04-creative-production/` | `CREATIVE-PRODUCTION-SPEC.md` — **the handoff contract for the asset-creation project** — plus the capture-system ops to start now | Building the ad-asset factory |
| `05-measurement/` | `MEASUREMENT.md` — KPIs and the data feedback loop into {{MEASUREMENT_STACK}} <!-- source: intake §6 — where the numbers live: CRM, warehouse, dashboard, MMP --> | Weekly/monthly reviews |
| `06-setup-walkthroughs/` | Click-by-click one-time setup: ad account/campaign build, landing page/funnel build, tracking/pixel/server-side events | Doing the one-time setup |
| `07-organic/` | The **organic social** plan ({{ORGANIC_PLATFORM_LIST}} <!-- source: intake §9 — the in-scope platforms; name any §9.1 exclusions -->): `ORGANIC-SOCIAL-STRATEGY.md` (the spine), `ORGANIC-CONTENT-PLAYBOOK.md` (weekly ops per platform), `ORGANIC-PRODUCTION-PIPELINE.md` (capture→clip→post chain), `MEASUREMENT-ORGANIC.md` (saves-first scorecard) | Running the social channels; feeding pre-validated creative to paid |

> The doctrine behind these rules — the lesson breakdowns and their synthesis — is not copied into this plan. It lives in the generator package as the lessons corpus (generator `lessons/`, `01..09.md` + `INDEX.md`); go there when you want the source of a rule ("why 10 creatives/week?").

## The one-paragraph strategy

<!-- MODEL: lead-gen -->
Modern ad delivery made the creative the targeting: instead of a few generic "{{GENERIC_AD_EXAMPLE}}" <!-- source: PRD — the generic category ad this niche defaults to --> ads, run a high volume of narrow creatives that each call out one avatar and one pain in the avatar's own words, let the platform find the matching pocket of people, and optimize only on **qualified** leads (the pixel fires after a {{QUALIFICATION_GATE}} <!-- source: intake §1 — e.g. "3–5 question form" -->). Feed the machine from two flywheels: (1) organic content posted at volume, with the ~1-in-10 outliers promoted into paid; (2) every customer journey captured at set checkpoints ({{CAPTURE_CHECKPOINTS_SHORT}} <!-- source: intake §8 -->) so every customer eventually produces at least one ad. The avatars and their language come from the business's own highest-value customers — {{AVATAR_LIST_INLINE}} <!-- source: avatar research — the avatar names, comma-separated --> — not from guesswork.
<!-- /MODEL -->
<!-- MODEL: app -->
Modern ad delivery made the creative the targeting: instead of a few generic "{{GENERIC_AD_EXAMPLE}}" <!-- source: PRD --> ads, run a high volume of narrow creatives that each call out one avatar and one pain in the avatar's own words, let the platform find the matching pocket of people, and optimize on **activation** ({{ACTIVATION_EVENT}} <!-- source: intake §1 — the in-app moment that predicts retention -->), not raw installs. Feed the machine from two flywheels: (1) organic content posted at volume, with the ~1-in-10 outliers promoted into paid; (2) every user journey captured at set checkpoints ({{CAPTURE_CHECKPOINTS_SHORT}} <!-- source: intake §8 -->) so every happy user eventually produces at least one ad. The avatars and their language come from the app's own highest-LTV users — {{AVATAR_LIST_INLINE}} <!-- source: avatar research --> — not from guesswork.
<!-- /MODEL -->
<!-- MODEL: ecom -->
Modern ad delivery made the creative the targeting: instead of a few generic "{{GENERIC_AD_EXAMPLE}}" <!-- source: PRD --> ads, run a high volume of narrow creatives that each call out one avatar and one pain in the avatar's own words, let the platform find the matching pocket of people, and optimize on **purchases** (with {{DOWN_FUNNEL_EVENT}} <!-- source: intake §6 — the LTV-qualified event fed back server-side --> fed back server-side so spend chases repeat-buyer economics, not one-off carts). Feed the machine from two flywheels: (1) organic content posted at volume, with the ~1-in-10 outliers promoted into paid; (2) every customer journey captured at set checkpoints ({{CAPTURE_CHECKPOINTS_SHORT}} <!-- source: intake §8 -->) so every customer eventually produces at least one ad. The avatars and their language come from the store's own highest-value customers — {{AVATAR_LIST_INLINE}} <!-- source: avatar research --> — not from guesswork.
<!-- /MODEL -->



## Downstream project

A separate project will build the actual assets (hooks, scripts, statics, video clipping/assembly automation). It should receive **this entire plan folder** and treat `04-creative-production/CREATIVE-PRODUCTION-SPEC.md` plus `07-organic/ORGANIC-PRODUCTION-PIPELINE.md` as its requirements documents, with `01-avatars/` as its raw material.
