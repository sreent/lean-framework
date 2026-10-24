# Roadmap

**Status:** Draft v0.2 · **Owner:** the data governance specialist · **Approved by:** the Head of Data, AI & Development · **Last updated:** 2026-10-24

How and when we get from today's setup to the target described in the other
documents. This is the one document with dates, so when a date moves, only
this page changes. All dates are first estimates. Until each request type
moves, the [interim arrangements](interim.md) apply.

## Where we're heading

| | Today | Target |
| --- | --- | --- |
| Requests raised in | The current app | The unified master data app |
| Master data created and changed by | The master data vendor, in SAP | The unified app, posting approved requests to SAP |
| Requests approved by | The vendor, within the rules | The unified app, for request types the owner has approved; otherwise the steward |
| Sensitive changes confirmed by | The steward | The steward |
| Domain profiles | Documents each GPDO approves | Settings in the unified app, approved there by their owner |
| Agents | Coordinate, check and propose; they never create or change master data | The same, and they can make approved, non-sensitive changes through the app |

Customer and supplier requests move first, in December 2026. The rest follow
one request type at a time, and the master data vendor leaves by Q2 2027.

## Timeline

| When | What | Who |
| --- | --- | --- |
| Now to early November 2026 | The charter is signed. Baseline scorecards for customer and supplier data. The governance coordinator drafts the customer and supplier profiles from the starters and the data as it stands, and the two GPDOs name their stewards. | Signatories; data team; Commercial and Procurement GPDOs |
| Early November 2026 [TBC: date] | The Commercial and Procurement GPDOs approve their profiles and agree the business partner data they share | Commercial and Procurement GPDOs |
| November 2026 | The quality agent starts on customer and supplier data, and the change reconciler starts (see the interim arrangements) | Data team |
| November to December 2026 | The worst customer and supplier data is cleaned up. The platform team builds the checks into the unified app. Requesters and stewards are trained. | Master data vendor; platform team; data team |
| December 2026 | Customer and supplier requests move to the unified app. The vendor stops processing them and loses the SAP rights to change them. | Platform team; Commercial and Procurement GPDOs |
| December 2026 to [TBC: February 2027] | The Manufacturing and Finance GPDOs approve their profiles, and Commercial approves pricing | GPDOs |
| [TBC: early 2027] | The request assistant and the steward assistant start in the unified app | Data team |
| [TBC: 2027] | Domain profiles move into the unified app as settings that owners approve there | Platform team; GPDOs |
| By Q2 2027 [TBC: date] | The remaining request types move one at a time, the master data vendor leaves, and the interim arrangements are deleted | Platform team; GPDOs; vendor |
| After Q2 2027 | Non-SAP systems come in one at a time, as their GPDOs propose them, and the quality agent compares each with SAP (see the data landscape in the operating model) | GPDOs; data team |

## Critical path

Each request type follows the same chain, because the unified app's checks come
from the domain profiles:

1. Its GPDO approves the domain profile, including its request types, and
   agrees any shared data with the other GPDO concerned.
2. The platform team builds its checks into the unified app.
3. Requesters and stewards are trained [TBC: format].
4. The request type moves. The vendor stops processing it and loses the SAP
   rights to change it.

For customer and supplier, that chain has about six weeks, so the governance
coordinator drafts their profiles and the two GPDOs approve them in early
November. Nothing moves on a date alone. If a profile isn't approved, its
request types stay with the vendor until it is. [TBC: the fallback if that
runs past the vendor's exit date]

## Cleaning up existing data

The rules apply to new and changed records, and existing records are cleaned
up domain by domain (see the [rulebook](rulebook.md)).

- Before each domain moves, its worst data is cleaned up first, using the
  scorecards: duplicates and critical fields come first, because they break
  transactions and trip the unified app's checks.
- The master data vendor's remaining capacity goes into this clean-up before it
  leaves, as mass changes the data owner signs off (R-07).
- After the vendor leaves, the quality agent and the stewards handle what
  remains.
