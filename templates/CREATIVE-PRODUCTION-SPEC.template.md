<!--
TEMPLATE: CREATIVE-PRODUCTION-SPEC.template.md
PURPOSE: Generates the handoff contract for the client's creative/asset production project —
  the requirements doc that a separate build effort (human editor, automation build, or both)
  uses to produce ad creatives at volume. Self-contained together with its sibling folders:
  avatars/language in ../01-avatars/, campaign rules in ../03-ads/ADS-PLAYBOOK.md,
  capture ops in CAPTURE-SYSTEMS.md (sibling file).
INPUTS REQUIRED BEFORE INSTANTIATION:
  - PRD: business name, niche, offer, primary conversion action, brand assets inventory
  - Intake interview: §1 business model & offer economics, §2 avatar hypotheses,
    §3 creative faces (who can be on camera), §4 budget, §5 geography/scope,
    §7 compliance, §8 capture opportunities
  - Avatar research: finished ../01-avatars/AVATARS.md and ../01-avatars/language-bank.md
GENERATOR RULES:
  - Keep exactly ONE <!-- MODEL: ... --> block per variant point; delete the others.
  - Replace every {{PLACEHOLDER}}; none may survive into the generated doc.
  - Worked-example blockquotes may be kept, replaced with niche-appropriate ones, or dropped.
QA CHECKLIST (run after instantiation):
  [ ] No {{...}} placeholders or <!-- MODEL --> / <!-- source --> comments remain
  [ ] Avatar codes in §1 match ../01-avatars/AVATARS.md exactly
  [ ] Volume table in §2 is consistent with the budget in ../03-ads/ADS-PLAYBOOK.md
  [ ] Compliance checklist in §5.4 cites the actual rules for this niche, not a generic stub
  [ ] The pre-purchase VSL recipe (§4.3) matches the chosen business model
  [ ] Every cross-reference resolves to a file that exists in the generated plan
-->

# Creative Production Spec — Handoff Contract for the Asset Project

This is the requirements document for the separate project that builds ad assets and the production automation for {{BUSINESS_NAME}} <!-- source: PRD -->. It is self-contained together with its sibling folders: avatars and language in `../01-avatars/`, campaign rules in `../03-ads/ADS-PLAYBOOK.md`, capture ops in `CAPTURE-SYSTEMS.md`. The asset project's job: **make 5–10 new ad creatives per week cheap, fast, and on-avatar — scaling to roughly 10+/week per $10K/month of spend** (rule of thumb: weekly creative volume ≈ monthly spend ÷ $1,000).

---

## 1. The asset ID system (non-negotiable — used by ads, URLs, and measurement)

Every creative gets an ID: `A<avatar>-H<hook#>-M<meat#>-C<cta#>-v<variation>`

- Avatar codes: one per avatar in `../01-avatars/AVATARS.md` — {{AVATAR_CODE_LIST}} <!-- source: avatar research --> — plus **A0 = general-proof** (reviews, brand assets, social proof not tied to one avatar).
- Hook/meat/CTA numbers index into the component libraries (§3). Variations (v1, v2…) are same-components re-cuts: different opening 2 seconds, length, music, speaker, background, aspect ratio.
- **The ID is the file name, the ads-platform ad name, and the `utm_content` value** (see `../06-setup-walkthroughs/TRACKING-SETUP.md`). A `manifest.csv` (id, avatar, hook text, meat summary, cta, format, source footage, date, status) is the registry; the automation must append to it on every render. If the ID chain breaks anywhere, per-creative measurement breaks everywhere.

## 2. Volume targets

Targets scale with {{BUDGET_TIER}} <!-- source: intake §4 -->. Baseline table (adjust the weekly row to ≈ monthly spend ÷ $1,000):

| Cadence | Output |
|---|---|
| Weekly | {{WEEKLY_CREATIVE_TARGET}} <!-- source: intake §4 --> finished creatives into the test queue (mix per 70/20/10: ~70% variations of current winners, ~20% adjacent concepts, ~10% wild swings) |
| Monthly | 1 founder/expert shoot (≈2 hrs) → 15–30 talking-head raws → 40–100 assembled ads via components |
| Quarterly | hook-library refresh from new customer-conversation notes/reviews; retire fatigued components |

Format mix while proof footage accumulates: ~50% statics, ~35% talking-head clips, ~15% faceless/proof. Shift toward testimonial/life-cycle formats as `CAPTURE-SYSTEMS.md` produces material.

## 3. The assembly formula: hook × meat × CTA

Ads are **assembled from components, not written from scratch**. One monthly shoot + component libraries ≈ hundreds of possible ads (the math: 50 hooks × 3–5 meats × 1–3 CTAs ≈ 750 combinations).

### 3.1 Hook library (target: 50 per priority avatar; seed bank lives in `../01-avatars/language-bank.md`)

Write hooks at all five awareness levels; tag each hook `H<n>` with avatar + level:

| Level | Hook type | Generic pattern |
|---|---|---|
| Unaware | curiosity | <!-- MODEL: lead-gen -->"Three things {{AVATAR_CALLOUT}} find out too late about {{PROBLEM_DOMAIN}}." <!-- source: intake §2 --><!-- /MODEL --><!-- MODEL: app -->"The {{DAILY_TASK}} habit that's quietly costing you {{HIDDEN_COST}}." <!-- source: intake §2 --><!-- /MODEL --><!-- MODEL: ecom -->"Why your {{PRODUCT_CATEGORY}} stops working after {{FAILURE_POINT}} — and nobody tells you." <!-- source: intake §2 --><!-- /MODEL --> |
| Problem-aware | pain | A vivid line naming the felt pain in the avatar's own words from the language bank ("The other side has X. You have a knot in your stomach.") |
| Solution-aware | promise | "There's a way to get {{DESIRED_OUTCOME}} without {{FEARED_COST}}." <!-- source: intake §2 --> |
| Product-aware | proof | Concrete numbers: "{{PROOF_STAT}} <!-- source: PRD -->. This is what {{CUSTOMER_WORD}} say about ours." |
| Most-aware | offer | <!-- MODEL: lead-gen -->"Book a {{CONSULT_NOUN}} this week — come out with an actual plan, not a sales pitch."<!-- /MODEL --><!-- MODEL: app -->"Start your free trial today — set up in under {{SETUP_MINUTES}} minutes."<!-- /MODEL --><!-- MODEL: ecom -->"{{OFFER_HOOK}} — this week only, mechanics spelled out."<!-- /MODEL --> |

Rules: call out ONE avatar with objective attributes (occupation, life stage, location, situation markers) + the emotional pain, **in language lifted from the language bank**. Never lead with price. **The 3-second rule for video: the speaker identifies the audience / what the ad is about in the first 3 seconds** ("If you {{AVATAR_SELF_ID}} and you're dealing with {{PROBLEM}} —").



### 3.2 Meat library (`M<n>`, 3–5 per avatar)

60–90 seconds (video) or 2–4 sentences (static/copy) of genuine value speaking to the avatar's pain: how the core mechanism of {{OFFER}} <!-- source: intake §1 --> actually works, what the avatar's specific situation means for them, what the process/product experience really involves. Meats come from expert/founder answers — see the shoot format (§5.2). Outcomes, not process ("what you get," never a full how-to that substitutes for the paid thing).

### 3.3 CTA library (`C<n>`, 1–3 standing)

- C1 (primary): "{{PRIMARY_CTA_LINE}} <!-- source: intake §1 --> — click below." In video versions, **demonstrate the click/action on screen**.
- C2 (direct-response alt): <!-- MODEL: lead-gen -->"Call {{TRACKING_NUMBER}} <!-- source: intake §6 --> — we answer, and we call back same day."<!-- /MODEL --><!-- MODEL: app -->"Download free on the App Store / Google Play — no card required."<!-- /MODEL --><!-- MODEL: ecom -->"Free shipping + {{GUARANTEE}} <!-- source: intake §1 --> — order in 60 seconds."<!-- /MODEL -->
- C3 (soft/education): "Follow for straight answers about {{TOPIC}}."

CTA doctrine: spell out the mechanics of what happens when they act; then layer specificity (availability, timing, location where relevant).

## 4. Format recipes (the recipe book — all formats specced; capture-dependent ones start producing when material exists)

### 4.1 Static image ads (launch format — 10+ per avatar)

- Composition: bold call-out headline (the hook, ≤12 words) + one supporting line + brand mark + CTA strip. Real photography (the actual people, product, locations recognizable to {{GEO_SCOPE}} <!-- source: intake §5 --> where relevant) or clean typographic cards. AI-generated *imagery* is acceptable for backgrounds/scenes, **never for fake people presented as real customers**.
- Variants per concept: 2–3 crops (1:1, 4:5, 9:16), light/dark, photo/typographic.
- **Review-screenshot subformat (A0):** a real review from {{REVIEW_PLATFORM}} <!-- source: intake §6 -->, reviewer name shortened exactly as published, star row visible, one highlighted sentence, "one of {{REVIEW_COUNT}} <!-- source: PRD --> reviews" caption.

### 4.2 Expert/founder talking-head clips (30–90s)

- Source: the monthly Q&A shoot (§5.2). Structure: 3-second self-ID hook → meat (one question, one answer) → CTA. Captions always; raw and authentic beats polished (low edit complexity is a feature — it automates).
- Entity-trust language: "we / our team" — trust must attach to the business, not one irreplaceable person. On-camera faces per {{CREATIVE_FACES}} <!-- source: intake §3 -->.

### 4.3 The pre-purchase VSL (highest-priority single asset) + per-avatar landing VSLs

5, 7, or 10 minutes, scripted. Skeleton: warm intro + what-this-video-is-for (30s) → Q&A blocks (30–60s each: question as on-screen text → answer → what it means for you) → what the next step actually is → what to expect/bring → CTA + reassurance.

<!-- MODEL: lead-gen -->
- Content: the **10–15 most-asked pre-consult/pre-call questions**, mined from actual sales-call recordings and notes (harvest procedure in `CAPTURE-SYSTEMS.md`), answered by the expert. Closing block: what the consult/call actually is (discovery + plan), what to bring.
<!-- /MODEL -->
<!-- MODEL: app -->
- Content: a **demo/onboarding VSL** answering the top objections and confusions found in App Store / Play Store reviews and support tickets — what the app does in the user's real day, the "aha" moment on screen, the top 10–15 questions/objections answered over live product footage. Closing block: what happens in the first session after install.
<!-- /MODEL -->
<!-- MODEL: ecom -->
- Content: a **product-demo VSL** — the product in real use, the mechanism ("why it works"), the top 10–15 pre-purchase questions/objections (mined from reviews, support inbox, and competitor-review complaints) answered on camera. Closing block: offer, guarantee, and what happens after checkout.
<!-- /MODEL -->

- Cut-downs: every Q&A block doubles as a talking-head ad (§4.2) — the shoot must slate each block cleanly to enable this.
- Per-avatar landing VSLs are the same skeleton filtered to that avatar's questions.

### 4.4 Testimonial ads (capture-dependent)

- Interview per the 6-question arc (full guide in `CAPTURE-SYSTEMS.md`): who they are → external before → internal before → **the bridge (their doubts, and why they said yes anyway — the conversion mechanism)** → external after → advice-to-someone-unsure (the natural CTA).
- **Consent/privacy ladder** — produce at whichever rung the customer consents to; more sensitive niches will cluster at the lower rungs: (a) on-camera full name; (b) on-camera, first name only; (c) voice-only + b-roll; (d) written story, actor voice-over, "details shared with permission, name changed"; (e) review-screenshot static. Written consent required for a–d; consent template lives with `CAPTURE-SYSTEMS.md`. Consent strictness scales with {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 -->.

### 4.5 Life-cycle ads (the long game; capture starts now)

One consenting customer documented across {{JOURNEY_CHECKPOINTS}} <!-- source: intake §8 --> — from pre-purchase doubts (recorded or reconstructed) → decision moment → first milestone → mid-journey → final outcome / "one year later." The prospect's own objections, voiced by someone who lived them, become the hooks. Realistic yield: 2–4 willing customers/year — that's enough; one great life-cycle ad can run for years.



### 4.6 Faceless / education

Text-slideshow or motion-typography over stills: listicles ("5 things to do before {{KEY_DECISION}}"), mechanism explainers, jargon decoders for {{NICHE}} <!-- source: PRD -->. Whiteboard-style breakdowns (cheap, long shelf life). No booms/whooshes — **effective production beats overproduction**.

### 4.7 Spokesperson (optional lane)

A recurring non-expert brand face (marketing/support team member) for education + man-on-the-street formats, clearly identified as non-expert where the niche demands it ("I'm not the {{EXPERT_TITLE}} — I sit next to them; here's what they'd want you to know…"). Never gives regulated advice on camera where {{COMPLIANCE_DOMAIN}} applies. This lane de-risks expert/founder availability.

## 5. Production system

### 5.1 Brand kit (build first; the automation consumes it)

Logo files, color hex set, headline/body fonts, subtitle style (font/size/position/color), intro-free opening rule (no bumpers), CTA end-card templates per aspect ratio, tracking-number/URL set per avatar. Store as `brand-kit/` with a `brand.json` the automation reads.

### 5.2 The monthly founder/expert shoot (2 hours, one operator)

Setup: one camera (phone on tripod is fine), lav or shotgun mic (**clean audio is the only hard requirement**), neutral backdrop, teleprompter optional. Format: interviewer off-camera reads questions from the hook/meat backlog; the expert answers to camera twice (once long, once tight); operator **slates each block** ("A1-M3, take 2"). An hour of pre is worth ten of post: consistent framing + slating is what makes automated clipping reliable.

### 5.3 The clipping/assembly automation (the "vibe editing" build)

Build with Claude Code as the orchestrator. Capabilities, in build order:

1. **Ingest & transcribe:** drop a folder of footage → `ffmpeg` normalizes → Whisper (or equivalent) transcribes with timestamps → transcript stored beside the media.
2. **Clip selection (LLM over transcript):** prompt pattern: *"Find 30–90s segments where one question is asked and fully answered. Each clip must open with (or be prependable with) a 3-second audience call-out, contain one complete thought (a hook, tension, and payoff), and end on a natural sentence boundary. Prefer segments matching these named hooks: [hook library for the target avatar]."* Shorts need the stricter prompt (explicit include/exclude rules); mid-form only needs clip-start/clip-end.
   - Pro move: feed proven high-performing clips (yours or public examples from {{NICHE}} advertisers) and ask the model to *extract the first principles that made them work*, then bake those principles into the selection prompt.
3. **Render:** `ffmpeg` cuts, burns captions per `brand.json`, applies the CTA end card, exports 4:5 + 9:16 + 1:1, names files by asset ID, appends to `manifest.csv`.
4. **Assembly mode:** given hook clip + meat clip + CTA card IDs, concatenate into a finished ad — this is what turns one shoot into dozens of ads.
5. **Statics generator:** template-driven (HTML/CSS→PNG or design-tool API): headline + supporting line + brand kit → the §4.1 variants.
6. **Hook factory:** the "50 hooks in 5 minutes" pattern — prompt an LLM with the avatar dossier + language bank + awareness-level definitions → 50 candidate hooks → human curates to ~15 → into the library. Rerun quarterly with fresh customer-conversation language.
7. *(Later)* competitor ad-library miner: pull {{NICHE}} advertisers from Meta's public Ad Library, extract hook patterns to a sheet, pattern-analyze, permutate per 70/20/10 into your voice.

Build method: reverse-prompt the roadmap first; use plan mode; make the agent interview you for brand/context; review the plan, not the code; iterate — most of the time goes into the clip-selection prompt. A simple local web UI (pick file → state what clips should contain → run) is the preferred operator surface.

### 5.4 Human QA gate (every asset, 2 minutes)

Compliance + quality checklist, tuned to {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 -->:

- [ ] No misleading claims or unjustified-expectation language ({{COMPLIANCE_RULE_CITATIONS}} <!-- source: intake §7 --> — e.g. professional-conduct advertising rules, FTC endorsement guides, platform health/finance policies, as applicable)
- [ ] Testimonials consented at the stated ladder rung; no customer-identifying details beyond consent
- [ ] Captions accurate; audience call-out present in the first 3 seconds (video)
- [ ] CTA mechanics spelled out
- [ ] File named by asset ID; manifest row written

Only then does the asset enter the weekly test queue.

## 6. What "done" looks like for the asset project

1. Brand kit exists; automation renders slated shoot footage into ID-named, captioned, multi-ratio clips with ≤10 min of operator time per batch.
2. The statics pipeline produces a 10-static avatar set in under an hour.
3. Weekly output ≥ {{WEEKLY_CREATIVE_TARGET}} net-new creatives sustained for 4 consecutive weeks without heroics.
4. Manifest + naming survive contact with the ads platform (IDs intact end to end into `utm_content` — verify against `../06-setup-walkthroughs/TRACKING-SETUP.md`).
5. The pre-purchase VSL and ≥2 avatar landing VSLs are shot, edited, and live.
