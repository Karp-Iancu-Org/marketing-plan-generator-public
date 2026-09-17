<!--
TEMPLATE: MEASUREMENT.template.md
PURPOSE: The KPI set and feedback loop for the {{NICHE}} marketing system — commercial
metrics only, a funnel KPI table, the per-creative join that ties spend to revenue, an
operating cadence, and honest-measurement guardrails.

INPUTS REQUIRED TO INSTANTIATE:
- PRD: niche, business model (lead-gen | app | ecom), ad platform
- Intake interview: §1 business model & offer economics (value benchmarks, close-rate
  expectations), §4 budget, §6 tech stack (CRM/analytics, revenue system)
- Avatar research: cohort value benchmarks if available
- The instantiated ADS-PLAYBOOK.md and ../06-setup-walkthroughs/TRACKING-SETUP.md (event
  names and target bands must match across all three docs)

CONVENTIONS: Placeholders are `{{UPPER_SNAKE}}`, annotated with their source at first
occurrence. Keep exactly ONE `<!-- MODEL: ... -->` block per variant point (matching the
business model in the PRD) and delete the others, including the marker comments.

QA CHECKLIST (before delivering the instantiated doc):
- [ ] No `{{...}}` placeholders or `<!-- MODEL -->` / `<!-- source -->` comments remain
- [ ] Exactly one model variant kept in the funnel table, matching the PRD
- [ ] Every KPI target band filled with a real starting number (marked "v1 — revise after month 2")
- [ ] Qualified/valuable event name identical to ADS-PLAYBOOK.md and TRACKING-SETUP.md
- [ ] The per-creative join names the client's actual systems ({{CRM_OR_ANALYTICS}}, {{REVENUE_SYSTEM}})
- [ ] Creative-ID/utm_content convention preserved verbatim
- [ ] All honest-measurement guardrails present
-->

# Measurement — KPIs and the Feedback Loop

**Doctrine: commercial metrics only.** Views, likes, and followers are explicitly rejected ("3× views up = 3× revenue down" is a real failure mode); the leading indicator for organic is **saves**, and everything paid is judged on **qualified** cost metrics all the way down to revenue.

## Funnel KPIs (weekly)

## Stage definitions and assumptions

| Stage | Model-appropriate definition | Owner / source of truth | Assumption or confirmed evidence |
| --- | --- | --- | --- |
| Contactable | {{CONTACTABLE_STAGE_DEFINITION}} <!-- source: intake §1A.4 --> | {{CONTACTABLE_OWNER}} | {{CONTACTABLE_EVIDENCE_STATUS}} |
| Engaged | {{ENGAGED_STAGE_DEFINITION}} <!-- source: intake §1A.4 --> | {{ENGAGED_OWNER}} | {{ENGAGED_EVIDENCE_STATUS}} |
| Qualified / valuable | {{QUALIFIED_STAGE_DEFINITION}} <!-- source: intake §1A.4 --> | {{QUALIFIED_OWNER}} | {{QUALIFIED_EVIDENCE_STATUS}} |
| Customer / retained customer | {{RETAINED_CUSTOMER_DEFINITION}} <!-- source: intake §1A.7 --> | {{REVENUE_OWNER}} | {{RETENTION_EVIDENCE_STATUS}} |

Use `contactable → engaged → qualified → customer → retained` only where it matches the model. For lead-gen, add response, scheduled, show, and close stages; for app, activation and paid/retained stages; for ecommerce, purchase and repeat-purchase stages. All targets are assumptions until a named owner validates them.

| Stage | Metric | Source | Target/band (v1 — revise after month 2) |
|---|---|---|---|
| Ad | Spend, CPM, CTR (link), frequency | {{AD_PLATFORM}} <!-- source: PRD --> ads manager / export | CTR ≥1%; **frequency <3.5** (above = fatigue) |
<!-- MODEL: lead-gen -->
| Lead | **Cost per QualifiedLead** (post-qualification-gate event only) | Ads manager (event per `../06-setup-walkthroughs/TRACKING-SETUP.md`) | {{TARGET_CPL_BAND}} <!-- source: intake §1 --> |
| Lead quality | % of QualifiedLeads the sales/intake team rates "real" | intake spot-check | ≥80% |
| Speed | % called within 5 min (business hours) | call log / {{CRM}} <!-- source: intake §6 --> | ≥90% |
| Consult | Cost per booked sales conversation; booking rate from qualified leads | {{CRM}} pipeline | booking ≥40% of qualified |
| Show | Show rate | {{CRM}} / scheduler | ≥75% (pre-call VSL + day-before touch exist to push this) |
| Close | Conversation → customer rate; **cost per customer** | {{CRM}} deal stages (+ CAPI mirror of closed/won) | close {{TARGET_CLOSE_RATE}} <!-- source: intake §1 --> |
| Value | Customer value over time vs cohort benchmarks | {{REVENUE_SYSTEM}} <!-- source: intake §6 --> | vs {{VALUE_BENCHMARKS}} <!-- source: avatar research --> |
<!-- /MODEL -->
<!-- MODEL: app -->
| Install | Cost per install (context only — never optimize on it) | Ads manager / MMP | trend only |
| Activation | **Cost per {{ACTIVATION_EVENT}}** <!-- source: intake §1 --> ; install→activation rate | {{CRM_OR_ANALYTICS}} <!-- source: intake §6 --> | {{TARGET_CPA_BAND}} <!-- source: intake §1 --> ; activation ≥{{ACTIVATION_RATE_TARGET}} |
| Trial | Trial-start rate; cost per trial | {{CRM_OR_ANALYTICS}} | fill per intake §1 |
| Paid | Trial→paid rate; **cost per paying customer (CAC)** | {{REVENUE_SYSTEM}} (+ CAPI mirror of paid conversions) | CAC ≤ {{TARGET_CAC}} <!-- source: intake §1 --> |
| Retention | D30 retention of paid cohorts, by acquisition creative | {{CRM_OR_ANALYTICS}} | ≥{{D30_TARGET}} ; cheap cohorts that churn are expensive cohorts |
<!-- /MODEL -->
<!-- MODEL: ecom -->
| Click | CPC, landing-page view rate | Ads manager | trend only |
| ATC | Add-to-cart rate; cost per ATC (context only — never optimize on it) | Ads manager + store analytics | trend only |
| Purchase | **Cost per Purchase; ROAS (value-based)** | Ads manager + {{REVENUE_SYSTEM}} (server-side/CAPI mirror) | CAC ≤ {{TARGET_CAC}} ; ROAS ≥ {{TARGET_ROAS}} <!-- source: intake §1 --> |
| Repeat/AOV | AOV, repeat-purchase rate, 90-day LTV by acquisition creative | {{REVENUE_SYSTEM}} | AOV ≥ {{AOV_TARGET}} ; LTV pays back CAC within {{PAYBACK_WINDOW}} |
<!-- /MODEL -->
| Organic | Saves per post (primary), plus DMs/inbound attributed | platform insights | trend, not absolute |

## Economics and retention measurements

| Measure | Formula | Owner / system | Assumption and action |
| --- | --- | --- | --- |
| Engaged-lead rate | engaged leads ÷ contactable leads | {{CRM_OR_ANALYTICS}} | {{ENGAGEMENT_RATE_ASSUMPTION}} <!-- source: intake §1A.4 --> |
| Qualified rate | qualified leads/customers ÷ engaged leads | {{CRM_OR_ANALYTICS}} | {{QUALIFICATION_RATE_ASSUMPTION}} |
| Response / show / close rate (lead-gen only) | responses ÷ follow-ups; shows ÷ scheduled; customers ÷ shows | {{CRM}} | {{SALES_RATE_ASSUMPTION}} <!-- source: intake §1A.6 --> |
| CAC | paid acquisition spend ÷ new customers | {{REVENUE_SYSTEM}} | {{CAC_ASSUMPTION}} <!-- source: intake §1/§1A.7 --> |
| Contribution margin | revenue − directly attributable delivery/fulfillment cost | {{REVENUE_SYSTEM}} | {{MARGIN_ASSUMPTION}} |
| LTV | gross profit collected over customer lifespan (state cohort/window) | {{REVENUE_SYSTEM}} | {{LTV_ASSUMPTION}} |
| Retention / repeat | retained customers ÷ eligible cohort; repeat buyers ÷ customers | {{REVENUE_SYSTEM}} | {{RETENTION_ASSUMPTION}}; owner reviews cohort feedback |



## The per-creative join (why naming discipline matters)

**Invariant:** `ad name` = `utm_content` = creative ID `A<avatar>-H<hook>-M<meat>-C<cta>-v<n>`. That single convention makes three systems joinable:

1. **Ad platform export** ({{AD_PLATFORM}} ads manager, or a synced warehouse table) → spend/impressions per ad name.
2. **{{CRM_OR_ANALYTICS}}** → `utm_content` captured at conversion → qualified events and pipeline stages per creative.
3. **{{REVENUE_SYSTEM}}** → eventual customer value per creative (via the contact/customer join).

That chain answers the only creative question that matters: **which hook × meat × avatar prints revenue** — which then drives the 70/20/10 allocation and tells creative production what to make more of. Automate the join when volume justifies it; until then it's a monthly manual pull.

## Cadence

- **Weekly (30 min, same session as the ads ops):** fill one row per creative in a running sheet (spend, cost per qualified event, qualified events, next-stage conversions). Kill/scale decisions per `ADS-PLAYBOOK.md`.
- **Monthly (1 hr):** cost per customer by avatar and by angle; quality spot-check with the team that touches conversions; landing/store/onboarding dry-run; review whether the qualification bar needs tightening or loosening.
- **Quarterly:** re-run the avatar/segment analysis on fresh customer data; check whether avatar lifts have shifted; refresh the customer-list lookalike; revisit cost bands with real data; feed new customer language from the "Why People Buy" loop (`../04-creative-production/CAPTURE-SYSTEMS.md`) into the language bank in `../01-avatars/AVATARS.md`.

## Honest-measurement guardrails

- **A sudden cost *improvement* with worse downstream quality = the tracking gate broke** (dry-run immediately). Suspiciously cheap leads/events mean the qualification gate is misfiring and silently retraining the pixel on everyone. Cheap bad leads are the expensive kind.
- **Don't judge any creative on <$60 spend or <3 days.**
- Keep ONE attribution truth source for "where customers come from" — a first-touch source field maintained in {{CRM_OR_ANALYTICS}} — and distrust auto-populated source fields known to be polluted by imports. For paid specifically, trust the `utm_content` chain above.
- **When spend scales, re-derive the volume rule: creatives/week ≈ spend/$1,000** — the measurement sheet grows with it.
