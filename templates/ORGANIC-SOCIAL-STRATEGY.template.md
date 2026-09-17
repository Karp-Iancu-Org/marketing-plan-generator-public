<!--
TEMPLATE: ORGANIC-SOCIAL-STRATEGY.template.md
PURPOSE: The spine of the organic-social half of the plan — why organic social,
  the interest-media thesis, content pillars, the organic→paid flywheel coupling,
  platform priorities, phased rollout, exclusions, and risks. The paid strategy
  (MARKETING-STRATEGY) and this doc describe ONE system with two engines; this
  doc must never contradict the paid spine — it extends it.
INPUTS:
  - The generated 02-strategy/MARKETING-STRATEGY.md (position, avatars, funnel)
  - Intake §3 (faces), §8 (capture), §9 (organic scope, active platforms,
    sustainable cadence, ritual owner)
  - Avatar research (../01-avatars/AVATARS.md, language-bank.md)
  - Lessons corpus: 02 (interest media, saves, capture-don't-manufacture),
    03 (organic→paid flywheel, CPM economics, brand lowers CAC),
    06 (cadence rules, people-follow-people, brand guidelines),
    09 (clipping pipeline volume benchmarks)
GENERATOR ACTIONS:
  1. Fill every {{PLACEHOLDER}} from the source noted in its comment.
  2. Keep exactly ONE `<!- - MODEL: ... - ->` variant per variant point; delete
     the others including markers.
  3. Rewrite or delete the worked-example blockquotes for the client's niche.
  4. Order platform priorities for THIS niche/audience (the template's order is
     a lead-gen-local default) and honor the §9.1 scope exclusions explicitly.
QA CHECKLIST:
  [ ] No {{...}} placeholders or source comments remain; one MODEL variant per point.
  [ ] Scope note names what is explicitly OUT of scope (§9.1), even if "nothing."
  [ ] Pillar allocation sums to ~100% and the education pillar dominates.
  [ ] The flywheel diagram's boxes all correspond to docs that exist in the plan.
  [ ] Cadence numbers match §9.3 (sustainable-for-a-year), not aspiration.
  [ ] The "NOT doing" list includes vanity metrics and trend-chasing.
  [ ] Compliance risk names the client's real regulatory regime (§7).
-->

# {{BUSINESS_NAME}} <!-- source: PRD --> — Organic Social Strategy ({{FOCUS_NICHE}}-First) <!-- source: intake §5 -->

The organic-social companion to `../02-strategy/MARKETING-STRATEGY.md`. Same avatars, same positioning, same anti-avatar — different engine. The paid plan buys attention; this plan **earns it and compounds it** on {{IN_SCOPE_PLATFORMS}} <!-- source: intake §9.1/§9.2 — the social platforms in scope -->. Scope note: {{ORGANIC_SCOPE_NOTE}} <!-- source: intake §9.1 — what is explicitly excluded and why (e.g., "SEO/Google Business Profile is out of scope — already performing, managed separately"), or "all organic channels are in scope" -->. The paid and organic engines are one system (lesson 03: "It used to be two different systems. It's one system now. One team, one approach.").

## Why organic social

- {{ORGANIC_EVIDENCE_BULLET}} <!-- source: avatar research / intake — the strongest niche-specific evidence that organic discovery reaches the best customers: attribution data, community behavior, competitor organic presence. If no data exists, state the hypothesis honestly and mark it for validation. -->
- **Brand is the only thing that lowers CAC over time** (lesson 03). Every month of avatar-true organic content makes the paid dollar cheaper.
- **CPM math:** an organic post reaching 1,000–3,000 of the right viewers is worth $15–75 in equivalent ad spend — per post, at zero media cost (lesson 03 §4).
- **Organic is the free creative-testing lab for paid.** The $100M book-launch lesson: 4,000 scripted ads all lost to organic clips with one appended CTA line. Every organic outlier becomes a pre-validated ad for the {{MONTHLY_AD_BUDGET}} <!-- source: intake §4 -->/month paid budget.



## The operating thesis: interest media

The algorithm distributes by interest, not follower count — **the content is the targeting**, exactly as the creative is the targeting on paid (lessons 02, 03). Consequences:

1. **Follower count is irrelevant.** A page with 800 followers can reach everyone in {{POND}} <!-- source: strategy doc --> who consumed {{NICHE_TOPIC}} <!-- source: PRD --> content this month. (Proof set, lesson 02: $6.5M on 5,000 followers; $1M/yr on 8,000.)
2. **Niche depth beats reach.** {{POND_MATH}} <!-- source: intake §5 + research — the size of the actual buying pool per year/month, and why owning it needs thousands of right viewers, not millions of any viewers -->
3. **The leading KPI is saves.** {{SAVE_BEHAVIOR_RATIONALE}} <!-- source: avatar research — why this niche's buyer saves content before acting (private research, long consideration, comparison shopping) -->. A save is pre-intent. Views, likes, and followers are explicitly not business metrics (the 2024 ACQ failure: 3× views up = 3× revenue down).

## The four content pillars (allocation target)

| Pillar | Share | What it is | Feeds |
|---|---|---|---|
| **P1 Education** (save-engineered) | ~60% | {{EDUCATION_PILLAR_SCOPE}} <!-- source: avatar research — the niche-specific questions, checklists, process explainers, and myth-busts mapped to the avatars --> | Saves, search authority; the say-do "Martha Stewart" trust engine (lesson 03 SPCL: power + credibility) |
| **P2 Proof** | ~25% | {{PROOF_PILLAR_SCOPE}} <!-- source: intake §8 + capture systems — reviews, testimonials, customer-story retells, before/afters, life-cycle material as capture produces it --> | The skeptic's bridge; direct outlier→paid candidates |
| **P3 People / brand** | ~10% | {{PEOPLE_PILLAR_SCOPE}} <!-- source: intake §3 — the faces, entity-trust framing, behind-the-scenes capture; many faces, one front door --> | Likeness + key-person insurance (the boy-band effect, lesson 06) |
| **P4 Timely / reasons-for-new** | ~5% | {{TIMELY_PILLAR_SCOPE}} <!-- source: strategy doc "NEW" wrappers + any referral-source interview play (lesson 02 §8 podcast play) --> | Offers to the most-aware; referral edification |

Every pillar respects the anti-avatar rule: nothing that appeals on {{ANTI_DRIVER}} <!-- source: avatar research — usually cheap/fast/easy -->, ever. And 95%+ of content stays niche-relevant — even charming off-avatar content is a liability (the protein-bomb lesson, 02 §6).

## The flywheel (how organic couples to everything else)

```
{{VOICE_OF_CUSTOMER_HARVEST}} (CAPTURE-SYSTEMS §2)   <!-- source: capture doc — the recorded-conversation/review harvest for this niche -->
  → question backlog in the avatars' own words
    → monthly on-camera shoot (the same shoot the paid plan schedules)
      → clipping pipeline → 20–30 posts/month at near-zero marginal cost
        → post at sustainable volume, CTA on everything
          → weekly outlier check (≥3× trailing-30-day median saves/engagement)
            → outlier + one appended CTA line → paid (ORG- prefix)
              → customers → reviews/testimonials → new proof content → repeat
```

The paid and organic plans share the shoot, the avatars, the language bank, the capture systems, and the measurement join. Organic adds zero new on-camera obligations beyond what the paid plan already schedules.

## Platform priorities

{{PLATFORM_PRIORITIES}} <!-- source: intake §9 + niche judgment. Order by (a) where the paid budget runs (tightest flywheel coupling), (b) search shelf life, (c) redistribution-only channels. Lead-gen-local default: 1. Facebook+Instagram (organic posts are literal ad candidates — Meta can promote the post keeping social proof), 2. YouTube (question-titled mid-form + Shorts; shelf life in years), 3. TikTok (Shorts redistribution only until data earns bespoke effort). App default: TikTok/IG Reels first (install intent), YouTube Shorts, then FB. Ecom: IG+TikTok first (product demo native), YouTube, FB. B2B: LinkedIn first, YouTube, then the rest. -->

Cadence rule (lesson 06): **a pace sustainable for a year beats the hero month.** Start at {{STARTING_CADENCE}} <!-- source: intake §9.3 -->; scale toward {{TARGET_CADENCE}} <!-- source: production pipeline capacity --> only as the automation carries the load.

## Phased rollout

**Phase A (weeks 1–4) — Foundation.** Brand guidelines + anonymous internal brand survey (lesson 06 prerequisites). {{VOICE_OF_CUSTOMER_HARVEST}} running → first question backlog. First monthly shoot (shared with paid) → first ~20 posts from existing material ({{EXISTING_MATERIAL}} <!-- source: intake §3.3/§8.3 — reviews corpus, old footage, support threads -->). CTA doctrine live on every post.
**Phase B (months 2–3) — Volume.** Clipping pipeline online (`ORGANIC-PRODUCTION-PIPELINE.md`) → cadence rises without added on-camera time. {{SHELF_LIFE_CHANNEL}} <!-- source: platform priorities — usually YouTube --> seeded with question-titled mid-forms. First outliers promoted to paid. Saves scorecard running monthly.
**Phase C (months 4–12) — Compounding.** Testimonial/life-cycle material enters the mix as capture matures. {{P4_PLAY}} <!-- source: pillar table — e.g. the referral-source interview show --> launches. Repost winners on schedule until decay. Quarterly: refresh the question backlog from the harvest; re-check pillar allocation against attributed {{DOWN_FUNNEL_EVENT}} <!-- source: strategy doc -->.

## What we deliberately are NOT doing

- No trend-chasing or entertainment formats disconnected from the niche — entertainment is consumed; education changes behavior (lesson 02 §4).
- No follower-growth campaigns, giveaways, or engagement bait. Followers are not the mechanism.
- No posting cadence the team can't sustain for 12 months.
- No lazy CTAs — organic content gets full CTAs too (lesson 02 §15).
- No {{BRAND_SAFETY_EXCLUSIONS}} <!-- source: intake §7 + lesson 06 association guardrails — the niche's specific never-post list (political/cultural content on brand channels, competitor disparagement, regulated-claims violations) -->.

## Risks & watch items

- **The hero-move collapse** is the #1 organic failure mode: a heroic month then silence. Mitigation: the pipeline makes recording the only human production step; quotas are set to the automation's capacity, not enthusiasm.
- **Key-person risk:** one camera-natural person becomes the brand. Mitigation: entity-trust language everywhere, multiple faces from the start (intake §3), spokesperson lane specced in the creative spec.
- **Compliance — {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 -->:** the regime applies to organic posts exactly as to ads. Same QA gate as paid assets, every post.
- **Vanity drift:** the moment reporting includes views or follower counts, the 2024 failure restarts. `MEASUREMENT-ORGANIC.md` defines the only numbers that appear in reviews.
