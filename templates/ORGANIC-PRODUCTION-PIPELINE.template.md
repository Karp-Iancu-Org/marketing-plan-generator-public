<!--
TEMPLATE: ORGANIC-PRODUCTION-PIPELINE.template.md
PURPOSE: How organic volume gets made without consuming the team — the
  capture→clip→post chain. EXTENDS the creative-production spec (which the
  asset project owns) with organic-specific requirements; never duplicates it.
INPUTS:
  - ../04-creative-production/CREATIVE-PRODUCTION-SPEC.md (the automation spec
    this doc adds requirements to) and CAPTURE-SYSTEMS.md (shared capture ops)
  - ORGANIC-SOCIAL-STRATEGY.md + ORGANIC-CONTENT-PLAYBOOK.md (cadence, series)
  - Intake §3 (faces/footage), §9 (cadence, owner)
  - Lessons: 09 (the clipping automation, vibe editing, named hooks, volume
    benchmarks: 35 clips/day at $2.59/video), 02 §10 (capture-don't-manufacture),
    04 (workflow = trigger→action→result; the closing organic+paid-automatic bar)
GENERATOR ACTIONS:
  1. Fill placeholders; adapt the chain's box (1) corpus to the niche's actual
     voice-of-customer sources.
  2. Write the named-hook list for the niche (§3.2) — hooks the clipping prompt
     can be taught to find; weight the save-engine hooks for organic.
  3. Rewrite worked-example blockquotes or delete.
QA CHECKLIST:
  [ ] Exactly two human boxes remain in the chain (record + compliance QA).
  [ ] Volume expectations state numbers (clips per hour of footage, posts/month).
  [ ] The manifest/naming requirement joins organic to the paid measurement
      chain (ORG- prefix survives into utm_content).
  [ ] Roles table names owners from intake, not "the team."
  [ ] Definition-of-done items are verifiable, not aspirational.
-->

# Organic Production Pipeline — Capture → Clip → Post

How the volume gets made without consuming the team. This doc **extends** `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md` with the organic-specific requirements; capture ops live in `CAPTURE-SYSTEMS.md` and are shared with paid. Principle: **capture, don't manufacture** (lesson 02 §10) — and only two boxes in the chain stay human: recording and compliance review.

## 1. The chain (the 8-box pipeline of lesson 09, this business's edition)

```
(1) Mine the corpus — {{VOICE_SOURCES}}   <!-- source: intake §8 — recorded calls, reviews, support threads, community posts, language bank -->
(2) Arrange into a question backlog (avatar-tagged, ranked by frequency)
(3) Generate shoot run-sheets (one question per slated block)
(4) {{TALENT}} RECORDS  ← human box #1 (the shared monthly shoot, SPEC §5)   <!-- source: intake §3.1 -->
(5) Footage-detect (watched drive folder / cron)
(6) Clipping automation (transcribe → LLM segment-finding → render)
(7) COMPLIANCE QA  ← human box #2 (2-min gate per asset)
(8) Schedule & post per platform → pull performance → informs (2) next month
```

Boxes 1–3, 5–6, and 8 are the downstream asset project's build. Until it exists, the same chain runs manually at lower volume — {{MANUAL_CADENCE}} <!-- source: intake §9.3 — the Phase A by-hand pace --> is sustainable by hand; the pipeline is what unlocks {{TARGET_CADENCE}} <!-- source: strategy -->.

## 2. Volume expectations (recalibrated per lesson 09's benchmarks)

- **Every recorded hour of {{TALENT}} footage yields 5–10 mid-form clips + 10–20 shorts** at near-zero marginal cost (the reference: 35 clips/day at $2.59/video with one operator).
- One monthly shoot {{PLUS_SECONDARY_SOURCE}} <!-- source: playbook — e.g. "+ one interview-show episode" or delete --> ≈ **30–50 organic posts/month** — more than the cadence needs, which is the point: the queue never runs dry, and paid takes its weekly creatives from the same output.
- If a vendor quotes thousands per month for a handful of clips, or {{MODEST_CADENCE}} <!-- source: intake §9.3 --> feels like "a lot," recalibrate against these numbers.

## 3. Organic-specific requirements on the clipping automation (adds to SPEC's automation section)

1. **Dual-output render:** every selected segment renders both an ad candidate (per SPEC) and organic variants — 9:16 short with burned captions + CTA end-card, 16:9 mid-form with title card, and a caption file (hook line, body, CTA per the playbook, {{DISCLAIMER_SHORT}} <!-- source: intake §7 — or delete -->, avatar/series tags).
2. **Named hooks drive selection** (lesson 09: name your hooks so the AI can find them). This niche's named hook types for the clipping prompt:
   {{NAMED_HOOKS}} <!-- source: language bank + lesson 09's hook taxonomy — 4–6 named hooks, e.g. myth-bust (start at the contradiction), cost/consequence reveal (a number, a timeline), question-flip, checklist/number, fear-defusal. Note which are the save engines for this niche and weight them up for organic. -->
3. **Shorts prompt is the strict one** (lesson 09): open on a named hook within 3 seconds, cut all preamble, one complete idea with payoff, {{COMPLIANCE_CUT_RULE}} <!-- source: intake §7 — e.g. "never end a clip before the qualifying caveat that follows an outcome-adjacent claim" or delete -->, exclude anything implying a guarantee.
4. **Manifest is shared with paid.** Organic posts append to the same `manifest.csv` with an `ORG` channel column, post URL, and platform — this is what makes the outlier→paid promotion and the measurement join mechanical instead of vibes.
5. **Scheduling output:** a weekly queue file (post date, platform, file, caption) the operator approves in one sitting. Full auto-posting is a later milestone; the QA gate stays human indefinitely.

## 4. Statics and carousels (the no-footage lane)

Runs even in weeks nobody films — the "cheap variation machine" (lesson 02 §11, format 5):
- **Checklist carousels** from the education series (template-driven per the brand kit).
- **Proof statics** from the praise inbox (screenshot every new review/thank-you the day it arrives — CAPTURE-SYSTEMS).
- **Quote cards** from language-bank customer phrasing (anonymized/consented per the niche's rules).
Target: 10–20 static/carousel variants per month, batched in one sitting.

## 5. Roles

| Role | Owns |
|---|---|
| {{RITUAL_OWNER}} <!-- source: intake §9.4 --> | Backlog, run-sheets, weekly ritual, scheduling queue, outlier promotion, reporting |
| {{TALENT_ROLES}} <!-- source: intake §3.1 --> | The monthly shoot {{PLUS_SECONDARY_SOURCE}}; consent sign-offs; nothing else |
| {{COMPLIANCE_REVIEWER}} <!-- source: intake §7 — who has final say --> | The 2-minute gate; final say, no appeals |
| Asset project | Boxes 1–3, 5–6, 8 of the chain; the templates; the manifest |

## 6. Definition of done (organic additions to the SPEC's)

1. One monthly shoot reliably produces ≥20 posted organic assets within 10 days, ≤10 min operator time per batch.
2. The weekly queue sustains the Phase B cadence for 4 consecutive weeks without heroics.
3. Outlier promotion is a one-step action (manifest row → paid test queue with `ORG-` ID intact).
4. All in-scope platforms are fed from the one weekly queue — no platform requires its own separate workflow.
5. Saves/engagement data flows back into the monthly backlog ranking (the loop closes — lesson 04's bar: every customer result posts to organic and paid, automatically).
