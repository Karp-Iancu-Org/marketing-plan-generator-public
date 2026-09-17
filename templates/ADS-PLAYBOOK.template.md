<!--
TEMPLATE: ADS-PLAYBOOK.template.md
PURPOSE: The standing operating rules for running paid-social ads for {{NICHE}} — account
structure, angle taxonomy, budget tiers, weekly cadence, lead/customer handling, and guardrails.
One-time setup lives in ../06-setup-walkthroughs/. Creative supply comes from
../04-creative-production/CREATIVE-PRODUCTION-SPEC.md. Avatars and language come from
../01-avatars/AVATARS.md.

INPUTS REQUIRED TO INSTANTIATE:
- PRD: niche, business model (lead-gen | app | ecom), ad platform, offer description
- Intake interview: §1 business model & offer economics, §2 avatar hypotheses, §3 creative
  faces, §4 budget, §5 geography/scope, §6 tech stack, §7 compliance
- Avatar research: ../01-avatars/AVATARS.md (avatar call-out attributes, language bank)
- External research: CPM/CPL/CPA benchmarks for the niche and geography

CONVENTIONS: Placeholders are `{{UPPER_SNAKE}}`, annotated with their source at first
occurrence. Keep exactly ONE `<!-- MODEL: ... -->` block per variant point (matching the
business model in the PRD) and delete the others, including the marker comments.

QA CHECKLIST (before delivering the instantiated doc):
- [ ] No `{{...}}` placeholders or `<!-- MODEL -->` / `<!-- source -->` comments remain
- [ ] Exactly one business-model variant kept at each variant point, and it matches the PRD
- [ ] Budget tier row highlighted/selected matches the intake §4 budget
- [ ] Angle taxonomy table filled with niche-adapted angles, not just the generic seeds
- [ ] Planning-economics worksheet computed with real numbers from intake §1 + external research
- [ ] The qualified/valuable event named here matches ../06-setup-walkthroughs/TRACKING-SETUP.md
  and ../05-measurement/MEASUREMENT.md exactly
- [ ] All universal invariants (creative ID, ABO→CBO, broad+CAPI, 70/20/10, volume rule,
  never-edit-live, golden-BB retry, frequency 3.5) preserved verbatim
- [ ] Compliance constraints from intake §7 reflected in guardrails
-->

# Ads Playbook — Operating Rules at {{MONTHLY_BUDGET}} <!-- source: intake §4 -->/Month

The standing rules for running the {{AD_PLATFORM}} <!-- source: PRD --> account for {{BUSINESS_NAME}} <!-- source: PRD -->. One-time setup lives in `../06-setup-walkthroughs/META-ADS-SETUP.md` (do that first). Creative supply comes from `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`. Avatars and language come from `../01-avatars/AVATARS.md`.

## The governing principles

1. **The creative is the targeting.** Broad audiences; each ad calls out ONE avatar with objective attributes plus the emotional pain, in the customer's own words (pull both from `../01-avatars/AVATARS.md`). Generic ads ("{{NICHE}} <!-- source: PRD --> — buy now") attract the anti-avatar (cost-shoppers, poor-fit buyers) as efficiently as they attract anyone.

   


2. **Volume rule: creatives/week ≈ monthly spend / $1,000.** New creatives every week, every week. Creative burns out long before the market saturates — the market is never saturated, the creative is.
3. **Test ABO, scale CBO.** One concept → 5–10 variations → one ABO test ad set. Winners duplicate into the angle's CBO campaign (one CBO campaign per angle).
4. **Optimize ONLY on the qualified/valuable event** — never on a cheap upstream proxy. Feed downstream revenue outcomes back via CAPI (see `../06-setup-walkthroughs/TRACKING-SETUP.md`).

   <!-- MODEL: lead-gen -->
   The optimization event is **`QualifiedLead`** — fired only AFTER the form's qualification gate ({{QUALIFICATION_GATE}} <!-- source: intake §1 -->), never on raw form submit. Mirror closed/won outcomes back via CAPI so the platform learns what a buyer looks like, not just a lead.
   <!-- /MODEL -->
   <!-- MODEL: app -->
   The optimization event is **`trial_started`** or your activation event ({{ACTIVATION_EVENT}} <!-- source: intake §1 -->) — **NOT install**. Installs are the cheap proxy that trains the algorithm on tire-kickers. Mirror `subscription_started` / paid conversions back via CAPI.
   <!-- /MODEL -->
   <!-- MODEL: ecom -->
   The optimization event is **`Purchase` with value passed** — not ATC, not InitiateCheckout. Pass real order values so the platform optimizes for revenue, and mirror server-side purchases via CAPI to close the signal gap.
   <!-- /MODEL -->

5. **Never retire a winner out of boredom.** New customers see it for the first time every day; they're owed the highest-converting ad.

## Account structure

```
TEST | ABO | {{NICHE}}                       ← all testing, one campaign, budget per ad set
SCALE | CBO | <Angle 1>                      ← one CBO campaign per proven angle
SCALE | CBO | <Angle 2>
SCALE | CBO | <Angle 3>                      ← activates as capture systems produce material
RETARGET | Engagement + Site Visitors        ← small always-on
```

**Naming discipline (invariant):** creative ID `A#-H#-M#-C#-v#` (Avatar-Hook-Meat-CTA-version) = ad name = `utm_content`. This is the join key for all measurement (`../05-measurement/MEASUREMENT.md`).

## Angle taxonomy (fill in per {{NICHE}})

Seed with the four generic angles below, then adapt: rename each to the niche's version, add niche-specific angles suggested by `../01-avatars/AVATARS.md`, and delete any that genuinely can't apply. Statics launch first — cheapest to produce at volume.

| # | Angle (generic seed) | Adapted for {{NICHE}} | Format | Production cost | Launch order |
|---|---|---|---|---|---|
| 1 | **Static avatar call-outs** — image + text calling out one avatar/segment/pain | {{ANGLE_1_ADAPTED}} <!-- source: avatar research --> | Static image | Lowest | First |
| 2 | **Founder/expert talking-head** — 30–90s clips: one question, one answer, 3-second self-ID opening; faces from {{CREATIVE_FACES}} <!-- source: intake §3 --> | {{ANGLE_2_ADAPTED}} <!-- source: avatar research --> | Short video | Low–mid | Second |
| 3 | **Testimonial/proof** — review-screenshot statics, then filmed testimonials and life-cycle ads as `../04-creative-production/CAPTURE-SYSTEMS.md` (companion doc) produces material | {{ANGLE_3_ADAPTED}} <!-- source: avatar research --> | Static → video | Low (statics) | As material arrives |
| 4 | **Faceless education** — text-slideshow/whiteboard explainers on the niche's most-misunderstood question | {{ANGLE_4_ADAPTED}} <!-- source: avatar research --> | Slideshow/VO | Low | Optional, later |

## Budget tiers

Pick the row matching {{MONTHLY_BUDGET}}; the whole playbook scales along this table. The wild budget lives *inside* the testing bucket — it is deliberately expected to lose; it's where new super-winners come from.

| Monthly spend | New creatives/week (≈ spend/$1,000) | Concurrent test ad sets (ABO) | Angle CBOs | Testing % | Scaling % | Retargeting % | Wild % (inside testing) |
|---|---|---|---|---|---|---|---|
| **<$5K** | 2–5 | 1–2 | 1–2 | ~35% | ~50% | ~5% | ~10% |
| **$5–10K** | 5–10 | 3–5 | 2–3 | ~30% | ~55% | ~5% | ~10% |
| **$10–25K** | 10–25 | 5–8 | 3–4 | ~25% | ~60% | ~5% | ~10% |
| **$25K+** | 25+ | 8–12 | 4–6 | ~20% | ~65% | ~5% | ~10% |

Test ad sets run at roughly $20–40/day each at the lower tiers; scale proportionally above $10K.

## Planning economics (fill-in worksheet — validate in month 1–2)

Work backwards from unit economics before spending a dollar:

| Line | Value | Source |
|---|---|---|
| CPM assumption for {{NICHE}} in {{GEO_SCOPE}} <!-- source: intake §5 --> | {{CPM_ASSUMPTION}} <!-- source: avatar research --> | External benchmark research |
| Price point / average order value | {{PRICE_POINT}} <!-- source: intake §1 --> | Intake §1 |
| Average customer value (LTV or first-year) | {{AVG_CUSTOMER_VALUE}} <!-- source: intake §1 --> | Intake §1 / revenue system |
| Target CAC (must clear margin at {{PRICE_POINT}}) | {{TARGET_CAC}} <!-- source: intake §1 --> | Intake §1 |
| Expected conversion rate, qualified event → paying customer | {{QUALIFIED_TO_CUSTOMER_RATE}} <!-- source: intake §1 --> | Intake §1 / analogs |
| **Derived target cost-per-qualified-event band** | {{TARGET_CPL_BAND}} = {{TARGET_CAC}} × {{QUALIFIED_TO_CUSTOMER_RATE}} | Computed |
| Expected qualified events/month at {{MONTHLY_BUDGET}} | {{MONTHLY_BUDGET}} ÷ band midpoint | Computed |

Treat a cost-per-qualified-event *well under* the band as suspicious (check event quality / tracking routing) rather than as victory. Identify the downstream constraint the ads will hit first (sales capacity, onboarding capacity, fulfillment/inventory) and watch it deliberately — the constraint is rarely the ad math.



## Weekly operating cadence (one owner, same day weekly)

1. **Ship the tier's creative quota** into the TEST campaign, mixed per **70/20/10**:
   - ~70%: minimal variations of current winners (new opening 2 seconds, different segment call-out, different quote, same script different speaker/wardrobe/background).
   - ~20%: adjacent (new hook on a proven meat, new testimonial, new format for a proven message).
   - ~10%: wild new concepts.
2. **Judge last week's tests** (3–5 days / ~$60–100 spent per ad): winners → duplicate into the angle CBO; losers → off. A believed-in flop gets ONE **golden-BB retry**: kill it, re-upload the identical creative into a fresh ad set, give it 2–3 days — once, never more.
3. **Tend scale campaigns:** budget nudges ≤20% every 2–3 days on winners; **frequency >3.5 = fatigue** → rotate in fresher variations; cost per qualified event >50% above target for a week → replace.
4. **Check the funnel behind the ads:** platform event health, landing/store/app-listing dry-run monthly, and the response SLAs below.
5. **Log the week** per `../05-measurement/MEASUREMENT.md`.

## Retargeting (small, always-on)

Audiences: website/app visitors 180 days, video viewers 25%+, social engagers 365 days, plus **customer-list lookalike** (upload the paying-customer list; refresh quarterly). Serve the strongest proof assets (review compilations, expert Q&A, "what happens next" explainer). Broad + optional lookalikes can be layered on scale campaigns too — lookalikes don't conflict with the broad doctrine.

## Response systems — the part the ad platform can't fix

Ads only pay if the seconds and days after the click are engineered. Non-negotiable:

<!-- MODEL: lead-gen -->
**Speed-to-lead SLAs:**
- **Call within 60 seconds** of form submit during business hours (staff or an answering service must cover this; after-hours leads get first call before 9am next day).
- **Cadence for unreached leads: double-dial + text, 2×/day for days 1–3, then 1×/day through day 7**, then into the nurture/retarget list. Benchmark to beat: 80% reached within 3 days.
- **Book the sales conversation within 3 days**, not "next opening in two weeks."
- **Day-before confirmation** email/text: "we've reserved this time for you."
- **Pre-call VSL or prep asset sent at booking**, with an enforcement script at call start.
- **Lead scoring:** route by the qualification answers — top-scored leads go to the strongest closer's calendar first. Best leads → best closer.
<!-- /MODEL -->
<!-- MODEL: app -->
**Activation SLAs:**
- **Onboarding push/email sequence fires within minutes of signup** — the first session is the sale.
- **Day-1 activation nudges:** if the user hasn't hit {{ACTIVATION_EVENT}} within 24 hours, trigger the guided path (push + email + in-app prompt) pointing at the single next action.
- **Days 1–7 sequence:** one value-demonstrating touch per day until activation, then switch to the habit/retention track.
- **Trial-end save flow:** reminder before trial expiry with the strongest proof asset; downgrade/win-back path for non-converters.
- **Score signups** by acquisition creative and onboarding behavior; route high-intent cohorts to high-touch onboarding (or sales assist) where the price point justifies it.
<!-- /MODEL -->
<!-- MODEL: ecom -->
**Purchase-flow SLAs:**
- **Abandoned-cart flow:** first touch within 1 hour, sequence over days 1–3 (reminder → objection-handling proof → incentive last).
- **Abandoned-browse and abandoned-checkout** get their own lighter flows.
- **Post-purchase flow:** immediate confirmation + expectation-setting, shipping/usage touches, then the review/UGC ask timed to {{PRODUCT_AHA_MOMENT}} <!-- source: intake §1 --> (feeds `CAPTURE-SYSTEMS.md`).
- **Repeat/replenishment trigger** timed to product usage cycle; winners here lift LTV and therefore the affordable CAC.
<!-- /MODEL -->

## Kill-criteria and guardrails

- Account spending limit set at the monthly ceiling (`../06-setup-walkthroughs/META-ADS-SETUP.md`).
- Any week downstream quality collapses → dry-run the tracking routing same day (the usual culprit: the qualified/unqualified event split breaking, which silently retrains the pixel on everyone).
- **Never edit a live ad** (resets learning) — duplicate, change, launch, kill the old one.
- No interest targeting, no "helpful" audience narrowing beyond geography ({{GEO_SCOPE}}).
- Creative fatigue is the default explanation for *slow* cost drift; funnel breakage is the default explanation for *sudden* cost cliffs (in either direction).
- Every ad and claim complies with {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 --> rules before launch.

## Escalation path (when the current tier is working)

Raise spend only when: cost per qualified event stable in band ≥3 weeks, response SLAs holding, downstream capacity absorbing volume. Then +20–30%/month — and creative volume scales with it (re-derive the volume rule: creatives/week ≈ spend/$1,000), moving down the budget-tier table as you go.
