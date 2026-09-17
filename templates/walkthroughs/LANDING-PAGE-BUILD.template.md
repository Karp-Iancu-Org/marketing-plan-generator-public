<!--
TEMPLATE: LANDING-PAGE-BUILD.template.md
PURPOSE: Generates the step-by-step build guide for the destination the ads point at —
  per-avatar landing pages (lead-gen), landing page / store listing (app), or product
  page (ecom). The doctrine: the ad is personalized per avatar; the destination continues
  that exact conversation — one page per avatar, one video speaking only to that avatar,
  ONE action, and no exit points.
INPUTS REQUIRED BEFORE INSTANTIATION:
  - PRD: business name, domain, offer, primary conversion action
  - Intake interview: §1 business model & offer economics, §2 avatar hypotheses,
    §5 geography/scope, §6 tech stack (landing platform, CRM, booking tool), §7 compliance
  - Generated docs: ../01-avatars/AVATARS.md, ../01-avatars/language-bank.md,
    ../04-creative-production/CREATIVE-PRODUCTION-SPEC.md (VSL recipes), TRACKING-SETUP.md
GENERATOR RULES:
  - Keep exactly ONE <!-- MODEL: ... --> block per variant point; delete the others.
  - Replace every {{PLACEHOLDER}}; none may survive into the generated doc.
  - The section anatomy in Step 1 is the contract, not the tool — adapt labels to
    {{LANDING_PLATFORM}} but never drop sections.
QA CHECKLIST (run after instantiation):
  [ ] No {{...}} placeholders or <!-- MODEL --> / <!-- source --> comments remain
  [ ] Headline formulas reference the actual generated language-bank sections
  [ ] The conversion mechanics (form/thank-you pages, store badges, or cart) match the
      chosen model AND match TRACKING-SETUP.md exactly
  [ ] Per-avatar swap table lists the real avatars from AVATARS.md
  [ ] Compliance/disclaimer requirements for this niche appear in the footer section
-->

# Landing Page Build — Step-by-Step

The doctrine: **you personalize the AD per avatar; the landing destination continues that exact conversation** — a page that "is" the business for that avatar, a video speaking only to that avatar, one action ({{PRIMARY_CONVERSION_ACTION}} <!-- source: intake §1 -->), and "not a bunch of exit points." A subdomain is explicitly fine — no visitor penalizes you for a different URL.

One page per avatar (see `../01-avatars/AVATARS.md`). At launch that's 3–5 pages that share one template and swap the avatar-specific blocks.

---

## Step 0 — Platform and destination

<!-- MODEL: lead-gen -->
1. **Platform:** use {{LANDING_PLATFORM}} <!-- source: intake §6 --> — or whatever the team can edit fastest **with custom-code support** (needed for the pixel and the redirect logic in `TRACKING-SETUP.md`). Check for existing accounts before buying anything. Any capable builder works; **the contract is the section structure below, not the tool.**
2. **Subdomain:** create `{{CAMPAIGN_SUBDOMAIN}}` <!-- source: PRD --> in DNS (CNAME to the page platform per its instructions). Pages live at one slug per avatar (slugs mirror avatar names in `../01-avatars/AVATARS.md`).
3. Verify the root domain in Meta first (`META-ADS-SETUP.md` §1.4) — subdomains are then covered.
4. `noindex` these pages (page settings → SEO → hide from search engines). They exist for ad traffic; keeping them out of SEO avoids duplicate-content questions with the main site.
<!-- /MODEL -->
<!-- MODEL: app -->
1. **Decide the flow:** (a) **web landing page → store** (recommended when you need avatar-specific messaging, a VSL, or web-to-app tracking — build the page per Step 1 with store badges as the CTA), or (b) **direct-to-store** (ads link straight to the listing; the store listing IS the landing page).
2. If (a): platform = {{LANDING_PLATFORM}} <!-- source: intake §6 --> with custom-code support for the pixel; subdomain per avatar-slug as above; `noindex`. Deep-link/UTM handling per `TRACKING-SETUP.md`.
3. If (b), the **store listing** must do the landing page's job — treat this as the build:
   - **Screenshots = the section anatomy in miniature:** first screenshot is the headline + call-out; the next 4–6 walk hook → proof → mechanism → CTA in the avatar's language.
   - **Preview video = the VSL:** 15–30s, self-ID in the first 3 seconds, real product footage.
   - **Store-listing optimization checklist:** title + subtitle keywords; first 2 lines of description carry the promise (the rest is truncated); rating prompt strategy in-app so review score supports the ads; localized listings where {{GEO_SCOPE}} <!-- source: intake §5 --> warrants; custom product pages / store listing experiments used to mirror avatars where the platform allows.
<!-- /MODEL -->
<!-- MODEL: ecom -->
1. **Platform:** the store's own product pages on {{LANDING_PLATFORM}} <!-- source: intake §6 --> (e.g. the ecommerce platform's theme editor) — custom-code access needed for the pixel per `TRACKING-SETUP.md`. Ads land on a **product page or dedicated offer page**, never the homepage or a collection grid.
2. One landing product/offer page per avatar where messaging differs enough to matter; otherwise one strong product page with avatar-specific ad→section deep links.
3. Keep campaign-specific offer pages out of site nav and `noindex` where the platform allows.
<!-- /MODEL -->

## Step 1 — Page structure, section by section (top to bottom)

Every section either continues the ad's conversation or gets deleted. **No site nav, no footer link farm, no menu of other services.** The only clickable things: the primary CTA (repeated) and, where relevant, a click-to-call/contact link.

1. **Header strip:** logo (small), {{HEADER_CONTACT_ELEMENT}} <!-- source: intake §1 e.g. click-to-call number for lead-gen, support link for ecom --> top-right. Nothing else — no menu.
2. **Headline (H1):** the avatar's pain/promise **in their own words** — pull from `../01-avatars/language-bank.md`, matched to the ad's hook. Formula: *[Call-out], [the outcome they want] — [the reassurance they need].*
3. **Sub-headline:** one sentence of proof + specificity: years/customers/ratings + locality or category authority. <!-- source: PRD -->
4. **VSL block (above the fold):** the avatar's video — the pre-purchase VSL cut for this avatar (production spec in `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md` §4.3; 5, 7, or 10 minutes, scripted). Native/embedded player, thumbnail = a real person facing camera + caption text. Autoplay muted with captions is acceptable; captions are mandatory either way.
5. **Primary CTA button #1** directly under the video: "{{CTA_BUTTON_COPY}}" <!-- source: intake §1 -->. Button copy stays identical everywhere on the page. <!-- MODEL: lead-gen -->It scrolls to (or opens) the form.<!-- /MODEL --><!-- MODEL: app -->App Store + Google Play badges side by side (or a smart link that routes by device); on mobile the badge for the visitor's platform leads.<!-- /MODEL --><!-- MODEL: ecom -->It goes straight to add-to-cart / the offer selector.<!-- /MODEL -->
6. **Proof block:** rating badge + review count from {{REVIEW_PLATFORM}} <!-- source: intake §6 -->, 2–3 short review quotes **chosen for THIS avatar** from the language bank's post-purchase praise section (names/initials exactly as published), plus concrete numbers. The Amazon-style nuance: "Rated highly for [the thing this avatar fears getting wrong]" beats a generic 5-star wall.
7. **"What happens next" 3-step strip:** pre-frame the journey so the next step feels known: 1) {{NEXT_STEP_1}} → 2) {{NEXT_STEP_2}} → 3) {{NEXT_STEP_3}} <!-- source: intake §1 -->. Every next step gets pre-framed — ideally by video.
8. **Avatar-specific objection block:** 3–5 question/answer accordions using the EXACT questions this avatar asks (mined from sales conversations, reviews, or support tickets — see `../04-creative-production/CAPTURE-SYSTEMS.md`). Two-sentence answers; each ends pointing at the CTA.
9. **The conversion element:**
<!-- MODEL: lead-gen -->
   **The form** (3–5 qualifying questions + name/email/phone) — exact fields, logic, and the **two-thank-you-page redirect** per `TRACKING-SETUP.md` §2. Title above it repeats the promise, not "Contact us": "Get a plan for your situation."
<!-- /MODEL -->
<!-- MODEL: app -->
   **The install block:** store badges repeated + a one-line friction-killer ("Free to start · no card · set up in {{SETUP_MINUTES}} minutes"). Optional email-capture fallback for desktop visitors ("text me the link").
<!-- /MODEL -->
<!-- MODEL: ecom -->
   **The offer/bundle block:** product gallery (multiple angles + in-use shots), variant/bundle selector with the featured offer pre-selected, price + guarantee + shipping promise stacked at the button, reviews module directly beneath. Scarcity/urgency only when true.
<!-- /MODEL -->
10. **Trust footer:** photo of the real team with "we/us" entity-trust framing (trust must attach to the business, not one unavailable person), credentials/certifications, physical address where applicable, and the disclaimers {{COMPLIANCE_DOMAIN}} <!-- source: intake §7 --> requires, in small print.



## Step 2 — After the conversion

<!-- MODEL: lead-gen -->
Build `/thank-you-a` and `/thank-you-b` as **identical twins** (only page A carries the qualified-lead event — see `TRACKING-SETUP.md` §2):

1. **Headline:** "You're booked / You're on the list — here's what to do next."
2. **The pre-purchase VSL (again, or the fuller version).** Every next step gets pre-framed by video. If booking wasn't completed in-form, the {{BOOKING_TOOL}} <!-- source: intake §6 --> scheduling embed goes here, ABOVE the video.
3. **What-to-expect checklist:** when we contact you (within minutes during business hours), what to have handy, how long the first conversation runs.
4. **No exit points** other than call/book.
5. Placeholder-copy check: read every word on these pages before launch; broken thank-you pages silently kill show rates.
<!-- /MODEL -->
<!-- MODEL: app -->
The "thank-you page" is the **first session**. The landing work isn't done until:

1. The install deep-links into an onboarding flow that continues the avatar's conversation (pass the avatar/campaign context via deferred deep link or onboarding question — see `TRACKING-SETUP.md` for UTM handoff).
2. The first session reaches the "aha" moment the VSL promised, in minutes not days.
3. A day-1 message (push/email) pre-frames the next step, ideally with the same face from the VSL.
<!-- /MODEL -->
<!-- MODEL: ecom -->
The **order-confirmation page + post-purchase flow** continue the conversation:

1. Confirmation page: what-happens-next (ship timing, how to use it on arrival), a getting-the-most-from-it video, and the one sensible upsell/cross-sell at most.
2. Post-purchase email/SMS sequence pre-frames delivery and first use; the review ask comes only after value is delivered.
3. Placeholder-copy check on every transactional page and email before launch.
<!-- /MODEL -->

## Step 3 — Mobile + speed pass

1. Preview every page at phone width: headline ≤ 2 lines visible with the video's (or gallery's) top edge on the first screen; buttons thumb-sized; contact elements tappable.
2. Compress the VSL (platform-hosted or a proper video host embed, not a 200MB self-hosted mp4). Target page load under ~3s on 4G (test: PageSpeed Insights, mobile).
3. Kill any popups, chat widgets, or cookie walls beyond the legally required minimum — every interruption is an exit point.

## Step 4 — QA checklist before pointing ads at it

- [ ] Pixel fires `PageView` on the landing destination (Pixel Helper / SDK debug per `TRACKING-SETUP.md`).
- [ ] Conversion dry-run per `TRACKING-SETUP.md` (all branches; contact/order/install visible in {{CRM}} <!-- source: intake §6 --> with UTMs captured).
- [ ] All copy proofread; no placeholders anywhere, including page titles.
- [ ] Every contact/CTA element works from a real phone.
- [ ] <!-- MODEL: lead-gen -->{{BOOKING_TOOL}} embed books into the correct calendar.<!-- /MODEL --><!-- MODEL: app -->Store badges resolve to the correct listing per device; deferred deep link carries campaign context.<!-- /MODEL --><!-- MODEL: ecom -->Test order completes end to end (use a 100% discount code or test gateway) and fires `Purchase` with the right value.<!-- /MODEL -->
- [ ] Page renders correctly from an Instagram in-app browser (a large share of Meta clicks) — test by DMing yourself the link.

## Per-avatar swap list (what changes between the 3–5 pages)

| Section | Swapped content source |
|---|---|
| Headline/sub | avatar's hook language (`../01-avatars/language-bank.md`) |
| VSL | avatar-specific video (`../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`) |
| Proof quotes | reviews matched to this avatar's themes |
| Objection accordions | this avatar's top pre-purchase questions |
| Conversion element defaults | unchanged (same form/offer for all) |

Everything else — layout, conversion mechanics, post-conversion pages, tracking — is shared. Build page 1 (the priority avatar) completely, QA it, then clone for the rest.
