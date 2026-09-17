<!--
TEMPLATE: CAPTURE-SYSTEMS.template.md
PURPOSE: Five always-on operational systems that turn {{BUSINESS_NAME}}'s daily reality into
a compounding library of proof material (testimonials, customer language, life-cycle stories,
b-roll) for the ads and organic engines. These are ops changes, not marketing spend.

INPUTS REQUIRED TO INSTANTIATE:
- PRD: niche, business model (lead-gen | app | ecom)
- Intake interview: §1 offer economics (what "a strong outcome" means), §3 creative faces,
  §6 tech stack (where consent records and captured assets live), §7 compliance,
  §8 capture opportunities (existing recordings, reviews, touchpoints, journey checkpoints)
- Avatar research: which proof moments each avatar needs to see

CONVENTIONS: Placeholders are `{{UPPER_SNAKE}}`, annotated with their source at first
occurrence. Keep exactly ONE `<!-- MODEL: ... -->` block per variant point (matching the
business model in the PRD) and delete the others, including the marker comments.

QA CHECKLIST (before delivering the instantiated doc):
- [ ] No `{{...}}` placeholders or `<!-- MODEL -->` / `<!-- source -->` comments remain
- [ ] Exactly one model variant kept in systems 2 and 4, matching the PRD
- [ ] Privacy-ladder consent rungs kept intact (all five) and adapted to the niche's sensitivity level
- [ ] 6-question testimonial interview arc preserved verbatim, including the bridge question
- [ ] Life-cycle checkpoints filled from intake §8 / the actual customer journey
- [ ] Compliance section names the real regulator/rules from intake §7
- [ ] Each system has a named trigger, owner, and storage location
-->

# Capture Systems — Start These Now

Proof footage compounds slowly; every month these systems aren't running is a month of ads {{BUSINESS_NAME}} <!-- source: PRD --> can't make later. All five systems below are ops changes, not marketing spend. The framing: **capture, don't manufacture** — look at what already happens (before/during/after the customer's journey), set up so the clip needs minimal editing, capture routinely, edit later. Target state: *every customer eventually produces at least one ad.*

## 1. Consent infrastructure (week 1, prerequisite for everything)

- One-page consent form with the **privacy ladder** (mirrored in `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`) as checkboxes:
  - (a) on-camera, full name
  - (b) on-camera, first name only
  - (c) voice-only
  - (d) anonymized retell / actor voice-over
  - (e) written review quote only
- Plus scope (ads/social/website), a revocation clause, and no-incentive-tied-to-review language.
- Store signed forms in {{CONSENT_RECORD_SYSTEM}} <!-- source: intake §6 --> against the customer record. **Nothing ships without a matching consent rung.** {{COMPLIANCE_APPROVER}} <!-- source: intake §7 --> signs off on the template before first use.

The ladder generalizes to any customer story: the more sensitive the niche, the more customers will start at the lower rungs — and lower-rung material (anonymized retells, written quotes) still makes ads.

## 2. The "Why People Buy" loop (weekly, ~30 min)

Harvest the places customers already explain — in their own words — what hurt, what they feared, and why they chose you. The loop, not any single insight, is the asset.

<!-- MODEL: lead-gen -->
**Source: sales-call / consult recordings.** If calls are already recorded (or summarized into {{CRM}} <!-- source: intake §6 -->), formalize the loop:
1. Weekly: pull the week's recordings/summaries and notes.
2. Extract into a running sheet: questions asked (verbatim), pains (internal feelings vs external situations), objections (price, risk, "is it too late"), avatar tags, and the phrases customers repeat.
3. Route monthly into: the hook library refresh, the objection accordions on landing pages, the pre-call VSL question list (this sheet IS its source of truth), and sales-script tuning (front-load the top objections).


<!-- /MODEL -->
<!-- MODEL: app -->
**Sources: onboarding calls, support tickets, app-store reviews, churn surveys.**
1. Weekly: pull the week's onboarding-call notes, new support tickets, fresh app-store reviews, and churn/cancellation survey responses.
2. Extract into a running sheet: what users were trying to do (verbatim), the moment it clicked, friction and confusion phrases, objections ("does it work with X," "is it worth paying for"), and churn reasons in the user's words.
3. Route monthly into: the hook library refresh, onboarding-copy and empty-state fixes, the objection sections of the landing page and store listing, and the activation-nudge sequence.
<!-- /MODEL -->
<!-- MODEL: ecom -->
**Sources: product reviews, support chats, post-purchase surveys.**
1. Weekly: pull new reviews (all star levels), support-chat transcripts, and post-purchase survey responses ("what nearly stopped you from buying?").
2. Extract into a running sheet: the job the product was bought for (verbatim), pre-purchase doubts, comparison language ("I almost bought X instead"), delight phrases, and complaint patterns.
3. Route monthly into: the hook library refresh, PDP copy and FAQ, ad objection-handling creatives, and the abandoned-cart flow's proof touches.
<!-- /MODEL -->

## 3. Testimonial capture (trigger-based, always-on)

- **Triggers:** (a) 5-star public review posted → same-week ask; (b) a strong outcome plus a warm relationship → the team member closest to the customer flags it to marketing; (c) NPS 9–10 responses.
- **The ask** (email/text template): "Your words could steady someone who's exactly where you were last year — would you share your story for 20 minutes? However you're comfortable: on camera, voice only, or written with your name changed."
- **The interview — 6-question arc, pre-set and scripted** (camera and questions ready before they arrive). This arc is universal; **the bridge question (Q4) is the conversion mechanism**:
  1. Who are you? (place, life situation — only what they'll allow)
  2. What was going on before you found us? (external)
  3. How did it *feel*? Who else was affected? (internal)
  4. **The bridge:** How did you find us? What almost stopped you from going ahead / choosing us? Why did you go ahead anyway?
  5. Where are things now — what can you do that you couldn't then?
  6. "What would you say to someone sitting where you were, unsure about taking the step?"
- Editors clip around Q4 and Q6 — the doubt and the advice are the ad.

## 4. Life-cycle documentation (opt-in; a handful of customers/year is success)

Document a few consenting customers across {{CUSTOMER_JOURNEY_CHECKPOINTS}} <!-- source: intake §8 --> — brief check-ins captured at each checkpoint, from rung (a)/(b) consenters with a cooperative temperament (team judgment). The doubts they felt at the start come from the §2 harvest (with consent) or are restated in the first check-in ("what were you afraid of the day you signed up?").

<!-- MODEL: lead-gen -->
**Checkpoint pattern for a service business:** signed/plan-in-place → first milestone → mid-engagement → completion/outcome → one-year-later. Handle with niche-appropriate care: no third parties or minors on camera without their own consent, no sensitive case details, and the customer can pause or withdraw at any checkpoint.
<!-- /MODEL -->
<!-- MODEL: app -->
**Checkpoint pattern for an app:** day 0 (signup — the problem in their words) → the aha moment → day 30 (habit formed, first results) → day 90 (transformation, measurable outcome). Screen-recordings + selfie check-ins keep this near-zero-cost; the day-0 vs day-90 contrast IS the ad.
<!-- /MODEL -->
<!-- MODEL: ecom -->
**Checkpoint pattern for a product:** unboxing/first use → early-result check-in → 6-month "still using it" update. Seed it via the post-purchase flow ("film your unboxing, tag us"); the long-term-use follow-up is the proof competitors can't fake.
<!-- /MODEL -->

## 5. Everyday b-roll — business-life capture

- Standing rule: **document, don't stage** — team prep sessions, behind-the-scenes of the work, workspace life, community/customer events, whiteboard moments, new-team-member introductions (entity trust: many faces, one brand).
- Phone + tripod stationed where the work happens; a shared "capture" drive folder the clipping pipeline watches. 60 seconds of capture per event; editing happens later, downstream.
- Review capture: screenshot every new 5-star review into the same drive (feeds the review-screenshot static format in the ads angle taxonomy).

## Operating notes

- **Owner:** {{CAPTURE_OWNER}} <!-- source: intake §3 --> owns triggers and the drive; the team members closest to customers own the asks and consent sign-offs.
- **Cadence review:** monthly — count assets captured per system; a system that produced zero for two months gets its **trigger redesigned, not abandoned**.
- **Compliance:** review the consent form and every testimonial against {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 --> rules before first publication; no "results guaranteed" framing anywhere; paid actors/voice-over always disclosed as such.
