<!--
TEMPLATE: META-ADS-SETUP.template.md
PURPOSE: Generates a zero-assumed-knowledge, click-by-click walkthrough for setting up Meta
  advertising for the client: business foundation → ABO testing campaign → CBO scaling →
  weekly ops. Companion to ../../templates/walkthroughs/TRACKING-SETUP.template.md (tracking
  MUST be instantiated and completed before any campaign launches) and the generated
  ../03-ads/ADS-PLAYBOOK.md (ongoing operating rules).
INPUTS REQUIRED BEFORE INSTANTIATION:
  - PRD: business name, domain(s), niche, primary conversion action
  - Intake interview: §1 business model & offer economics, §4 budget, §5 geography/scope,
    §6 tech stack (existing Meta assets, ad-account history), §7 compliance
  - Generated docs: CREATIVE-PRODUCTION-SPEC.md (asset IDs), TRACKING-SETUP.md (events)
GENERATOR RULES:
  - Keep exactly ONE <!-- MODEL: ... --> block per variant point; delete the others.
  - SPECIAL AD CATEGORIES: the generator MUST verify whether {{NICHE}} falls under Meta's
    special ad categories (credit, employment, housing, social issues/elections/politics)
    and write §1.4 with the correct instruction — flag ON with its targeting restrictions
    explained, or flag OFF with the "don't select it to be safe" warning. Do not leave both.
  - Replace every {{PLACEHOLDER}}; none may survive into the generated doc.
QA CHECKLIST (run after instantiation):
  [ ] No {{...}} placeholders or <!-- MODEL --> / <!-- source --> comments remain
  [ ] §1.4 special-category determination is stated definitively for this niche
  [ ] The conversion event named in §2.2 exactly matches TRACKING-SETUP.md
  [ ] Budget figures in §2.2/§3 are consistent with intake §4 and the ads playbook
  [ ] Campaign/ad-set/ad naming matches the ads playbook and the creative-ID system
-->

# Meta Ads Setup — Click-by-Click

Zero-assumed-knowledge walkthrough for setting up Meta advertising for {{BUSINESS_NAME}} <!-- source: PRD --> the way the playbook prescribes: **ABO for testing, CBO for scaling, broad audiences, optimize only on the event that means real value.** Companion docs: `../03-ads/ADS-PLAYBOOK.md` (the ongoing operating rules) and `TRACKING-SETUP.md` (do the pixel/tracking steps BEFORE launching any campaign).

Meta renames UI elements a few times a year; if a label below doesn't match exactly, look for the closest equivalent — the structure (Business Portfolio → Ad Account → Events Manager dataset → Campaign → Ad Set → Ad) has been stable for years.

---

## Part 1 — Business foundation (one-time, ~1 hour)

### 1.1 Business Portfolio (formerly "Business Manager")

1. Go to **business.facebook.com** while logged into a personal Facebook account that will administer the business (the personal account is only a key; nothing posts from it).
2. If the business already has a Business Portfolio (check with whoever ran past Facebook ads — historical UTM data often reveals prior campaigns), **use it**; don't create a duplicate. Click the portfolio name top-left to see which one you're in.
3. If none exists: **Create a business portfolio** → Business name "{{LEGAL_BUSINESS_NAME}}" <!-- source: PRD --> → your name → business email → **Submit**, then verify the email.
4. **Settings (gear icon, bottom left) → People** → add at least one other admin (bus-factor protection — a locked-out sole admin is a common disaster).
5. **Settings → Business info** → complete legal name, address, phone. Incomplete profiles trigger more ad-review friction, especially in scrutinized verticals.

### 1.2 Facebook Page + Instagram

1. **Settings → Accounts → Pages** → **Add** → claim the existing business Facebook Page, or create one if none exists (a Page is required to run ads).
2. **Settings → Accounts → Instagram accounts** → **Add** → log into the business Instagram. Ads run placement-wide across both.

### 1.3 Ad account

1. **Settings → Accounts → Ad accounts**. If a legacy ad account exists and is in good standing, add/claim it — **account history helps**; an aged account with clean history gets smoother review than a brand-new one. <!-- source: intake §6 -->
2. Otherwise **Add → Create a new ad account** → name it `{{BUSINESS_NAME}} — Meta`, timezone **{{TIMEZONE}}** <!-- source: intake §5 -->, currency {{CURRENCY}} <!-- source: intake §5 -->. (Timezone/currency are permanent per account.)
3. Open **Ads Manager** (`adsmanager.facebook.com`) → **Billing & payments** → **Payment methods** → **Add payment method** → business card. Set the **account spending limit** (Billing → Account spending limit) to a comfort ceiling slightly above {{MONTHLY_BUDGET}} <!-- source: intake §4 --> so a runaway campaign can't exceed the monthly plan.
4. **Settings → Accounts → Ad accounts → Add people** → give the person running ads **Manage ad account (full control)**.

### 1.4 Domain + special-category check

1. **Settings → Brand safety and suitability → Domains** → **Add** → `{{ROOT_DOMAIN}}` <!-- source: PRD --> → verify by the **meta-tag** method (paste the tag into the site `<head>`) or DNS TXT record. Verifying the root domain covers subdomains (landing pages may live on a subdomain — see `LANDING-PAGE-BUILD.md`).
2. **Special ad categories:** {{SPECIAL_CATEGORY_DETERMINATION}} <!-- source: intake §7 — GENERATOR: verify whether {{NICHE}} falls under Meta's special ad categories (credit, employment, housing, social issues/elections/politics) and write ONE of: (a) "This niche IS a special ad category ([which]). You MUST declare it at campaign creation; expect restricted age/gender/zip targeting and plan creative-led targeting accordingly." or (b) "This niche is NOT one of Meta's special ad categories (those are credit, employment, housing, and social/political). Leave the special-category selector OFF when building campaigns. Do not select it 'to be safe' — it cripples delivery options for no reason." --> (If Meta's policy list changes, the campaign-creation screen will force the issue.)

### 1.5 Events Manager dataset (pixel / SDK)

Covered step-by-step in `TRACKING-SETUP.md`. **Do not launch campaigns until the tracking exists, the optimization event fires correctly, and a test event has been verified in Test Events.** Campaigns optimized on a broken event burn the budget teaching Meta the wrong thing.

---

## Part 2 — The testing campaign (ABO)

The unit of testing is: **one creative concept → 5–10 variations → one ad set → its own budget.** Variations means: same core creative with different music, shorter/longer cut, starting a few seconds later, different opening text, different thumbnail — not different concepts.

### 2.1 Create the testing campaign shell (once)

1. Ads Manager → **+ Create**. Buying type: **Auction**.
2. Objective and conversion location — model-specific:

<!-- MODEL: lead-gen -->
   - Objective: **Leads**. Click **Continue** → choose the **manual** setup (not the Advantage+ shortcut — you need ad-set-level budget control for ABO).
<!-- /MODEL -->
<!-- MODEL: app -->
   - Objective: **App promotion**. Choose the **manual** app-promotion setup (not the Advantage+ shortcut — you need ad-set-level budget control for ABO). Select the app; the Meta SDK or MMP integration from `TRACKING-SETUP.md` must already be reporting app events. **Optimize for a down-funnel event (trial started / activation), not installs** — install-optimized campaigns fill the funnel with tourists. Note the iOS constraints: Aggregated Event Measurement / SKAdNetwork limit event granularity and delay reporting; configure per `TRACKING-SETUP.md` before judging any test.
<!-- /MODEL -->
<!-- MODEL: ecom -->
   - Objective: **Sales**. Choose the **manual** sales campaign (not the Advantage+ shortcut — you need ad-set-level budget control for ABO). Conversion location: **Website** (catalog/DPA is a later layer once the pixel has purchase volume — don't start there).
<!-- /MODEL -->

3. Campaign name: `TEST | ABO | {{OFFER_SHORT_NAME}}` <!-- source: intake §1 --> (naming rules in `../03-ads/ADS-PLAYBOOK.md`).
4. **Special ad categories:** per §1.4. **Advantage campaign budget: OFF.** ← This is the switch that makes it ABO; budget will be set per ad set. Click **Next**.

### 2.2 Build one test ad set per concept

1. Ad set name: `T-YYYYMMDD-<conceptID>` (concept IDs come from `../04-creative-production/CREATIVE-PRODUCTION-SPEC.md`).
2. Conversion settings — model-specific:

<!-- MODEL: lead-gen -->
   - **Conversion location: Website.** **Performance goal: Maximise number of conversions.** **Dataset/Pixel:** the business dataset. **Conversion event: `QualifiedLead`** (the custom event from `TRACKING-SETUP.md` — NOT the default "Lead", which counts unqualified submissions too). If the event shows a red "no recent activity" flag, fix tracking first.
<!-- /MODEL -->
<!-- MODEL: app -->
   - **App events** via the SDK/MMP. **Performance goal: maximise app events → select the optimization event defined in `TRACKING-SETUP.md`** (trial_started / activation — not installs). On iOS confirm the event sits in an AEM-prioritized slot.
<!-- /MODEL -->
<!-- MODEL: ecom -->
   - **Conversion location: Website.** **Performance goal: Maximise number of conversions** (move to value optimization once ~50+ purchases/week exist). **Dataset/Pixel:** the store dataset. **Conversion event: `Purchase`** — with value passing verified per `TRACKING-SETUP.md`.
<!-- /MODEL -->

3. **Budget & schedule:** Daily budget **{{TEST_ADSET_DAILY_BUDGET}}** <!-- source: intake §4 --> per test ad set (at {{MONTHLY_BUDGET}}/month total, run 3–5 concurrent test ad sets and leave most of the budget for scaling — split guidance in the playbook). Start date: tomorrow morning; no end date.
4. **Audience — broad ("the creative is the targeting"):**
   - Locations: {{GEO_TARGETING}} <!-- source: intake §5 --> as the base. When a concept targets a location-specific avatar, drop pins/radii for those areas instead.
   - Age: {{AGE_RANGE}} <!-- source: avatar research --> (set from actual customer data, not guesses). Gender: All — unless the creative itself is gendered, and even then prefer letting the creative select.
   - **Detailed targeting: leave empty.** Delete any interest suggestions. **Advantage+ audience: ON** (it's the default; broad is the point).
5. **Placements: Advantage+ placements (automatic).** Don't hand-pick.
6. Click **Next** to the ad level.

### 2.3 Load the 5–10 variations as ads

1. Ad name: `<adID>` from the creative spec, e.g. `A1-H07-M2-C1-v3` (avatar-hook-meat-CTA-variation; **this exact ID is also the `utm_content` value** — see `TRACKING-SETUP.md`).
2. **Identity:** the business Page + Instagram account.
3. **Ad setup: Create ad → Manual upload.** Upload the video/image. Supply 4:5 or 1:1 for feed and 9:16 for Reels/Stories if the creative kit includes them.
4. **Primary text / Headline / Description:** from the creative spec's copy block for that ad ID.
5. **Call to action button:** per the ad's CTA component (e.g. Book now / Learn more / Download / Shop now).
6. **Destination:** the avatar's landing page (or app-store destination per the model) **with the UTM template** from `TRACKING-SETUP.md` pasted into **URL parameters**.
7. Duplicate the ad (⋮ → **Duplicate**) for each remaining variation, swap the creative file + name, keep everything else.
8. **Publish.** Expect "In review" for minutes to ~24h.

### 2.4 Reading a test (give it 3–5 days or ~2,000 impressions per ad before judging)

In Ads Manager, columns → **Customize columns**: Amount spent, Impressions, CPM, CTR (link), Cost per result (result = the optimization event), Frequency, plus video plays 3s/ThruPlay for videos.

- **Winner:** cost per result meaningfully below the account average (the playbook sets the target bands), with CTR ≥ ~1% as a secondary signal.
- **Loser:** 2–3× the target cost after fair spend (≥ roughly 2–3× your target cost-per-result spent on that ad) → turn the ad off.
- **Believed-in creative that flopped:** the "golden BB" case — Meta may have trained it on the wrong pocket of the audience. **Turn it off, duplicate it into a brand-new ad set** (new ad set = new learning), give it 2–3 days. One retry only.

## Part 3 — Scaling (CBO): one campaign per angle

1. When a test ad wins, create (once per angle) `SCALE | CBO | <angle>` — e.g. `SCALE | CBO | Talking-Head`, `SCALE | CBO | Static-Callouts`, `SCALE | CBO | Testimonial-Proof`. Same build as 2.1 **but Advantage campaign budget: ON**, budget at campaign level.
2. Inside, keep 1–3 ad sets (broad geo; optionally one tighter-radius ad set). **Duplicate the winning ad from the test campaign into the scale campaign** (⋮ → Duplicate → select destination). Never move the original — copy it, leave the test ads' history intact.
3. Campaign budget: start at {{SCALE_CAMPAIGN_DAILY_BUDGET}} <!-- source: intake §4 --> per active scale campaign; raise by **≤20% every 2–3 days** (bigger jumps rewind learning).
4. Prune: an ad whose cost per result drifts >50% above target for a week gets turned off; the 70/20/10 machine (playbook) replaces it. **Never pause things because you're bored of them** — "boredom is the founder's problem, not the market's."

## Part 4 — Weekly ops checklist (30–45 min, same day every week)

1. Launch this week's new test ad set(s) — {{WEEKLY_CREATIVE_TARGET}} <!-- source: intake §4 --> new creatives (the volume rule: weekly creatives ≈ monthly spend ÷ $1,000).
2. Judge last week's tests: promote winners to their angle CBO; kill losers; golden-BB retry at most one.
3. Check scale campaigns: cost per result vs target, frequency (>3.5 on a narrow local audience = creative fatiguing — feed newer variations), budget nudges ≤20%.
4. Check Events Manager for event health (any red flags on the optimization event).
5. Log the week's numbers per `../05-measurement/MEASUREMENT.md`.
6. <!-- MODEL: lead-gen -->Confirm speed-to-lead is holding: every qualified lead contacted within minutes during business hours (playbook nurture cadence).<!-- /MODEL --><!-- MODEL: app -->Confirm onboarding health: install→activation rate steady; any drop means the ads are fine but the first session is leaking.<!-- /MODEL --><!-- MODEL: ecom -->Confirm fulfillment/CX health: abandoned-checkout flows firing, delivery promises holding — ads scale problems as fast as they scale sales.<!-- /MODEL -->

## Common failure modes

- **Optimizing on the wrong event** (a shallow event — raw Lead, install, add-to-cart — instead of the qualified/valuable event) — the single most expensive mistake; recheck after any form/page/app change.
- **Editing a running ad** (new text, new thumbnail) — resets learning. Duplicate-and-replace instead.
- **Adding interest targeting "to help it"** — fights the broad-audience approach; the creative targets.
- **Judging in 24 hours** — daily costs swing wildly at modest spend levels; judge on 3–5 day windows.
- **One mega-campaign with every concept in one ad set** — budget pools to one early winner and the rest never get tested; keep one concept per test ad set.
