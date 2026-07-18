# Pylon × TOJ Partnership — Reference Archive

**Owner:** Kyron Cumby · Trail of Joy Management Group, LLC
**Partner:** Pylon Football (pylonfootball.com)
**Contract shape:** Pylon contracts TOJ (not Kyron W-2)
**Scope:** Tech + Sales + Scouting + Media — four operational functions delivered by TOJ, all contracted through Kyron

This repo is the **living reference archive** of the Pylon × TOJ partnership build spec. It is not the code repo — the code lands in `kcumby2-wq/TojCampaign` on branch `claude/pylon-partnership-2026` (per V2 handoff). This repo holds the layered decision docs.

## Where to start

See [`docs/handoffs/README.md`](docs/handoffs/README.md) — the layered spec index with what's locked at each version + open questions rollup.

## The frame in one paragraph

Pylon Football has mature infrastructure — Sports Thread runs their rankings, Team Inn runs their housing, Jordan Brand + Wilson + Muscle Milk + Battle + Overtime + BallerTV + Whistle are their top-tier sponsors. TOJ does not build parallel versions of any of that. TOJ is the layer above: production (Team Media Packages, Live Event Posting), mid-market sponsor sales, athlete-side pipeline (Subject Report subscription, Recruiting Concierge), content operations (a Pylon-staffed pod running on TOJ-built infrastructure across 4 pillars — Ritual, Scale, Prestige, Capture), and everything the Pylon corp team doesn't have bandwidth to reach one-to-one across 1,261 teams and 117,904 athletes. **North star: save Pylon time, produce Pylon revenue.** Every SKU either saves Pylon labor or opens a revenue line Pylon isn't monetizing today.

## Year-1 revenue lines locked (as of V2.8)

**14 SKUs across three domains:**

- **Creative (10):** Team Media Package Recap/Season/Combine (#1a/1b/1c), Merch drops per-team + per-event (#5a/5b), Live Event Posting Package (#10), Player Snapshot/Story/Feature (#12/13/14)
- **Scouting (2):** Digital Scouts On-Field Transcript (#3), Subject Report Athlete Subscription (#9), Recruiting Concierge (#11)
- **Efficiency (5):** Team Analytics (#2), Mid-market sponsors Field/Team Presenting/Content (#4a/4b/4c), Email database campaigns (#4d), CRM platform fee (#6), City League Host Toolkit (#7)
- **Vertical (1):** Girls Flag NIL Package (#8)

**Year-1 TOJ take estimate: $700K–$1.2M** across all lines. Plus recurring newsletter revenue.

## Content operations (V2.5 layer)

- 4 content pillars owned by TOJ system, staffed by Pylon pod: Ritual (Sunday Salvo, Power Rankings Show, Family Night Live) · Scale (AI Season Recaps, Extended Rankings, matchup previews, Play of the Week) · Prestige (Pylon Path docu-series, Live Draft broadcasts, Coach Corner, podcast) · Capture (Off-Season Signal newsletter, Parent Playbook, Ambassador program, Rivals Killer news)
- Content Pod org: Creative Lead (Pylon employee) → Head of Video / Head of Editorial / Head of Social / Head of Automation-Ops / Girls Flag Lead + rotating Subject Media contract crew
- Sponsor commission on content assets: ~$194K/year TOJ take at 25% of estimated $777K gross

## Media methodology (V2.8 layer)

- **Content Taxonomy 1/2/3:** every event produces at minimum 1 POV Reel + 1 Action Photos Carousel + 3 Support pieces = **6-piece deliverable minimum per team per event**
- Visual Direction rubric: cinematic realism + shallow DOF + high-contrast + candid emotion + dynamic body positioning
- Player Package Sales Guide: 6-step vendor booth close with 25% OFF referral loop + creator attribution
- Before/During/After event workflow codified as `skills/event-week-runbook/` in pylon-os

## White-label rules (V2.7 layer)

- **Pylon is the only customer-facing brand.** Subject Media + Subject Report stay live inside tojcampaign as TOJ's own proof-of-concept + pitch collateral only.
- Kyron's 4-function scope (Tech + Sales + Scouting + Media) added to the Partnership Memo.
- Recruiting Concierge added as SKU #11 (rivals-killer positioning, powered by Optimum Coaches Directory).
- TAPPS cross-recruit pathway added as strategic memo section (Optimum's TAPPS partnership → summer Pylon acquisition of ~250 Texas private/parochial programs).

## Media page architecture (V2.9 layer)

- No Xpand Sports integration — Pylon media checkout is custom-built inside tojcampaign
- `/pylon-media.html` landing + `/pylon-team-packages.html` team checkout + `/pylon-player-packages.html` player checkout
- Tiered vendor booth staffing model (small: rotating creators / mid: dedicated seller / large: sellers + booth manager)

## What lives in this repo vs the code repo

| Where | What lives there |
|-------|-----------------|
| `kcumby2-wq/Pylon` (this repo) | Reference archive — layered handoff docs · README index · open questions rollup |
| `kcumby2-wq/TojCampaign` branch `claude/pylon-partnership-2026` | The build — Partnership Memo, DB migration, routes, admin UIs, player/team checkout pages, Live Event Console, Live Card script |
| `kcumby2-wq/pylon-os` (to create) | Pylon operating brain (federation peer to `hooks-os`) — CLAUDE.md, skills library, per-team/athlete/event/sponsor data folders |

## Status

Handoff spec locked through V2.9 (2026-07-18). Execution has not begun on `claude/pylon-partnership-2026`. Open questions: 30 across all layers — full list in the handoff index.

---

*This archive is the source of truth for the partnership build. Changes to the spec land here first as a new versioned addendum (`v3.md`, `v3.5-*.md`, etc.), then execute in the code repo. Never edit `v2.md` through `v2.9-*.md` after their layer commits — those are historical.*
