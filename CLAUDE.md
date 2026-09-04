# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this project.

## What this is

Engagement workspace for **Ironbark Industrial Supply** — a ten-sprint Sales Cloud
Consultant (Sales-Con-201) simulation at a fictional national industrial parts
distributor: 140 reps across five states, forecasting run out of spreadsheets, no
territory model, an opportunity stage set nobody agrees on, and Agentforce licensed
but never switched on.

Sprint scope: discovery, sales process design, territory management, forecasting,
quoting, lead-to-opportunity, Agentforce for Sales, data quality, adoption and
enablement, executive dashboard.

## The brief is not "build features"

From the README, and worth holding to in every review: the job is to **work out
what the sales organisation actually does before changing anything**. That is the
discipline Sales-Con-201 tests, and the one that separates a consultant from an
admin taking orders.

Practical consequence: a design deliverable that proposes a stage set, a territory
model or a forecast hierarchy without evidence of the current-state discovery
behind it is incomplete, however good the design is. Discovery findings belong in
`deliverables/`, not in a commit message.

## Not to be confused with the TradeLink engagement

`tradelink-group` also covers Sales Cloud Consultant. Ironbark is a **greenfield
sales process design** at a distributor; TradeLink is a **remediation** of six
years of accumulated decisions at a franchise network. Keep the design reasoning
separate.

## The org

Target org alias **`ironbark`**, org ID `00Dbm00000uRk89EAC`.

```bash
sf org display --target-org ironbark
sf data query --target-org ironbark --query "SELECT COUNT() FROM Opportunity"
```

Agentforce entitlements confirmed active from day one: Agentforce (Default),
Agentforce Service Agent Builder (10,000), Einstein Prompt Templates. The
scenario's premise is that Agentforce is licensed and unused — that is a starting
condition, not a blocker.

**Two org items still outstanding** (both recorded in the build log):

1. **Currency locale is still USD.** `DefaultCurrencyIsoCode` is not a field on
   `Organization` in a single-currency org, so it cannot be set through the API.
   Setup → Company Information → Edit → Currency Locale → English (Australia) AUD.
   **Do this before seeding any Opportunity data** — forecasting and quoting work
   is built on those amounts, and every one of them is wrong until it is fixed.
2. **13 stock Salesforce sample Accounts are still present** (Edge Communications,
   GenePoint, United Oil & Gas et al.). Purge before seeding, or the pipeline
   numbers are meaningless.

Country and `DefaultLocaleSidKey` were already corrected to Australian via the API.

## The division of labour

**Hemayet builds all Setup configuration by hand** — sales processes, record types,
territory model, forecast hierarchy, quote templates, path, assignment rules,
dashboards, the agent itself. The certification tests Setup navigation and so does
the job. Do not build config via the Metadata API on his behalf unless he asks
explicitly.

**Claude does:** seed data (Apex anonymous in `seed/`), verification queries, code
review, deployment mechanics, ERD and documentation drafting, build-log entries,
and playing stakeholders in character for the discovery interviews.

## Repository conventions

| Folder | Contents |
|---|---|
| `force-app/` | Metadata **retrieved from** the org, not authored here |
| `seed/` | Apex anonymous scripts that build starting data, including its deliberate defects |
| `deliverables/` | Design docs, SOPs, analyses, runbooks — the substance |
| `evidence/` | Before/after screenshots and test results, per sprint |

`deliverables/build-log.md` carries five entries covering org provisioning and the
opening audit. Every subsequent change gets a row.

## Known stale reference

The README points at `03-admin-sunrise/seed/00-purge-sample-data.apex` for the
purge pattern. That path is from an earlier monorepo layout; the file now lives in
the separate `sunrise-solar-internship` repository at
`seed/00-purge-sample-data.apex`.

## Rules worth enforcing in review

- Deliberate defects in seed data are the exercise. Do not quietly fix them.
- No `sfdx-project.json` exists here yet — this repo cannot be deployed from or
  retrieved into until one is added.
- Never commit an sfdx auth URL. It is a full credential. See `.gitignore`.
