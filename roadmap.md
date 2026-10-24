# Roadmap

**Status:** Draft v0.1 · **Owner:** the data governance specialist · **Approved by:** the Head of Data, AI & Development · **Last updated:** 2026-10-24

This is the one document with dates, and the one place that describes the move
from the current app and the master data vendor to the unified master data
app. When a date or a step changes, only this page changes. All dates are
first estimates.

## Where we're heading

| | Before the unified app | With the unified app |
| --- | --- | --- |
| Requests raised in | The current app | The unified master data app |
| Master data created and changed by | The master data vendor, in SAP | The unified app, posting approved requests to SAP |
| Requests approved by | The vendor, within the rules | The unified app, for request types the owner has approved; otherwise the steward for each part the request touches |
| Sensitive changes confirmed by | The steward | The steward |
| Data platform and agents | Check, measure and propose. Agents never create or change master data. | The same, and agents can also prepare requests and make approved, non-sensitive changes |

Customer and supplier requests move first, in December 2026. The rest follow
one request type at a time, and the master data vendor leaves by Q2 2027.

## Timeline

| When | What | Who |
| --- | --- | --- |
| Now to early November 2026 | The charter is signed. Baseline scorecards for customer and supplier data. The Commercial and Procurement GPDOs propose their domain profiles, starting from the starters, and name their stewards. | Signatories; data team; Commercial and Procurement GPDOs |
| Early November 2026 [TBC: date] | A working session of the four GPDOs agrees the customer and supplier profiles, including who owns the business partner data they share | GPDOs; data governance specialist |
| November 2026 | The first two agents start on customer and supplier data: the duplicate finder and the change reconciler | Data team |
| November to December 2026 | The worst customer and supplier data is cleaned up. The platform team builds the agreed checks into the unified app. Customer and supplier requesters and stewards are trained. | Master data vendor; platform team; data team |
| December 2026 | Customer and supplier requests move to the unified app, and the vendor stops processing them | Platform team; Commercial and Procurement GPDOs |
| December 2026 to [TBC: February 2027] | The Manufacturing and Finance GPDOs propose their profiles, and Commercial proposes pricing, for the GPDOs to agree | GPDOs |
| [TBC: early 2027] | The request pre-check and quality triage agents start | Data team |
| By Q2 2027 [TBC: date] | The remaining request types move one at a time, and the master data vendor leaves | Platform team; GPDOs; vendor |
| After Q2 2027 | Non-SAP systems come in one at a time, as their GPDOs propose them, and the consistency checker agent starts with the first (see the data landscape in the operating model) | GPDOs; data team |

## Critical path

Each request type follows the same chain, because the unified app's checks come
from the domain profiles:

1. The GPDOs agree the domain profile, including its request types.
2. The platform team builds its checks into the unified app.
3. Requesters and stewards are trained.
4. The request type moves, and the vendor stops processing it and loses the SAP
   rights to change it.

For customer and supplier, that chain has about six weeks, so their profiles
are agreed at a working session in early November rather than at a monthly
review. Starting from the starters keeps it realistic: the GPDOs confirm and
adjust rather than write from scratch. Nothing moves on a date alone. If a
profile isn't agreed, its request types stay with the vendor until it is.
[TBC: the fallback if that runs past the vendor's exit date]

## Cleaning up existing data

The rules apply to new and changed records, and existing records are cleaned
up domain by domain (see the [rulebook](rulebook.md)).

- Before each domain moves, its worst data is cleaned up first, using the
  scorecards: duplicates and critical fields come first, because they break
  transactions and trip the unified app's checks.
- The master data vendor's remaining capacity goes into this clean-up before it
  leaves, as mass changes the data owner signs off (R-07).
- After the vendor leaves, the quality triage agent and the stewards handle
  what remains.
