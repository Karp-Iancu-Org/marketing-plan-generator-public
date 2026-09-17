<!--
TEMPLATE: TRACKING-SETUP.template.md
PURPOSE: Generates the click-by-click tracking walkthrough — the doc that must be completed
  BEFORE any campaign launches in META-ADS-SETUP.md. Its spine is the business model:
  lead-gen (pixel + qualification gate + two thank-you pages + CRM CAPI), app (SDK/MMP +
  optimization-event definition + AEM), ecom (Purchase pixel + value + server-side CAPI).
  The governing principle in every model: **the ads platform is only ever trained on the
  event that means real value — qualified, activated, or paid — never on shallow actions.**
INPUTS REQUIRED BEFORE INSTANTIATION:
  - PRD: business name, domain(s), primary conversion action, value per conversion
  - Intake interview: §1 business model & offer economics, §2 avatar hypotheses
    (qualifying attributes), §6 tech stack ({{CRM}}, {{LANDING_PLATFORM}}, form/booking
    tools, analytics), §7 compliance (data/privacy constraints)
  - Avatar research: what objectively separates high-value customers (drives the
    qualification bar for lead-gen)
GENERATOR RULES:
  - Keep exactly ONE <!-- MODEL: ... --> block per variant point; delete the others —
    the kept block is most of this document.
  - Replace every {{PLACEHOLDER}}; none may survive into the generated doc.
  - The naming/UTM convention (Part 4) and maintenance rules (Part 6) are universal —
    keep them verbatim in every model.
QA CHECKLIST (run after instantiation):
  [ ] No {{UPPER_SNAKE}} placeholders or <!-- MODEL --> / <!-- source --> comments remain
      (EXCEPTION: Meta's own dynamic URL parameters {{campaign.name}} / {{adset.name}} in
      Part 4 are literal Meta syntax — they MUST survive verbatim)
  [ ] The optimization event named here matches META-ADS-SETUP.md §2.2 exactly
  [ ] For lead-gen: the qualifying questions and bar are derived from real avatar
      research, not the template's generic examples
  [ ] The dry-run procedure covers every branch of the routing/flow
  [ ] utm_content is defined as the creative ID and ad name = creative ID
-->

# Tracking Setup — Events, Qualification, CAPI, Naming — Click-by-Click

The whole strategy hinges on one tracking decision: **the ads platform must only ever be trained on the event that means real value** — a qualified lead, an activated user, a paid order — never on shallow actions (form fills of any quality, installs, page views). Do this doc **before** launching anything in `META-ADS-SETUP.md`.

---

<!-- MODEL: lead-gen -->
## Part 1 — Create the dataset (pixel)

1. business.facebook.com → **All tools (≡) → Events Manager**.
2. **Connect data sources → Web → Connect**. Name the dataset `{{BUSINESS_NAME}} Web` <!-- source: PRD -->. (Meta now calls the pixel a "dataset"; same thing.)
3. Choose **Meta Pixel → Set up manually** (the base-code approach works on any landing platform, including {{LANDING_PLATFORM}} <!-- source: intake §6 -->).
4. Copy the **base code** snippet (`fbq('init','<PIXEL_ID>');fbq('track','PageView');`).
5. Paste it into the `<head>` of **every landing page and thank-you page** (in most builders: Settings → Custom code/Scripts → Head). Site-wide install on {{ROOT_DOMAIN}} <!-- source: PRD --> is also fine and helps retargeting pools.
6. Verify: install the **Meta Pixel Helper** Chrome extension → open a landing page → the badge should show `PageView` firing.

## Part 2 — The qualification gate and the two thank-you pages

The mechanism, verbatim:

```
Landing page → form with 3–5 objective qualifying questions
   ├─ answers meet the bar  → /thank-you-a   (pixel event fires here)
   └─ answers miss the bar  → /thank-you-b   (identical page, NO event)
```

You keep and work every lead (the team still contacts both groups); **only the pixel's training diet is filtered.**

### 2.1 The qualifying questions (from the avatar data — see `../01-avatars/AVATARS.md`)

Use **objective, non-gameable** questions that map to what actually separates high-value customers in the avatar research: {{QUALIFYING_QUESTIONS}} <!-- source: avatar research + intake §2 — typically: location/service-area, an asset/situation marker, a scale marker, a tenure/duration marker, and urgency/timeline -->

**Qualified bar (v1):** {{QUALIFIED_BAR}} <!-- source: avatar research — a boolean rule over the answers that mirrors what separates the top-quintile customers from the bottom -->. Revisit quarterly — tighten if the team reports junk qualifying, loosen if volume starves.



### 2.2 Build the routing

Any form tool that supports **conditional redirects** works (some CRM-native forms only support this via workflows; simplest is the landing platform's own form logic, or a small JS handler):

1. Create `/thank-you-a` and `/thank-you-b` as **pixel-identical copies** — same design, same "what happens next" copy (see `LANDING-PAGE-BUILD.md`), different URL. Don't link to them from anywhere (no nav, `noindex`).
2. On submit, evaluate the answers → redirect qualified to `/thank-you-a`, everyone else to `/thank-you-b`. If the form tool can't do logic: a 10-line inline script can read the field values on submit and set `window.location`. The contract is just "qualified → A, else → B."
3. Both submissions must still create the contact in {{CRM}} <!-- source: intake §6 --> with all answers (native form integration, or a Zapier/webhook fallback: form tool → {{CRM}} "Create/Update Contact"). Map the answers to CRM properties so the team sees them before dialing.

### 2.3 Fire the event on /thank-you-a only

1. On `/thank-you-a`, below the base pixel code, add:
   ```html
   <script>fbq('trackCustom', 'QualifiedLead');</script>
   ```
   `/thank-you-b` gets the base code ONLY (PageView) — never the event.
2. Events Manager → your dataset → **Test events** tab → open `/thank-you-a` in another tab → confirm `QualifiedLead` appears within seconds.
3. When building the ad set (`META-ADS-SETUP.md` §2.2) select `QualifiedLead` as the conversion event. (If you prefer standard events for Advantage+ compatibility, `fbq('track','Lead')` on page A only is an acceptable alternative — the principle is identical: **the event only exists on the qualified page.**)

### 2.4 Full dry-run (do this before spending a dollar)

1. Open the landing page via the ad's full URL (with UTMs, Part 4).
2. Submit the form with **qualifying** answers → land on `/thank-you-a` → Test Events shows `QualifiedLead`; {{CRM}} shows the contact with answers + UTMs.
3. Submit again with **non-qualifying** answers → land on `/thank-you-b` → **no** `QualifiedLead` in Test Events; {{CRM}} still shows the contact.
4. Confirm the intake/sales team received both leads through whatever notification path they use — the speed-to-lead cadence in `../03-ads/ADS-PLAYBOOK.md` depends on this.

## Part 3 — CAPI (Conversions API): send closed-won outcomes back to Meta

The third data layer: tell Meta which leads actually **became paying customers**, so it optimizes toward buyers, not form-fillers. Volume will often be low (a few per week) — that's fine and still valuable.

**Recommended path — {{CRM}}'s native Meta integration** (if the CRM is the system of record for deals):
1. In {{CRM}}, install/connect the Meta (Facebook) Ads integration and link the ad account.
2. Enable conversion-event syncing and map a lifecycle/deal-stage trigger to a Meta event: trigger = deal enters the won/paid stage, event name = `Purchase` (with a value — a static median customer value from the avatar research works) or a custom `ClosedWon`.
3. Match quality depends on email/phone being present on the contact — they will be (form-captured).

**Fallback path** if the native mapping can't target the right stage: Zapier (or equivalent) — trigger "deal stage changed → won" → action "Facebook Conversions: Send Conversion event" (user email + phone hashed automatically). Either path is fine; **pick one, don't run both** (duplicate events).

Verification: Events Manager → dataset → the event appears with "Server" channel a few minutes after a test stage change.
<!-- /MODEL -->

<!-- MODEL: app -->
## Part 1 — Choose the measurement stack: Meta SDK or MMP

1. **Decide once:** the **Meta SDK** directly (simplest; fine if Meta is your only/primary paid channel) or an **MMP** — AppsFlyer, Adjust, or similar <!-- source: intake §6 --> (required once you run multiple ad networks or need SKAdNetwork management done for you). Don't run both attribution paths for the same events.
2. Meta side: business.facebook.com → **Events Manager → Connect data sources → App** → register the app (both iOS and Android app IDs), or connect the MMP as the app's data source per the MMP's Meta-integration guide.
3. Install the SDK/MMP kit in the app build; verify install events appear in the Events Manager app dataset (or the MMP dashboard) from a test device.

## Part 2 — Define the optimization event (the decision everything hangs on)

**Never optimize on installs.** Define the event that predicts a valuable user:

1. Pick ONE down-funnel event as the optimization target: {{OPTIMIZATION_EVENT}} <!-- source: intake §1 — typically trial_started, activation (the "aha" action completed), or first subscription --> — the earliest event that reliably separates future payers from tourists.
2. Instrument it in the app (SDK `logEvent` / MMP in-app event), with a stable snake_case name. Log it **after the user has actually done the thing**, not on screen-view.
3. Also instrument the supporting funnel: install → onboarding_complete → {{OPTIMIZATION_EVENT}} → subscription/purchase (with value) — you'll need the ratios to judge campaigns.

## Part 3 — iOS: AEM / SKAdNetwork configuration

1. In Events Manager (or the MMP's SKAN config), set the **Aggregated Event Measurement priority list** so {{OPTIMIZATION_EVENT}} occupies a top slot; map SKAdNetwork conversion values so the event is distinguishable.
2. Accept the constraints and plan around them: iOS event counts are modeled/delayed (24–72h), user-level attribution is gone, and fine-grained breakdowns won't match Android. **Judge iOS tests on longer windows** (`META-ADS-SETUP.md` §2.4).
3. Implement the ATT prompt properly (pre-prompt explainer improves opt-in; higher opt-in = better optimization data).

## Part 4a — Web-to-app UTM handling (if ads land on a web page first)

1. Ads carry the full UTM template (Part 4). The landing page's store buttons must pass campaign context through a **deferred deep link** (MMP OneLink/AppLink, or Meta deep links) so the install is attributed to the ad and the app can read `utm_content` (the creative ID).
2. Persist the received campaign/creative ID onto the user record in {{CRM}} <!-- source: intake §6 --> / your backend at signup — this is the join key that makes "which hook prints money" answerable later.

## Part 5 — Dry-run (before spending a dollar)

1. Fresh install on a test device via the ad's full URL / test-ads flow.
2. Complete onboarding and trigger {{OPTIMIZATION_EVENT}} → confirm it appears in Events Manager (App events / Test events) or the MMP live view, attributed with campaign + `utm_content`.
3. Confirm the user record in your backend/{{CRM}} carries the creative ID.
4. Repeat on iOS specifically and confirm the SKAN/AEM conversion value registers.
<!-- /MODEL -->

<!-- MODEL: ecom -->
## Part 1 — Create the dataset (pixel) and standard-event mapping

1. business.facebook.com → **All tools (≡) → Events Manager** → **Connect data sources → Web → Connect**. Name the dataset `{{BUSINESS_NAME}} Store` <!-- source: PRD -->.
2. **Prefer the platform's native integration** ({{LANDING_PLATFORM}} <!-- source: intake §6 --> — e.g. the ecommerce platform's official Facebook/Meta channel app): it installs the pixel, maps the standard events, AND sends server-side CAPI events with proper deduplication in one step. Manual base-code install is the fallback for custom stacks.
3. Required standard-event mapping — verify each fires with correct parameters:
   - `ViewContent` (product pages, with `content_ids`)
   - `AddToCart`
   - `InitiateCheckout`
   - **`Purchase` — with `value` and `currency`. This is the optimization event.** No value = no value optimization later; treat a value-less Purchase as broken.
4. Verify with the **Meta Pixel Helper** extension on a product page and through checkout.

## Part 2 — Server-side CAPI

1. If the platform integration from Part 1 is active, **CAPI is included** — confirm in Events Manager that Purchase events show both "Browser" and "Server" channels with a good deduplication rate (matching `event_id`s).
2. Custom stack fallback: implement CAPI from the order webhook (server sends `Purchase` with `event_id` matching the browser pixel's, plus hashed email/phone). One implementation only — duplicate un-deduplicated events corrupt reporting AND optimization.
3. Event Match Quality: aim for "Good" or better on Purchase (email + phone + name fields passed, hashed).

## Part 3 — Dry-run (before spending a dollar)

1. Open a product page via the ad's full URL (with UTMs, Part 4) → Pixel Helper shows `ViewContent` with the right `content_ids`.
2. Complete a test order (100% discount code or test gateway) → Test Events shows `Purchase` with the correct value/currency, on both Browser and Server channels, deduplicated.
3. Confirm the order in the store admin carries the UTMs (platform order attributes, or a UTM-capture snippet writing to order notes/{{CRM}} <!-- source: intake §6 -->) — `utm_content` = creative ID must be queryable per order.
<!-- /MODEL -->

## Part 4 — Naming + UTM convention (the join key for measurement — universal, all models)

Every ad's URL parameters (Ads Manager ad-level **URL parameters** field — paste once per ad):

```
utm_source=meta&utm_medium=paid&utm_campaign={{campaign.name}}&utm_content=<AD_ID>&utm_term={{adset.name}}
```

- `<AD_ID>` is the creative's ID from `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`, format `A<avatar>-H<hook>-M<meat>-C<cta>-v<variation>` (e.g. `A1-H07-M2-C1-v3`). The `{{campaign.name}}`/`{{adset.name}}` dynamic parameters are filled by Meta automatically — leave them literal.
- **The ad name in Ads Manager must equal the AD_ID.** That makes platform spend exports joinable to per-creative spend, and the `utm_content` captured on contacts/orders/users joinable to per-creative results. This is what makes "which hook prints money" answerable per `../05-measurement/MEASUREMENT.md`.
- Capture UTMs at the conversion record: native form UTM capture in {{CRM}}, hidden form fields, order attributes, or deep-link params — whichever the kept model above specifies.

## Part 5 — GA4 parity (secondary; don't block launch on it)

Add the GA4 tag to the landing/conversion pages the same way as the pixel, and register the value event as a GA4 key event (e.g. Admin → Events → Create event on the qualified/purchase page or event). This keeps existing analytics and reports coherent with the new funnel. Never let GA4 numbers arbitrate ad decisions — it's a parity check, not the optimization source.

## Part 6 — Maintenance (universal, all models)

- Re-run the dry-run after **any** change to the form, questions, routing logic, app onboarding, checkout, or page URLs.
- Never add the value event to any other page/screen ("just to test"). One place, one event.
- **A suspiciously improved cost-per-result while the team reports junk quality = the gate is broken open** (everyone reaching the qualified path / event firing too early) — dry-run immediately.
