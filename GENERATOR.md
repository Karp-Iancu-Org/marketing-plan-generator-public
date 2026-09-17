# GENERATOR.md — How to Construct a Marketing Plan for Any Niche

You are constructing a complete, execution-ready marketing plan from a niche PRD, using the Acquisition.com/Mozi workshop lessons (`lessons/`) and the templates (`templates/`). Calibrate quality from the template QA requirements and the standalone, evidence, cross-reference, and invariant checks below. This public framework intentionally contains no completed niche plan.

**Output**: `niches/<niche-slug>/marketing-plan/` **inside this generator project** — never in the niche's own codebase.

`niches/` is already in this repo's `.gitignore`, so generated plans stay local and never push. That is the whole mechanism; no per-build git configuration is required, and **nothing is ever written into the source project the PRD came from.** That project is a source to read, not a target to modify — take the offer, the ICP, the geography constraints, and any voice specs in its prompt files, and disregard its tech stack, schema, and roadmap.

```
Marketing Plan Generator/
└── niches/                       ← gitignored; every generated plan lives here
    └── <niche-slug>/
        └── marketing-plan/       ← the structure below
```



```
marketing-plan/
├── README.md                  ← from templates/README.template.md
├── intake-record.md           ← every intake answer + every default taken (audit trail)
├── 01-avatars/
│   ├── AVATARS.md             ← from templates/AVATARS.template.md
│   └── language-bank.md       ← from templates/language-bank.template.md
├── 02-strategy/MARKETING-STRATEGY.md
├── 03-ads/ADS-PLAYBOOK.md
├── 04-creative-production/
│   ├── CREATIVE-PRODUCTION-SPEC.md
│   └── CAPTURE-SYSTEMS.md
├── 05-measurement/MEASUREMENT.md
├── 06-setup-walkthroughs/
│   ├── META-ADS-SETUP.md
│   ├── LANDING-PAGE-BUILD.md
│   └── TRACKING-SETUP.md
└── 07-organic/
    ├── ORGANIC-SOCIAL-STRATEGY.md
    ├── ORGANIC-CONTENT-PLAYBOOK.md
    ├── ORGANIC-PRODUCTION-PIPELINE.md
    └── MEASUREMENT-ORGANIC.md
```

The output is **two coupled plans — paid (01–06) and organic social (07)** — that share the avatars, language bank, capture systems, monthly shoot, and measurement join. They are one system: organic is the paid budget's free creative-testing lab (the outlier→paid flywheel), and paid winners inform the organic calendar.

The lessons corpus is NOT copied into the output — it stays here in the generator; the generated docs reference it by lesson number where a rule needs its source.

---

## Step 1 — Ingest the PRD

Read the PRD in full. Build the extraction table: for every questionnaire item in `INTAKE-QUESTIONNAIRE.md` (§1–§9), record `answered-by-PRD (with the quote)`, `inferable (state the inference)`, or `GAP`. **Never silently guess** — an inference gets confirmed at the next interview round; a gap gets asked.

## Step 2 — Intake interview

Run the asking protocol at the bottom of `INTAKE-QUESTIONNAIRE.md`: batched `AskUserQuestion` rounds covering only gaps and unconfirmed inferences. Two answers gate everything else and must exist before proceeding: **§1.1 business model** (selects every `<!-- MODEL: -->` variant) and **§4.1 budget tier** (sets volume targets and campaign structure). Write `marketing-plan/intake-record.md` as you go.

## Step 3 — Avatar research (interview + external research; no customer-data mining)

Goal: 3–5 avatar dossiers + 1 anti-avatar, each field **traceable to evidence** — a verbatim quote from research or an explicit intake answer. Invented pains are forbidden; if evidence is thin, say so in the dossier and mark the avatar "hypothesis — validate with first ad spend."

Research lanes (run what fits the niche; parallel subagents where available):
1. **Competitor & category reviews** — Google reviews, app-store reviews (both stores), G2/Capterra, Amazon — mine 1–5★ reviews of the §2.6 competitors for pains, decision language, praise, and rage-quits (anti-avatar signals live in competitors' 1★ reviews).
2. **Community language** — the §2.5 subreddits/groups/forums: how do these people describe the problem unprompted? Collect verbatim phrases.
3. **Competitor ads** — Meta Ad Library (facebook.com/ads/library, search each competitor): which hooks/angles/formats run long (long-running = working)? What awareness levels do they hit? What's absent (= open lane)?
4. **The user's own material** — any recordings, support threads, reviews, DMs the user can share (§8.3).

Synthesize into `01-avatars/language-bank.md` (per its template: themed quotes tagged [REVIEW]/[COMMUNITY]/[INTERVIEW]/[COMPETITOR-AD], then 40–60 hook-ready phrases across the 5 awareness levels) and `01-avatars/AVATARS.md` (per its template).

**CHECKPOINT — mandatory.** Present the avatars + anti-avatar to the user (short summaries + the evidence behind each) via `AskUserQuestion` (confirm / adjust per avatar). If research contradicted a §2 hypothesis, surface the contradiction explicitly. Do not generate downstream docs until avatars are confirmed — every other doc inherits them.

## Step 4 — Instantiate the templates (in this order)

Order matters — later docs cite earlier ones: **README → 02-strategy → 03-ads → 04-creative-production (spec, then capture) → 05-measurement → 06-setup-walkthroughs (meta → landing → tracking) → 07-organic (strategy → playbook → production → measurement)**.

The organic docs come last because they extend, and must never contradict, everything upstream: the organic strategy inherits the paid spine's position and avatars; the playbook's series tables draw from the language bank; the production pipeline adds requirements to the creative spec rather than duplicating it; the organic measurement joins the paid measurement's manifest/UTM chain. Honor the §9.1 scope exclusions explicitly — if the client already handles a channel (SEO/GBP, an agency-run platform), the organic strategy names it as out of scope rather than silently covering it.

For each template:
1. Resolve every `{{PLACEHOLDER}}` from the intake record / avatar research (the inline `<!-- source: -->` comment says where the value lives).
2. Keep exactly one `<!-- MODEL: -->` block per variant site (the §1.1 model); delete the other variants **and** the fence comments.
3. Delete the template's header comment (purpose/inputs/QA) after satisfying its QA checklist — the generated doc must read as a finished document, not a form.
4. Apply the lessons: `lessons/INDEX.md` is the rulebook; go into the numbered session docs when a section needs depth (e.g., writing hooks → lesson 03; VSL and sales motion → lesson 07; clipping automation → lesson 09). Translate principles into this niche only after research and intake evidence support the application.
5. Tune numbers to the niche: CPM/CPL planning bands, awareness-level examples, angle taxonomy, journey checkpoints — generic template values are starting points to be replaced with niche-informed ones, stated as assumptions to validate.

## Step 5 — QA gate (all must pass before declaring done)

- [ ] `grep -r '{{' marketing-plan/` → zero unresolved placeholders; `grep -r 'MODEL:' marketing-plan/` → zero leftover variant fences.
- [ ] `CREATIVE-PRODUCTION-SPEC.md` passes the standalone test: an asset team with ONLY the `marketing-plan/` folder knows what to build, how many, to what spec, with what naming.
- [ ] Walkthroughs pass the "never opened Ads Manager" test: every step names the screen, the control, and the expected result.
- [ ] Anti-avatar is defined and the qualification/optimization gate handles it.
- [ ] Every avatar pain/objection/hook traces to evidence in `language-bank.md` or `intake-record.md`.
- [ ] Compliance notes for the §7 domain appear in the creative spec QA gate and strategy risks (and the Meta special-ad-category flag is set correctly).
- [ ] Cross-references between the generated docs resolve (paths exist).
- [ ] The invariants survived instantiation: creative-ID `A#-H#-M#-C#-v#` = ad name = `utm_content`; ABO-test → CBO-scale; broad audiences; optimize only on the qualified/valuable event; 70/20/10; creatives/week ≈ monthly spend / $1,000.
- [ ] The organic invariants survived too: saves-first scoring with views/likes/followers absent from all reporting; the mechanical outlier rule (≥3× trailing-30-day median → appended CTA → paid test queue with `ORG-` prefix); cadence set to §9.3's sustainable-for-a-year answer; exactly two human boxes in the production chain (record + compliance QA); the §9.1 scope exclusions stated explicitly in the organic strategy.
- [ ] The two plans cross-reference correctly: organic docs cite the paid docs they extend (creative spec, capture, measurement), and the paid playbook's test queue accepts `ORG-` creatives.

## Step 6 — Executive briefs (optional but recommended — the decision-maker deliverable)

If the plan will be presented to partners/leadership, produce **two matching brief PDFs** — one per plan — from `templates/EXECUTIVE-BRIEF.template.html`, rendered via headless Chrome (`chrome --headless --no-pdf-header-footer --print-to-pdf=OUT.pdf IN.html`). Rules distilled from the reference build:

- **One design, two briefs.** Identical visual template (kicker, serif title, stat tiles, numbered steps, phase timeline, risks, sources footer) so they read as a pair; each footer names the other as its companion document.
- **Each brief leads with its own data-backed spine**, not the mechanism: the paid brief argues "our data identifies who to buy attention from"; the organic brief argues from the niche's organic-discovery evidence and the saves thesis. Neither repeats the other; a shared callout explains the outlier→paid coupling.
- **Executive language throughout**: no jargon from the operating docs (no "ABO/CBO," "Andromeda," "70/20/10" — say what they mean), 3–5 pages each, stat tiles carry the numbers that survive a partner meeting.
- Target ~4 pages; verify page breaks after rendering (headings must not dangle at page bottoms).

## Step 7 — Handoff summary

Confirm before reporting: `git status` in this repo does not list the generated plan (`niches/` covers it), and **the niche's own project directory was not written to at all**.

End with a short report to the user: the avatars (one line each), the chosen model and its funnel, the budget tier's volume commitment, the organic cadence commitment and platform order, the Phase A checklist (what to set up first, in order: tracking → landing → account → first creative batch → brand guidelines + first organic posts), and what the separate asset-creation project receives (the whole `marketing-plan/` folder; its requirements docs are `04-creative-production/CREATIVE-PRODUCTION-SPEC.md` plus `07-organic/ORGANIC-PRODUCTION-PIPELINE.md`).

---

## Operating rules

- **Ask, don't assume** — but batch questions; don't drip one at a time. Defaults exist in the questionnaire for a reason: offer them as "(Recommended)" options rather than asking open-ended everything.
- **Evidence discipline** is what makes this system better than generic marketing advice: quotes over adjectives, lifts over vibes, named sources over "research shows."
- **Depth over speed**: the reference build produced ~25 substantial documents. A thin plan defeats the purpose — the downstream asset project can only be as sharp as this plan.
- If the niche is one where paid Meta is a poor primary channel (pure B2B enterprise, for instance), say so in the strategy doc and adapt: the lessons (avatar-true creative volume, organic→paid flywheel, capture systems, VSL pre-framing) transfer to the channel that fits; the walkthroughs stay Meta-specific and get marked secondary.
