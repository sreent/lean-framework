# Operating Model

**Status:** Draft v0.1 · **Approved by:** [TBC: Head of Data, AI & Development] · **Under:** [Master data governance charter](charter.md)

How the framework runs day to day: who does what, the platform that enforces
the rules, the agents that do routine work, and the rhythm and measures that
keep it on track. It summarises the [charter](charter.md) and the
[rulebook](rulebook.md); where they differ, they win.

## Who does what

R = responsible, A = accountable, C = consulted, I = informed.

- **Owner:** the GPDO, or the attribute owner for their part of the domain.
- **Head of Data:** the Head of Data, AI & Development.
- **Specialist:** the data governance specialist.
- **Platform:** the platform team.
- **Steward:** the master data vendor today.
- **Agent:** agents do part of the work, but are never accountable.

| Activity | Owner | Head of Data | Specialist | Platform | Steward | Requester | Agent |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Propose and agree domain profiles | A/R | I | C | C | I | – | – |
| Set conventions, checks and quality thresholds | A/R | I | C | C | C | – | – |
| Raise a create or change request | – | – | – | – | I | A/R | – |
| Pre-check a request | – | – | A | – | I | I | R |
| Decide on a likely duplicate | C | – | – | – | A/R | I | C |
| Approve a routine request | – | – | – | – | A/R | I | – |
| Approve request types for automatic approval | A/R | C | C | C | – | – | – |
| Confirm a sensitive change | A/R | – | – | – | I | I | C |
| Approve a mass change | A/R | – | C | C | C | – | – |
| Approve access to Confidential or Restricted data | A/R | – | – | R | – | – | – |
| Build checks into the app, SAP and interfaces | I | A | C | R | – | – | – |
| Reconcile SAP changes to approved requests | I | – | A | – | – | – | R |
| Triage data quality issues | – | – | A | – | I | – | R |
| Fix data quality issues at source | A | – | C | – | R | – | C |
| Approve blocking inactive records, as a list | A | – | C | – | R | – | R |
| Supervise agents (agent owner) | I | I | A/R | C | C | – | – |
| Approve an agent's autonomy level | A/R | C | C | C | – | – | – |
| Approve an exception | A/R | – | C | – | – | I | – |
| Track exceptions to expiry | I | – | A/R | – | – | – | – |
| Manage the vendor against its requirements | I | A | R | – | C | – | – |
| Maintain the rulebook, controls catalogue and this operating model | C | A | R | C | – | – | – |

## The platform

Three systems enforce the rules. The [controls catalogue](controls.md) shows
how each rule is enforced, today and once the app is live.

| System | Its job in governance |
| --- | --- |
| Unified master data app | The front door for SAP master data, built by the data team. It checks every request on entry, routes approvals, approves owner-approved request types automatically, and holds sensitive changes until they're confirmed before posting them to SAP. It covers SAP master data for now; later it can take requests from non-SAP systems. [TBC: go-live dates] |
| SAP | The system of record. Only the app can change master data, and the vendor's stewards until the app is live. Its sensitive-field settings act as a second line, and its change documents feed the reconciliation (R-08). |
| Data platform | Runs the checks on stored data, builds the scorecards, compares non-SAP copies with SAP, and holds the data agents read. |

Until the app is live, the vendor works directly in SAP, and the "Today"
column of the controls catalogue applies.

## Agents

Agents are for work that needs judgement. A check with a fixed answer, such as
whether a bank account is already used by another supplier, or a reminder on a
set date, belongs in the app's rules instead (see the
[controls catalogue](controls.md)).

This is the agent register (R-18). Every agent has a named agent owner from
the data team, starts at a low autonomy level, and moves up only on evidence
from an independent sample. Data owners approve how far an agent may act in
their domain, in their domain profiles. Agents that don't touch master data
are approved by the Head of Data, AI & Development. The autonomy levels are
defined in the rulebook.

| Agent | What it does | Rules | Starts at | When | Agent owner |
| --- | --- | --- | --- | --- | --- |
| Duplicate finder | Finds likely duplicates among existing records, including near matches on names and addresses, and proposes which to keep | R-05, R-10 | 1. Propose | Pilot | [TBC] |
| Change reconciler | Matches SAP master data changes to approved requests, including vendor tickets without a clear reference, and reports changes without one. Once the app records the request on every change, a fixed report takes over. | R-08 | 0. Observe | Pilot | [TBC] |
| Request pre-check | Reviews each request before a steward sees it: reads attachments, spots likely duplicates, and flags values that pass the app's checks but look wrong | R-05 | 1. Propose | With the app | [TBC] |
| Quality triage | Groups failing records by cause, raises fix requests and proposes new checks to the owner | R-09, R-10 | 1. Propose | With the app | [TBC] |
| Consistency checker | Works out which differences between non-SAP copies and SAP matter, and which side is right | R-04 | 0. Observe | Later | [TBC] |
| Inactive records | Prepares the monthly list of records to block, and flags those that may still be needed, such as seasonal suppliers | R-11 | 1. Propose | Later | [TBC] |

## Rhythm

- **Monthly owner review, 30 minutes,** run by the data governance specialist:
  scorecards, exceptions, ownership gaps, changes to domain profiles, agent
  performance and rule changes.
- **Quarterly:** a one-page scorecard to the executive team.

## Measures

Baseline each one in the first month, then set targets. [TBC]

- Records passing their domain's checks (incorrect data)
- Duplicates, and differences between SAP and non-SAP copies (inconsistent
  data)
- Downstream issues traced back to master data, such as blocked invoices,
  failed deliveries and report corrections
- Request turnaround and first-time-right rate
- Share of requests approved automatically
- SAP changes without an approved request
- Agents: work handled, proposal acceptance and review time. Almost no
  rejections combined with very short reviews usually means rubber-stamping.
