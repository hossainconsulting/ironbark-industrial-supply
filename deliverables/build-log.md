# Build log — Ironbark Industrial Supply Engagement

Every change, with the reason and the requirement it traces to. This is the
artefact that survives the project and the one an auditor or a successor reads.

| Date | Component | Type | Change | Why / requirement |
|---|---|---|---|---|
| 19/08/2026 | Org: `ironbark` | Provisioning | Developer Edition created, named Ironbark Industrial Supply (`00Dbm00000uRk89EAC`), authenticated to the CLI as alias `ironbark` | Dedicated org for the Sales Cloud Consultant track, kept separate from the TradeLink engagement which also covers Sales Cloud |
| 19/08/2026 | Org: `ironbark` | Correction | Country → Australia, `DefaultLocaleSidKey` → `en_AU` via the API | Org provisioned as `Country: United States`, `en_US`, despite Australia being selected at signup. Systematic with these DE signups — the same happened to `coastline`. Fixed before any data was loaded |
| 19/08/2026 | Org: `ironbark` | Audit | Agentforce entitlements confirmed: `Agentforce (Default)` Active, `Agentforce Service Agent Builder` Active (10,000), `Einstein Prompt Templates` Active | Establishes that Agentforce for Sales work is licensed from day one — the scenario's premise is that it is licensed and unused |
| 19/08/2026 | Org: `ironbark` | Finding | Currency locale still USD. `DefaultCurrencyIsoCode` is not a field on `Organization` in a single-currency org, so it cannot be set through the API | Must be changed in Setup before seeding Opportunity data. Forecasting and quoting work is built on these amounts |
| 19/08/2026 | Org: `ironbark` | Finding | Stock Salesforce sample data present — 13 Accounts (Edge Communications, GenePoint, United Oil & Gas et al.) | Purge before seeding. Leaving it mixes fictional-company data with Salesforce's own and makes the pipeline numbers meaningless |
