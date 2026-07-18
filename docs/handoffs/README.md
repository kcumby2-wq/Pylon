# Pylon × TOJ Handoff Spec — Layered Index

**Total layers to date:** 6 (V2 → V2.5 → V2.7 → V2.8 → V2.9 → V3.0)
**Superseded:** V1 (see `_archived/`)
**Last updated:** 2026-07-18

Every layer builds on the prior. **Read in order.** No layer replaces an earlier one — each locks additional decisions, adds SKUs, appends schemas, and answers a subset of the open-questions list.

Every layer is written for a Claude Code session with GitHub write access to `kcumby2-wq/TojCampaign` on branch `claude/pylon-partnership-2026`. Nothing in these docs has been executed as code yet.

---

## The 5 layers · what's locked at each

### [`v2.md`](v2.md) · Foundation · 37KB

**Locked:**
- The 4-principal structure (Kyron + 3 TBDs) and the compensation flip (Pylon contracts TOJ, not Kyron W-2)
- The 3 operational domains: Scouting · Creative · Efficiency
- **10 core SKUs** with prices + splits (Team Media 1a/1b/1c · Team Analytics 2 · Digital Scouts 3 · Sponsors 4a/4b/4c/4d · Merch 5a/5b · CRM platform 6 · City League Host 7 · Girls Flag NIL 8 · Athlete Subscription 9 · Live Event Posting 10)
- 3-phase sales sequence (pre/during/post) — 12 canonical templates
- Full DB schema: `pylon_teams`, `pylon_athletes`, `pylon_events`, `pylon_registrations`, `pylon_package_orders`, `pylon_athlete_subscriptions`, `pylon_sponsors`, `pylon_sponsor_deals`, `pylon_email_campaigns`, `pylon_merch_drops`, `pylon_city_league_hosts`, `pylon_sales_sequences`, `pylon_sequence_runs`, `pylon_live_posts`
- Route surface: `/api/pylon/*` (teams, athletes, events, packages, subscriptions, sponsors, sequences, live-posts)
- Admin UI: `/admin/pylon.html` (12 tabs)
- Team-facing checkout: `/pylon-packages.html`
- Athlete-facing subscription: `/pylon-athlete-subscribe.html`
- Live Event Console: `/admin/pylon-live-console.html` + `scripts/pylon-live-card.mjs`
- Partnership Memo (v2 reframe): `docs/pylon-toj-partnership-memo.md`
- pylon-os federation-peer scaffold (Priority 3 — creates `kcumby2-wq/pylon-os` after Priority 2 is on branch)

**Ships:** 14 file paths, 1 memo, 1 migration, 1 seed, 1 cron, 1 script.

**Open questions from V2:** 11.

---

### [`v2.5-content-ops.md`](v2.5-content-ops.md) · Content pod + 4 pillars · 24KB

**Locked:**
- TOJ owns all 4 content pillars (Ritual · Scale · Prestige · Capture)
- Content Pod org chart: Creative Lead (Pylon) → 5 heads + Girls Flag Lead + Subject Media contract crew
- Year-1 pod cost: ~$500K–$700K · break-even month 6 · profit-positive month 10
- 14 sponsor slots on content assets = **~$777K gross year-1 · TOJ take ~$194K at 25% commission** (on top of the 10 SKU lines)
- Ambassador program: 100 athletes as distributed creators · $50 standard / $150 featured / $500 flagship monthly stipend
- Off-Season Signal newsletter (Free tier + Premium $9.99/mo)
- Additional DB tables: `pylon_content_pieces`, `pylon_content_performance`, `pylon_ambassadors`, `pylon_ambassador_posts`, `pylon_newsletter_subscribers`, `pylon_newsletter_issues`
- Additional admin surfaces: content calendar, ambassadors, newsletter, content performance
- Additional public pages: `/pylon-newsletter.html`, `/pylon-ambassadors.html` (in applied_pending_review mode)
- 15 additional pylon-os skill folders (creative-lead, sunday-salvo, power-rankings-show, family-night-live, ai-season-recaps, extended-rankings, matchup-previews, play-of-the-week, pylon-path-doc, live-draft-broadcast, coach-corner, pylon-podcast, newsletter-signal, parent-playbook, ambassador-program, rivals-killer, girls-flag-content)
- Voice authority guardrail: `POST /api/pylon/content/:id/approve` checks `PYLON_APPROVERS` env var (server-side enforcement of "Pylon is the voice")

**Open questions from V2.5:** 6.

---

### [`v2.7-white-label.md`](v2.7-white-label.md) · Brand rules + Recruiting Concierge + TAPPS · 19KB

**Locked:**
- **Pylon is the only customer-facing brand.** No Subject Report or Subject Media logo, name, or reference on any team/athlete/parent/coach/sponsor/host-facing surface.
- Subject Report + Subject Media stay LIVE inside tojcampaign as TOJ's own proof-of-concept portfolio + pitch collateral only (used to close future non-Pylon deals)
- Kyron's TOJ scope = 4 functions (Tech + Sales + Scouting + Media), added to the Partnership Memo
- **SKU #11: Pylon Recruiting Concierge** — $99/mo OR $499/season/athlete · powered by Optimum Coaches Directory · rivals-killer positioning · year-1 gross estimate $584K–$1.75M · TOJ take $263K–$788K
- **TAPPS cross-recruit pathway** — memo-level growth channel · target 40–60 TX private/parochial teams onboarded via Optimum's existing TAPPS partnership · incremental gross to Pylon $200K+
- 5 naming decisions Kyron must confirm (default fallback: Option A across the board)
- 4 additional DB tables: `pylon_recruiting_subscriptions`, `pylon_recruiting_outreach`
- 6 additional routes: `/api/pylon/recruiting/*`
- New public page: `/pylon-recruiting.html`
- New pylon-os skill: `skills/tapps-pathway/`
- CLAUDE.md addendum (3 new operating rules)

**Open questions from V2.7:** 5.

---

### [`v2.8-media-methodology.md`](v2.8-media-methodology.md) · Content taxonomy + Player SKUs · 17KB

**Locked:**
- **Content Taxonomy is the operational spec for every Pylon media SKU:**
  - Content 1 = POV Reel per event per star athlete
  - Content 2 = Action Photos Carousel per event per team
  - Content 3 = Support Content (3 variants: team highlight + single shots + individual focus)
  - **Minimum 6 pieces per team per event** (contractual deliverable spec)
- Subject Media's Visual Direction rubric is the Pylon QC standard (cinematic realism + shallow DOF + high-contrast + candid emotion + dynamic body positioning)
- **3 new player-level SKUs (#12/#13/#14):** Player Snapshot $69 / Player Story $99 / Player Feature $199 · sold at vendor booth · 40% TOJ take
- 6-step Player Package Sales Guide codified as `skills/player-package-sales/`
- 25% OFF referral loop with creator attribution: `pylon_creator_referrals` + `pylon_referral_conversions` tables
- Before/During/After event workflow codified as `skills/event-week-runbook/`
- Xpand Sports integration: **Option A recommended** (integrate first, migrate later) — superseded by V2.9

**Open questions from V2.8:** 6.

---

### [`v2.9-media-page.md`](v2.9-media-page.md) · Custom media page + booth staffing · 12KB

**Locked:**
- **Option B superseded Option A** — build a Pylon-custom media page inside tojcampaign. No Xpand Sports subdomain integration.
- `dash.xpandsports.com` stays alive as Subject Media's proof-of-concept dashboard (Kyron uses for non-Pylon prospects)
- 3-page architecture: `/pylon-media.html` (landing) + `/pylon-team-packages.html` (team checkout) + `/pylon-player-packages.html` (player checkout)
- Design language locked: Pylon black + yellow + white sans-serif — NOT TOJ's cream/navy
- Delivery pipeline: Stripe checkout → creator assignment → QC → delivery via `pylon_media_assignments` table
- **Tiered vendor booth staffing:**
  - Small events (32–60 teams) → 1–2 creators rotate booth (zero incremental cost)
  - Mid events (60–120 teams) → 1 dedicated seller ($500/event) + 3–5 creators
  - Large events (120–265 teams) → 2 sellers + 6–8 creators + 1 booth manager ($750/event)
- Additional DB tables: `pylon_media_assignments`, `pylon_booth_staffing_plans` + column additions to `pylon_package_orders`
- `skills/booth-staffing/` skill file

**Open questions from V2.9:** 2.

---

### [`v3.0-national-coverage.md`](v3.0-national-coverage.md) · National coverage + Regional Coordinators · 12KB

**Locked:**
- **National coverage across all 5 Pylon territorial regionals** (Northeast · Southeast · Midwest · South Central · West) + international (Pylon Japan Mar 2027 pilot). **Replaces any prior "3-territory" framing.**
- **Kyron's physical operating presence:** Dallas + West Coast (Portland base 2026–2027, Seattle secondary) for the initial term; NYC/Queens relocation 2028+ aligned to his St John's transition
- **Pilot event stays anchored in Dallas** (South Central Regional stop, spring 2027) — TAPPS pathway warm, Hooks-adjacent, deepest talent pool
- **5 Regional Coordinators required** — hired in sequence based on where Kyron is physically present:
  1. West (Portland) — Q1 2026, colocated with Kyron for onboarding
  2. South Central (Dallas) — Q1 2026, colocated during Dallas swings
  3. Northeast (Philly/NY) — Q2 2026, remote until 2028 relocation
  4. Southeast (Atlanta/Tampa) — Q3 2026, remote + Subject Media contract crew support
  5. Midwest (Chicago/Indianapolis) — Q4 2026 OR defer to Q1 2027 based on cash flow
  6. International (Tokyo) — contract-only for Pylon Japan; permanent hire dependent on expansion volume
- Regional Coordinators are **TOJ contractors, not Pylon employees** (preserves TOJ IP portability across future partnerships)
- **Year-1 pod headcount = 11 total** (was 6 in V2.5, then 9, now 11): 6 Creative pod + 5 Regional Coordinators
- **Year-1 fully-loaded pod cost = $950K–$1.4M** (was $500K–$700K in V2.5) — break-even shifts from month 6 → month 8–10
- 8 Partnership Memo patches (M1–M8) covering scope statement, operating presence section, domain amendments, hire-sequence timeline, approval-gate updates, exit clause protection
- 3 new pylon-os skills: `regional-coordinator/`, `coverage-parity/`, `travel-triage/`
- `skills/tapps-pathway/` amended — South Central Coordinator (Dallas) becomes operational owner after Kyron's Optimum pitch

**Open questions from V3.0:** 4.

---

## Total open questions across all layers: 34

Rolled up from all 5 layers. Answer these to unblock the build.

### From V2 (11):

1. **Stripe account** — TOJ's existing or a Pylon-partnership sub-account?
2. **Optimum sub-agreement contact** — who at Optimum signs?
3. **First pilot event** for Digital Scouts + Live Event Console
4. **Sponsor prospect list** — existing mid-market relationships to seed the CRM
5. **Pylon-corp API access** — does Pylon Football have a registration API to integrate with?
6. **International currency** — Stripe multi-currency vs Japan-side payment partner for Pylon Japan Mar 2027?
7. **Sports Thread API access** — data feed to pull rankings + push grade/stat data?
8. **Team Inn API / booking link format** — how does TOJ embed Team Inn booking flows?
9. **Girls Flag NIL Night format** — is Subject Media already producing NIL Night content?
10. **City League host application review authority** — Pylon corp, TOJ, or joint?
11. **Live Event Console operator staffing** — hire dedicated crew, or Subject Media mentorship crew handles both?

### From V2.5 (6):

12. **Legal structure for ambassador stipends** — flow through TOJ, Pylon, or joint entity? Impacts 1099 + minor guardrails + NCAA compliance.
13. **Newsletter ESP + rate limits** — what does `utils/email/` use today? At 50K subscribers × weekly, throughput ceiling?
14. **Content Pod hiring timeline** — Creative Lead hired before, in parallel, or after V2 signature?
15. **Girls Flag Content Lead** — outside candidate (TOJ helps source) or promoted from within (Pylon shortlist)?
16. **Pylon Path S1 anchor athletes** — need 8–12 candidate represented athletes for casting.
17. **Ambassador program stipend rate** — $50/$150/$500 monthly tiers confirm or override?

### From V2.7 (5):

18. **Naming picks** — 5 row-by-row selections (default Option A if unanswered)
19. **Optimum warm intro** — BD lead vs founder vs product — determines 30-day vs 90-day close
20. **TAPPS relationship path** — through Optimum's TAPPS contact or direct?
21. **Recruiting Concierge public launch** — all 117K at once, or phase by region?
22. **Kyron's contracted rate** — fixed retainer + rev-share, or 100% rev-share?

### From V2.8 (6):

23. **Xpand Sports integration path** — A or B? *(**Answered in V2.9 → B**)*
24. **Existing Xpand Sports intake API** — order-intake endpoint or nightly export/import? *(**Answered in V2.9 → not needed, Option B chosen**)*
25. **Referral code format** — initials embedded (`JMILLER25`) or random slug?
26. **Creator payout structure** — 25% OFF + tip pool, or add flat per-package fee?
27. **Content 1 POV Reel scope** — 1 star athlete per team per event, or 1 per event across all teams?
28. **Vendor booth staffing** — dedicated seller, creators rotating, or Pylon event-staff cross-trained? *(**Answered in V2.9 → tiered by event size**)*

### From V2.9 (2):

29. **Pylon site typography** — exact display face on `pylonfootball.com` for design match
30. **Dedicated seller comp structure** — $500/event base confirm or override?

### From V3.0 (4):

31. **Midwest Coordinator timing** — Q4 2026 hire or Q1 2027 defer? Kyron confirms based on year-1 cash flow visibility around Q3 2026.
32. **International Coordinator (Tokyo)** — Pylon Japan Mar 2027 event only, or start scoping permanent hire in Q3 2026 in anticipation of broader international expansion (Europe, LATAM)?
33. **Regional Coordinator compensation structure** — proposal: $70K–$100K base + 5% of Coordinator's-territory-attributable revenue. Confirm or adjust.
34. **Nike Portland pitch** — do you want the pitch memo drafted for a walk-in meeting after you're settled in Portland?

**Effectively-open questions after V2.9 supersedes:** 30 (questions 23, 24, 28 answered in V2.9).

---

## Execution status

**Build has NOT begun.** Every layer above is a hand-off brief targeting the `claude/pylon-partnership-2026` branch in `kcumby2-wq/TojCampaign`. That branch does not yet exist. All 5 handoffs are drafted and locked; execution is the next step.

**Priority order per V2:**

1. **Partnership Memo** (V2 §Priority 1) — non-negotiable · Kyron must be able to email to Pylon owner within 48h of ship
2. **tojcampaign infrastructure** (V2 §Priority 2 + V2.5 + V2.7 + V2.8 + V2.9) — 8 deliverables from V2 + additions from every layer
3. **pylon-os operating brain** (V2 §Priority 3) — new repo `kcumby2-wq/pylon-os`, federation peer to `hooks-os`, only after Priority 2 is on branch AND Kyron greenlights

**Immediate execution blockers:**

- Optimum sub-agreement not signed (blocks launch of graded SKUs 1c, 2, 3, 9-Combine, and 11-Recruiting Concierge public launch)
- ~26 open questions unanswered (see rollup above)
- Sports Thread + Team Inn integration format unconfirmed

---

## How to navigate this repo going forward

- **When a new layer lands** (V3, V3.5, etc.), add it as a numbered file in `docs/handoffs/` and update this README's layer count + open questions rollup.
- **Never edit V2 through V2.9 after commit.** Those are the historical layers. Corrections go in a new layer.
- **The code repo** for actual execution is `kcumby2-wq/TojCampaign` on branch `claude/pylon-partnership-2026`. Nothing in this repo is executable — this repo is spec + reference.
- **The pylon-os brain** is a future repo (`kcumby2-wq/pylon-os`) — will be created after Priority 2 is on branch AND Kyron greenlights (V2 §What NOT to do #9).

---

*Every handoff at every layer was written to be dropped straight into a Claude Code session. Zero re-derivation needed.*
