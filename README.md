# Ironbark Industrial Supply Engagement

> **This is a simulation, not client work.** Ironbark Industrial Supply Pty Ltd is a fictional company.
> This repository documents a self-directed Salesforce project built to develop
> and evidence implementation skills. No real customer data appears anywhere in it.

**Certification track:** Sales Cloud Consultant (Sales-Con-201)
**Salesforce org:** Developer Edition (CLI alias `ironbark`)
**Scope:** 10 sprints | discovery, sales process design, territory management, forecasting, quoting, lead-to-opportunity, Agentforce for Sales, data quality, adoption and enablement, executive dashboard

## The brief

A national industrial parts distributor with 140 reps across five states, running
forecasting out of spreadsheets, with no territory model, an opportunity stage set
nobody agrees on, and Agentforce licensed but never switched on.

The consulting brief is not "build features." It is to work out what the sales
organisation actually does before changing anything — which is the discipline
Sales-Con-201 tests, and the one that separates a consultant from an admin taking
orders.

## What's in here

| Folder | Contents |
|---|---|
| `force-app/` | Salesforce metadata retrieved from the org — the configuration itself |
| `seed/` | Apex scripts that build the starting data, including its deliberate defects |
| `deliverables/` | The written work: design docs, SOPs, analyses, runbooks |
| `evidence/` | Before/after screenshots and test results per phase |

`deliverables/` is the substance. The configuration proves the clicks happened;
the documents prove the thinking did.

## Progress

Build log lives in `deliverables/build-log.md` — every change with its date,
reason, and the requirement it traces to.

## Org state

- [x] Org created and authenticated (`ironbark`, `00Dbm00000uRk89EAC`)
- [x] Locale corrected to Australian — the org provisioned as US despite the
      signup form. `Country: Australia`, `DefaultLocaleSidKey: en_AU`
- [ ] **Currency locale still USD.** Not settable through the API in a
      single-currency org. Setup → Company Information → Edit → **Currency
      Locale** → English (Australia) — AUD. Do this before seeding any
      Opportunity data, or every amount is wrong and the forecasting work is
      built on it.
- [ ] Stock Salesforce sample data still present (13 Accounts). Purge before
      seeding — see `03-admin-sunrise/seed/00-purge-sample-data.apex` for the
      pattern.

## For recruiters and agencies

**What this repository evidences:** Sales Cloud Consultant discipline — discovery before
features. A stage model, territory design or forecast hierarchy proposed before the
discovery write-up exists is the wrong artefact, and that rule is enforced here.

**State as at 06/09/2026:** Scoped; org provisioned and locale corrected. Currency locale
and sample-data purge are outstanding before any Opportunity data is seeded. No sprint has
been built yet, and this README will say so until one has.

**Read these first:**

1. [`deliverables/build-log.md`](deliverables/build-log.md) — the record so far, including the org audit
2. [`CLAUDE.md`](CLAUDE.md) — the engagement rules and the seed-data-must-contain-the-mess principle

**How to verify:** every change is in the build log with its date and the requirement it
traces to; corrections are appended, never edited over. The
[skill-to-evidence map](https://portfolio.hossainconsulting.com/#evidence) on the portfolio shows where each certification is
applied, and the [hiring page](https://portfolio.hossainconsulting.com/#hire) says what I am open to.

---

Built by [Hemayet Hossain](https://github.com/hossainconsulting) · Sydney, Australia
Portfolio: [portfolio.hossainconsulting.com](https://portfolio.hossainconsulting.com)

---

## Connect

Built by **Hemayet Hossain**, Salesforce administrator and implementation
consultant, Sydney, Australia. This is one of eight projects
published in full; the complete record and the certification track are on the
portfolio.

[Portfolio](https://portfolio.hossainconsulting.com/?utm_source=github&utm_medium=readme&utm_campaign=ironbark-industrial-supply) ·
[All links](https://portfolio.hossainconsulting.com/links) ·
[GitHub](https://github.com/hossainconsulting) ·
[LinkedIn](https://www.linkedin.com/company/hossain-consulting) ·
[Instagram](https://www.instagram.com/hossainconsulting/)
