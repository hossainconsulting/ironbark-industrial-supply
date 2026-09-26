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

---

Built by [Hemayet Hossain](https://github.com/hossainconsulting) · Sydney, Australia
Portfolio: [portfolio.hossainconsulting.com](https://portfolio.hossainconsulting.com)

## Verified Salesforce credentials

Hemayet Hossain holds four credentials verified through Salesforce's public credential record: Salesforce Certified Agentforce Specialist, Salesforce Certified Platform Administrator II, Salesforce Certified Platform App Builder, and Salesforce Certified Platform Administrator.

[View the public Salesforce credential record](https://trailhead.salesforce.com/en/credentials/certification-detail-print/?searchString=/EMytG9drkgo/H4/0tgVITa/sw2U8vhbkvkc3jqlaJgauY5cCr+PvNo4YAw1Ki9f) · [Review the Salesforce User Lifecycle SOP](https://github.com/hossainconsulting/salesforce-user-lifecycle-sop)


## AI contributor credit

**OpenAI Codex** is credited as an AI-assisted contributor for authorised
repository work under Hemayet Hossain's direction. This includes assistance
with documentation and repository maintenance; implementation or validation
contributions are recorded in the relevant commits and task evidence.

**Anthropic Claude Code** is also credited as an AI-assisted contributor for
authorised repository work under Hemayet Hossain's direction, including coding,
writing and documentation. Commits it co-authored carry a
`Co-Authored-By: Claude` trailer.

Hemayet Hossain remains the project owner and decision-maker. These credits do
not represent separate GitHub accounts or collaborator invitations, and do
not change existing authorship, licensing or project completion claims.
