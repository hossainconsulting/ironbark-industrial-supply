# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this project.

## What this is

Engagement workspace for the **Ironbark Industrial Supply engagement** — ten sprints
against the **Sales Cloud Consultant (Sales-Con-201)** track. Hemayet plays the
consultant at a fictional national industrial parts distributor: 140 reps across five
states, forecasting run out of spreadsheets, no territory model, an opportunity stage
set nobody agrees on, and Agentforce licensed but never switched on.

Ironbark Industrial Supply Pty Ltd is fictional; no real customer data is in here.

**Current state: scaffold.** `force-app/`, `seed/` and `evidence/` hold only
`.gitkeep`. Nothing has been built yet.

## The brief is discovery, not features

From `README.md`, and worth enforcing in any review: the brief is **not** "build
features." It is to work out what the sales organisation actually does before changing
anything. That discipline is what Sales-Con-201 tests and what separates a consultant
from an admin taking orders.

Practically: a stage model, a territory design or a forecast hierarchy proposed before
the discovery write-up exists is the wrong artefact, however good it is. Discovery
findings land in `deliverables/` first.

## The org

Target org alias **`ironbark`** — Developer Edition, org ID `00Dbm00000uRk89EAC`.

```bash
sf org display --target-org ironbark
```

Two items were outstanding as of the last README update and **both must be cleared
before any Opportunity data is seeded**:

1. **Currency locale is still USD.** Not settable through the API in a single-currency
   org. Setup → Company Information → Edit → Currency Locale → English (Australia) AUD.
   Seed opportunities before this and every amount is wrong — and the forecasting work
   is built on those amounts.
2. **Stock Salesforce sample data is still present** (13 Accounts). Purge before seeding.
   The pattern is `seed/00-purge-sample-data.apex` in the **sunrise-solar-internship**
   repo. (The README points at `03-admin-sunrise/seed/...`, a path from before these
   engagements were split into separate repositories — that path does not exist.)

Locale is already corrected (`Country: Australia`, `DefaultLocaleSidKey: en_AU`).

## Known repo gap

There is **no `sfdx-project.json`** in this repo, so `sf project deploy` and
`sf project retrieve` will not work against `force-app/` until one is added. The other
Salesforce repos in this program use `packageDirectories: [{path: "force-app", default:
true}]` with `sourceApiVersion: "67.0"`.

## The division of labour on this engagement

**Hemayet builds all Setup configuration by hand** — sales processes, record types,
path, territory model, forecast types, quote templates, lead assignment, the Agentforce
agent. The certification tests Setup navigation and so does the job. Do not build config
via the Metadata API on his behalf unless he asks explicitly.

**Claude does:** seed data (Apex anonymous in `seed/`), including the deliberate defects
the engagement depends on; verification queries; evidence extraction; code review;
deployment mechanics; ERD and documentation drafting; and playing stakeholders in
character for the discovery interviews — which in this engagement is a substantial part
of the work, because discovery *is* the brief.

## Seeded data must contain the mess

The engagement premise is a broken sales operation. Seed data that is clean defeats it:
opportunities parked in a stage nobody uses, close dates in the past, amounts with no
products, accounts with no owner, five reps' worth of duplicate pipeline. The defects
are the deliverable's raw material, and each one should trace to a finding the discovery
write-up can make.

## Documentation standards

`deliverables/` is the substance and the interview evidence. The configuration proves
the clicks happened; the documents prove the thinking did.

- **Every change goes in `deliverables/build-log.md`** with its date, the component, the
  change, and the requirement it traces to. Corrections are appended as new rows, never
  edited over.
- **Claim only what was verified** — a query or a screenshot backs every "verified".
- **Accepted risks are recorded, not hidden.**
- **Dates are Australian** — `dd/mm/yyyy`. Currency is AUD, once the locale is fixed.
- `evidence/` holds before/after extracts and screenshots per sprint.

## Never commit

Auth files and sfdx auth URLs — an auth URL is a full credential. `.gitignore` covers
`**/*authFile*.json`, `**/*sfdxAuthUrl*`, `.env*`, `.sf/` and `.sfdx/`. A credential
that reaches git history has to be *rotated*, not deleted.

## Agent workflow

Superpowers is expected to be installed as a **user-level plugin**
(`/plugin install superpowers@claude-plugins-official`), not vendored into this repo.
There is no test runner here and most work is Setup configuration, so the red/green TDD
skills have little to bite on; the planning, verification and code-review skills apply
to the seed scripts and the written deliverables.
