# Intake Questionnaire

The complete question set for generating a marketing plan. **Do not ask everything** — first extract what the PRD already answers (see `GENERATOR.md` step 1), then ask only the gaps, batched into 3–4 `AskUserQuestion` rounds of related questions. Every question lists: what to extract from the PRD, the fallback default, and which templates consume the answer.

Section numbers (§1–§8) are the reference used by `<!-- source: intake §N -->` comments throughout `templates/`.

---

## §1 Business model & offer economics

| # | Question | PRD extraction hint | Default if unanswered | Feeds |
|---|---|---|---|---|
| 1.1 | Which model fits: **lead-gen/service** (humans close sales), **app/self-serve** (users sign up and pay in-product), or **ecommerce** (cart checkout)? Hybrids: pick the one paid ads must drive. | product description, revenue section | — (must answer; drives every MODEL variant) | all templates |
| 1.2 | What is the core offer and price point? (subscription price, service fee range, AOV) | pricing section | — (must answer) | strategy, playbook economics, creative spec |
| 1.3 | Estimated customer lifetime value (rough is fine: price × expected months, or average total fees) | LTV/retention notes | 3× first purchase/month | playbook economics, measurement |
| 1.4 | What does the sales motion look like between lead and money? (lead-gen: consult/demo/quote? app: trial length, paywall placement? ecom: single product vs catalog?) | funnel/UX flows | model-typical (14-day trial / free consult / single-product page) | strategy funnel, tracking, capture |
| 1.5 | Target CAC or acceptable cost per customer, if known | unit economics | back out as ≤⅓ of LTV | playbook economics |
| 1.6 | Is there a cheaper front-end/bridge offer, or could one exist? (the workshop's self-liquidating front-end lesson) | pricing tiers | none yet — flag as strategy option | strategy |

## §2 Avatar hypotheses (seeds research — answers here are hypotheses, verified in the research phase)

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 2.1 | Who do you *believe* the 2–4 best customer types are? (role/life situation, not demographics alone) | target-user/persona section | derive from research alone | AVATARS |
| 2.2 | What are the top 3 pains each type would say **in their own words**? | problem statement | research-derived | AVATARS, language bank |
| 2.3 | What objections stop people from buying/signing up? | risks/competition section | research-derived | language bank, VSL content |
| 2.4 | Who should we **stop attracting**? (the customer that churns, refunds, price-shops, or costs more than they pay) | non-goals section | research-derived anti-avatar | AVATARS anti-avatar |
| 2.5 | Where do these people already gather online? (subreddits, FB groups, forums, competitor followings) | market section | researcher discovers | research phase, language bank |
| 2.6 | Name 3–5 direct competitors (for review mining + Meta Ad Library pulls) | competition section | researcher discovers | research phase |
| 2.7 | What objective, ad-nameable attributes mark the best customers? (owns X, role Y, life stage Z, spends on W) | persona details | derived from research | AVATARS call-outs, qualification gate |

## §3 Creative faces & talent

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 3.1 | Who can be on camera regularly? (founder / team member(s) / hired spokesperson / nobody) | — | recipe-book-for-all: spec every format, faceless-first until talent confirmed | creative spec, capture |
| 3.2 | Are customers reachable and plausibly willing to give testimonials? Any privacy sensitivity in this niche? | user base description | testimonials assumed possible with consent ladder | capture systems |
| 3.3 | Does existing footage/content exist? (YouTube, podcast, webinars, demos) | marketing/assets section | none — plan the monthly shoot | creative spec §5 |

## §4 Budget

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 4.1 | Monthly paid budget tier: <$5K / $5–10K / $10–25K / $25K+ | budget section | $5–10K | playbook tiers, volume targets |
| 4.2 | Is the budget fixed or scalable if CAC proves out? | — | scalable on proof | playbook escalation path |

## §5 Geography & scope

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 5.1 | Geographic scope: local (radius/metro) / regional / national / international? | market section | app & ecom: national; service: metro | ad-set locations, avatar call-outs |
| 5.2 | Any languages beyond English? | — | English only | creative spec |

## §6 Tech stack

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 6.1 | CRM / customer database? ({{CRM}}) | tech section | model default: HubSpot-free assumption; capture in doc as "chosen at setup" | tracking CAPI, playbook |
| 6.2 | Landing/site platform? App: iOS/Android/both? Ecom: platform (Shopify etc.)? | tech stack | chosen at setup | landing walkthrough, tracking |
| 6.3 | Existing Meta assets? (Business Portfolio, pixel, ad account history, Page/IG) | — | assume none — full setup walkthrough applies | Meta setup |
| 6.4 | App model only: is an MMP (AppsFlyer/Adjust) or the Meta SDK integrated? | tech stack | none — tracking doc prescribes the choice | tracking |
| 6.5 | Booking/scheduling tool (lead-gen) or trial/checkout flow owner (app/ecom)? | — | chosen at setup | landing, funnel |

## §7 Compliance domain

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 7.1 | Does the niche touch a regulated claims domain? (legal, health/medical, financial, housing, employment, credit, political) | domain description | none | creative QA gate, Meta special-category flag, strategy risks |
| 7.2 | Any industry ad rules or platform restrictions known? (e.g., bar advertising rules, HIPAA-adjacent, financial disclaimers) | — | generator researches the domain's basics and lists them in the QA gate | creative spec QA |

## §8 Capture opportunities

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 8.1 | What already happens in the business that could be filmed/recorded? (calls, onboarding, delivery, support, events) | operations section | model-typical list proposed by generator | capture systems |
| 8.2 | Are sales/support conversations recorded today (or recordable)? | — | recommend starting | capture §2 "Why People Buy" loop |
| 8.3 | Where does customer praise already accumulate? (reviews site, app store, DMs, emails) | traction section | researcher locates | capture, language bank |

## §9 Organic social scope

| # | Question | PRD hint | Default | Feeds |
|---|---|---|---|---|
| 9.1 | Which organic channels are **already handled or out of scope**? (e.g., SEO/Google Business Profile managed separately, an agency runs LinkedIn) The organic-social plan covers only what's in scope. | marketing/assets section | everything in scope | organic strategy scope note |
| 9.2 | Which social platforms are already active, and roughly how do they perform? (follower counts irrelevant — ask about posting cadence and any posts that produced customers) | traction section | none active — start fresh | organic strategy platform priorities, playbook |
| 9.3 | What posting cadence can the business sustain **for a full year**? (the corpus's cadence rule: a modest pace held for 12 months beats a heroic month) | — | 5 posts/week rising with automation | playbook cadence, production quotas |
| 9.4 | Who owns the weekly organic ritual (scoring, scheduling, outlier promotion)? | team section | same owner as the paid ads ops | playbook §6, production roles |

---

## Asking protocol

1. Batch related gaps: typically Round 1 = §1+§4 (model & money), Round 2 = §2 (avatar hypotheses), Round 3 = §3+§8+§9 (faces, capture & organic scope), Round 4 = §5+§6+§7 (scope, stack, compliance). Skip any round fully answered by the PRD.
2. Use `AskUserQuestion` with concrete options + "Other"; put the recommended default first, labeled "(Recommended)".
3. Record every answer (and every default taken) in the generated plan's `intake-record.md` — templates cite `intake §N`, and the record is the audit trail.
4. §2 answers are hypotheses: the research phase must confirm or correct them with evidence before the avatar checkpoint. If research contradicts the user's hypothesis, present the contradiction at the checkpoint — don't silently override.
