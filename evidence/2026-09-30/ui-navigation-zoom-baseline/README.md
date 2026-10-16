# Read-only UI navigation and 200% zoom baseline

**Date:** 2026-09-30, ~21:05–21:20 AEST
**Target:** Ironbark Industrial Supply, Developer Edition, Org ID 00Dbm00000uRk89 (verified via Setup → Company Information; matches deliverables/build-log.md)
**Environment:** Chrome on Windows host, Lightning Experience, Sales app
**Scope:** Pre-upgrade read-only smoke check. No records created, edited or deleted; no setup changes.

| # | Check | 100% zoom | 200% zoom |
|---|---|---|---|
| 1 | Sales app opens from App Launcher | Pass | Not tested |
| 2 | Accounts list views (Recently Viewed, All Accounts) | Pass: loads, 0 items | Pass: nav tabs collapse into "More" |
| 3 | Account record detail and related lists | Blocked: no Account records | Blocked |
| 4 | Opportunities list views | Pass: loads, 0 items | Pass |
| 4b | Opportunity record and stage path | Blocked: no Opportunity records | Blocked |
| 5 | New Opportunity modal | Not tested | Pass: Owner, Amount, Private, Close Date, Opportunity Name visible; footer (Cancel / Save & New / Save) overlaps lower fields, modal scrolls. Closed without saving; All Opportunities still 0 items afterwards |

## Findings
- The org contains no Account or Opportunity records, although the repo includes a `seed/` folder. Record-level checks are blocked until seed data is confirmed or loaded.
- At 200% zoom, the modal footer overlays form fields; content remains reachable by scrolling. Observation only, not confirmed as a defect.

## Limitations
- Salesforce CLI authentication from the salesforce-dev VM failed (`sf org login web` → AuthTimeoutError; browser callback did not complete). Checks were run manually in the browser.
- Screenshots were not committed because they show the org's My Domain URL.
- Service Cloud screens and non-admin visibility were not tested.

## Next action
Review `seed/` and `deliverables/build-log.md` to confirm whether seed data should exist, then rerun checks 3 and 4b.
