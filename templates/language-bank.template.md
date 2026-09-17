<!--
TEMPLATE: language-bank.template.md
PURPOSE: Produce the voice-of-customer language bank — the verbatim raw material behind every
  hook, headline, and objection-handling line in the plan. This doc feeds
  ../01-avatars/AVATARS.md (evidence for every pain/objection), ../03-ads/ADS-PLAYBOOK.md, and
  ../04-creative-production/CREATIVE-PRODUCTION-SPEC.md (hook quotas draw from the closing
  "Hook-ready phrases" section).

INPUTS REQUIRED before instantiating:
  1. User interview transcript — especially intake §2 (avatar hypotheses: best/worst customer
     stories, common objections in their own words).
  2. Review corpus — the business's own reviews if any, plus competitor reviews for the niche
     (Google, Trustpilot, G2, Yelp, Amazon, App Store / Play Store — whichever fit the model).
  3. Community corpus — Reddit threads, Facebook groups, forums, Discord, YouTube comments where
     the niche's buyers talk unprompted.
  4. Meta Ad Library pull — competitors' long-running ads (longevity ≈ working), noting the
     hooks, promises, and objection-handles they lead with.
  There is NO customer-data path: no CRM exports, no survey mining. Every quote comes from the
  four sources above.

QA CHECKLIST for the instantiated doc:
  [ ] Sources note lists each corpus with its size (counts of reviews/threads/ads) and pull date.
  [ ] 5–10 pain themes, discovered FROM the corpus (not imposed on it), 5–15 quotes each.
  [ ] Every quote carries exactly one source tag: [REVIEW] / [COMMUNITY] / [INTERVIEW] / [COMPETITOR-AD].
  [ ] Quotes are verbatim (typos kept) except redactions per the redaction rules — no paraphrase
      presented as quote; distilled lines live only in "Hook-ready phrases" and are labeled as distilled.
  [ ] Redaction rules section states exactly what was scrubbed.
  [ ] Contrast section draws only on language actually present in the corpus + interview.
  [ ] Hook-ready phrases: 40–60 total, grouped by the 5 awareness levels, each traceable to
      corpus language; claims/compliance-sensitive lines flagged against intake §7.
  [ ] No unreplaced {{PLACEHOLDERS}}, no template comments remain.
-->

# Language Bank — Voice of the {{CUSTOMER_NOUN}} <!-- source: PRD — "Customer", "Client", "User", "Patient", "Member"… -->

Raw material for writing {{HOOK_TARGET_COUNT}} <!-- source: intake §4 — typically "50+" ; scale with budget/creative volume -->+ ad hooks for {{BUSINESS_NAME}} <!-- source: PRD --> marketing.

**Sources:**
- {{REVIEW_CORPUS_LINE}} <!-- source: avatar research — e.g. "318 competitor reviews across [4 named competitors] (Google + Trustpilot), pulled YYYY-MM-DD" --> → tagged **[REVIEW]**
- {{COMMUNITY_CORPUS_LINE}} <!-- source: avatar research — e.g. "~240 threads/comments from r/[subreddit], [Facebook group], [forum], searched for [key phrases], pulled YYYY-MM-DD" --> → tagged **[COMMUNITY]**
- {{INTERVIEW_CORPUS_LINE}} <!-- source: intake §2 — e.g. "founder interview YYYY-MM-DD: best/worst customer stories, objections heard on sales calls" --> → tagged **[INTERVIEW]**
- {{AD_LIBRARY_CORPUS_LINE}} <!-- source: avatar research — e.g. "52 competitor creatives from Meta Ad Library, filtered to ads running 90+ days, pulled YYYY-MM-DD" --> → tagged **[COMPETITOR-AD]**

**Redaction rules applied:** No personal names, no identifiable third parties, no company/employer names of private individuals, no handles/usernames from community sources. Where a quote embedded one, it is replaced with a bracketed placeholder (e.g., `[spouse]`, `[boss]`, `[competitor]`, `[product]`) — everything else is verbatim, typos included. Public figures and competitor brand names in [COMPETITOR-AD] entries may be kept for internal analysis but must never appear in published creative. {{ADDITIONAL_REDACTION_RULES}} <!-- source: intake §7 — any niche-specific scrubbing (health details, financial specifics, minors); delete if none -->

---

## Pains & fears (pre-purchase, their words)

<!-- Discover 5–10 themes from the corpus — cluster the quotes first, then name the clusters.
     Do NOT start from a theme list and hunt for supporting quotes. Themes should map onto (and
     justify) the avatar pains in ../01-avatars/AVATARS.md. 5–15 quotes per theme. -->

### {{PAIN_THEME_1}} <!-- source: avatar research — name the theme in the customers' own framing, e.g. "Afraid of being overcharged and not knowing" -->
- "{{QUOTE}}" [REVIEW]
- "{{QUOTE}}" [COMMUNITY]
- "{{QUOTE}}" [INTERVIEW]
<!-- …5–15 quotes; mix source tags where the corpus allows -->

### {{PAIN_THEME_2}}
- "{{QUOTE}}" [{{TAG}}]
<!-- … -->

### {{PAIN_THEME_N}} <!-- repeat until the corpus's real themes are exhausted (5–10 total) -->
- "{{QUOTE}}" [{{TAG}}]



---

## Goals & desired outcomes (their words)

<!-- Same discovery method: 4–8 outcome themes, 5–10 quotes each. Goals are what they want to be
     true AFTER buying — distinct from pains. Look for "I just want…", "hoping to…", "so that…" -->

### {{GOAL_THEME_1}} <!-- source: avatar research — e.g. "Just want it handled without drama" -->
- "{{QUOTE}}" [{{TAG}}]

### {{GOAL_THEME_N}} <!-- repeat 4–8 total -->
- "{{QUOTE}}" [{{TAG}}]

---

## Decision language — why they chose / why they hesitated

### What made them buy/book/subscribe
<!-- Sub-theme the triggers found in the corpus: e.g. specific expertise, social proof volume,
     a friend's recommendation, a feature no competitor had, speed of response. Include, where
     the corpus supports it, a note on which decision factor dominates for BEST-fit customers —
     this becomes the "decision driver" evidence in ../01-avatars/AVATARS.md. -->

**{{DECISION_TRIGGER_THEME_1}}:** <!-- source: avatar research -->
- "{{QUOTE}}" [{{TAG}}]

**{{DECISION_TRIGGER_THEME_N}}:** <!-- repeat 3–6 themes -->
- "{{QUOTE}}" [{{TAG}}]

### Why they hesitated
<!-- Sub-theme the hesitations: not-ready-yet, waiting on a person/event, fear of making things
     worse, comparison shopping, a cheaper alternative, DIY-first instinct. These write the
     retargeting and objection-handling creative. -->

**{{HESITATION_THEME_1}}:** <!-- source: avatar research -->
- "{{QUOTE}}" [{{TAG}}]

**{{HESITATION_THEME_N}}:** <!-- repeat 3–6 themes -->
- "{{QUOTE}}" [{{TAG}}]

---

## Objections (incl. price objections)

<!-- Every objection the corpus + interview surfaced, verbatim. Price gets its own sub-sections
     because price language splits by customer quality — capture BOTH the objection and any
     counter-language satisfied customers use ("worth every penny" equivalents). -->

**{{OBJECTION_THEME_1}}:** <!-- source: avatar research + intake §2 — e.g. "Will this work for MY situation" -->
- "{{QUOTE}}" [{{TAG}}]

**Price objections (the wrong-customer tell vs. the fair question):**
- "{{PRICE_OBJECTION_QUOTE}}" [{{TAG}}] <!-- capture both flavors: price-FIRST language (anti-avatar signal) and price-paired-with-value language (real buyer doing diligence) — label which is which -->

**The counter-language that lands (from satisfied {{CUSTOMER_NOUN}} reviews — use in objection-handling copy):**
- "{{VALUE_AFFIRMATION_QUOTE}}" [REVIEW] <!-- e.g. corpus equivalents of "worth every penny", "should have done this years ago", "cheaper than the mistake I was about to make" -->

---

## Post-purchase praise

<!-- From [REVIEW] (own + competitor positive reviews) and [INTERVIEW] (what customers thank them
     for). Theme by praised BEHAVIOR, in rough frequency order — the top theme is usually the
     strongest provable differentiator and becomes proof-level creative. If mining competitor
     reviews only: this is what the market rewards, i.e. the bar and the gap map. -->

### {{PRAISE_THEME_1}} — {{PRAISE_THEME_1_NOTE}} <!-- source: avatar research — e.g. "Responsiveness — the single most-praised behavior" -->
- "{{QUOTE}}" [REVIEW]

### {{PRAISE_THEME_N}} <!-- repeat 4–8 themes, frequency order -->
- "{{QUOTE}}" [{{TAG}}]



---

## Contrast: best-{{CUSTOMER_NOUN}} language vs wrong-{{CUSTOMER_NOUN}} language

<!-- 5–12 numbered contrasts. Without customer data, build this from: interview best/worst customer
     stories, the difference between 5-star and 1-star review language, and community threads that
     ended well vs. badly. Each contrast should be phrased as "BEST does X / WRONG does Y" with the
     linguistic tell named — these become creative include/exclude rules and qualification signals. -->

1. **{{CONTRAST_DIMENSION_1}}.** {{CONTRAST_1_DESCRIPTION}} <!-- source: avatar research + intake §2 — e.g. "Specificity: best-fit buyers name concrete stakes and numbers; wrong-fit buyers speak in vague absolutes" -->
2. **{{CONTRAST_DIMENSION_2}}.** {{CONTRAST_2_DESCRIPTION}}
3. **{{CONTRAST_DIMENSION_N}}.** <!-- repeat 5–12; common dimensions worth checking against the corpus: something-to-protect vs something-to-escape, readiness/deadlines vs pre-decision limbo, capability-first vs price-first questions, realistic vs maximal goals, coherent story vs chaos markers, post-purchase "worth it" vs "waste of money" framing -->

---

## Hook-ready phrases

<!-- 40–60 phrases distilled or lightly edited from the corpus above — the ONLY section where
     editing beyond redaction is allowed. Each phrase must trace to corpus language; no invented
     claims. Group by the 5 awareness levels; aim for rough balance (unaware and most-aware are
     usually the thinnest — that's acceptable). Check every phrase against intake §7 compliance
     constraints (regulated claims, platform policies, personal-attribute call-out rules). -->

### Unaware / curiosity (they don't know they have the problem yet)
1. "{{HOOK_PHRASE}}" <!-- reframes, hidden-cost reveals, "you're already X" lines; ~6–10 phrases -->
2. …

### Problem-aware / pain (they feel it; name it back to them)
<!-- The largest group: mirror the pain themes above almost verbatim; ~12–18 phrases -->
1. "{{HOOK_PHRASE}}"
2. …

### Solution-aware / promise (they know the category; why this kind, why now)
<!-- Differentiation and urgency lines built on the decision-trigger themes; ~8–12 phrases -->
1. "{{HOOK_PHRASE}}"
2. …

### Product-aware / proof (they know {{BUSINESS_NAME}}; give them receipts)
<!-- Direct review quotes, counts ("N five-star reviews"), named results — only claims the corpus
     or the business's own assets can substantiate; ~8–12 phrases -->
1. "{{HOOK_PHRASE}}"
2. …

### Most-aware / offer (they're comparing; make the ask)
<!-- The offer, the risk-reversal, the CTA mechanics from intake §1 and §8: trial terms, guarantee,
     consult mechanics, bundle, deadline; ~6–10 phrases -->
1. "{{HOOK_PHRASE}}"
2. …

---

*Compiled {{COMPILATION_DATE}} <!-- source: avatar research — date of the research pull --> from {{SOURCES_ONE_LINE_RECAP}} <!-- source: avatar research -->. All identifying details redacted per the rules above. Refresh alongside `../01-avatars/AVATARS.md` — quarterly, or when a fresh research pass shifts the themes. Hook quotas that consume this bank: `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`.*
