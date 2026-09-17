<!--
TEMPLATE: MEASUREMENT-ORGANIC.template.md
PURPOSE: The organic scorecard — saves-first leading indicators, commercial
  signals, the mechanical outlier definition, review cadence, and the join to
  the paid measurement chain. Companion to MEASUREMENT (which owns the paid
  funnel); the two share the manifest/utm join.
INPUTS:
  - ../05-measurement/MEASUREMENT.md (the paid KPIs and the per-creative join)
  - ORGANIC-CONTENT-PLAYBOOK.md (the weekly ritual this scorecard feeds)
  - Intake §6 (attribution stack), §9 (platforms)
  - Lessons: 02 §5 (saves KPI), 02 §6 (the 3×-views/3×-revenue-down warning),
    06 §7 (commercial metrics, not vanity)
GENERATOR ACTIONS:
  1. Fill placeholders; keep one MODEL variant per point; delete markers.
  2. Scorecard rows only for in-scope platforms.
  3. Wire the attributed-conversion row to the client's actual stack (§6).
QA CHECKLIST:
  [ ] Views appear only in the outlier-math note, never as a reported metric.
  [ ] The outlier threshold is a number relative to the account's own median.
  [ ] The attributed row names real systems, not "analytics."
  [ ] Cadence section gives durations and owners.
  [ ] Guardrails include the do-not-judge-early rule and vanity-drift warning.
-->

# Organic Measurement — Saves First, Commercial Signals Always

Companion to `../05-measurement/MEASUREMENT.md` (which owns the paid funnel). Doctrine: **commercial metrics only.** Views, likes, and follower counts are explicitly rejected and never appear in reporting — the 2024 ACQ experiment (3× views up = 3× revenue down, lesson 02 §6) is the standing warning. The leading indicator for educator content is **saves**; the lagging truth is attributed {{DOWN_FUNNEL_EVENT}} <!-- source: strategy — consults/retainers, activations/subscriptions, purchases/LTV -->.

## The scorecard (one row per post, filled at the weekly ritual)

| Metric | Why | Source |
|---|---|---|
| **Saves** (and save rate: saves/1,000 views) | The #1 leading revenue KPI (lesson 02 §5); a save is pre-intent from someone not ready to act | platform insights |
| Shares / sends | Second-order intent ("send it to the friend who needs it") | platform insights |
| **DMs & comments with buying questions** | The commercial signal (lesson 06 §7 — "what got the buying questions") | manual log, weekly |
| Profile visits → link taps | The click toward the funnel | platform insights + UTM |
{{PLATFORM_SPECIFIC_ROWS}} <!-- source: in-scope platforms — e.g. YouTube: watch time + search impressions on question titles (demand validation); LinkedIn: follower-quality spot check for B2B. One row per platform-native commercial signal. -->
<!-- MODEL: lead-gen -->
| **Consults/bookings attributed to organic** | The truth | intake "how did you hear about us" + UTM (`utm_source=organic`, `utm_content=<post-id>`) joined in {{ATTRIBUTION_STACK}} <!-- source: intake §6 --> |
<!-- /MODEL -->
<!-- MODEL: app -->
| **Installs → activations attributed to organic** | The truth | {{MMP_OR_SDK}} <!-- source: intake §6.4 --> attribution + onboarding "where did you find us" survey |
<!-- /MODEL -->
<!-- MODEL: ecom -->
| **Purchases attributed to organic** | The truth | UTM-tagged link-in-bio + post-purchase survey ("how did you find us") joined in {{ATTRIBUTION_STACK}} <!-- source: intake §6 --> |
<!-- /MODEL -->

Views are recorded in the manifest for outlier math only — never reported.

## Outlier definition (mechanical, no vibes)

A post is an outlier when saves (preferred) or views ≥ **3× the account's trailing-30-day median** for that platform. Absolute numbers stay small for a niche account — outlier status is relative to our own median, which is all the algorithm signal needed. Every outlier → appended CTA → paid test queue (`ORG-` prefix) → judged there on {{PAID_QUALITY_METRIC}} <!-- source: MEASUREMENT.md — cost per qualified lead / activation / purchase --> like any ad. This is the non-negotiable rule.

## Cadence

- **Weekly (inside the playbook ritual):** fill scorecard rows; run the outlier check; log buying-question DMs.
- **Monthly (30 min, alongside the paid review):** save-rate by series and avatar → kill or iterate anything below the account median for 2 consecutive months (redesign the series, don't abandon the pillar); top-decile series get doubled next month. Attributed {{DOWN_FUNNEL_EVENT}} vs. last month. Check pillar drift (target 60/25/10/5).
- **Quarterly:** re-rank the question backlog by demonstrated save-rate {{PLUS_SEARCH_DEMAND}} <!-- source: platforms — "+ YouTube search demand" if in scope -->; feed winning topics into the paid hook library (the 70/20/10 input); compare organic-attributed customer value against cohort medians ({{VALUE_BENCHMARKS}} <!-- source: avatar research — the median and top-cohort values to compare against -->) — does organic pull the high-value profile?

## The join (same discipline as paid)

Organic post ID lives in the manifest and in `utm_content` on every link. That makes three questions answerable: which series/avatar produces saves → which produces {{MID_FUNNEL_EVENT}} <!-- source: model — leads/installs/carts --> → which produces {{DOWN_FUNNEL_EVENT}} and value. The per-creative reporting join in `../05-measurement/MEASUREMENT.md` should include ORG rows from day one.

## Honest-measurement guardrails

- A viral post with median-or-worse saves and zero buying questions is noise, not success — do not let it reshape the calendar (the protein-bomb rule).
- Don't judge a new series on fewer than 6 posts or 4 weeks.
- If attributed conversions rise while link taps and buying-question DMs are flat, check attribution before celebrating — "how did you hear about us" logging drifts.
- Follower counts may be glanced at annually, for amusement only.
