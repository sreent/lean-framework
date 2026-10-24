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
- **Steward:** the master data vendor until Q2 2027; after that, a person each
  owner names, for what the unified app and agents can't handle.
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
how each rule is enforced, until Q2 2027 and once the unified app takes over.

| System | Its job in governance |
| --- | --- |
| Current app | Where requests are raised until Q2 2027. The vendor then makes the changes in SAP. [TBC: its name, and who runs it] |
| Unified master data app | From Q2 2027, the front door for SAP master data, built by the data team. It checks every request on entry, routes approvals, approves owner-approved request types automatically, and holds sensitive changes until they're confirmed before posting them to SAP. It covers SAP master data for now; later it can take requests from non-SAP systems. [TBC: go-live dates] |
| SAP | The system of record. Until Q2 2027, only the vendor's stewards can change master data; after that, only the unified app. Its sensitive-field settings act as a second line, and its change documents feed the reconciliation (R-08). |
| Data platform | Runs the checks on stored data, builds the scorecards, compares non-SAP copies with SAP, and holds the data agents read. It does all this before Q2 2027 too. |

Until Q2 2027, requests are raised in the current app and the vendor makes the
changes in SAP; the first column of the controls catalogue covers that period.
Only creating and changing master data waits for the unified app: the data
platform and agents check, measure and propose from now on.

## The data landscape

Every system that holds master data or confidential data, and when it comes
into the framework. The rows are examples to start from: the GPDOs confirm the
systems that hold their data, and the data governance specialist keeps the
list.

| System | What it holds | Relationship to SAP | In the framework |
| --- | --- | --- | --- |
| SAP [TBC: release] | Customer, pricing, material, production, supplier and finance master data | The system of record | Now, in full |
| Current app, then the unified app | Requests for SAP master data | The front door to SAP | Now, in full |
| Data platform | Copies of master data, for checks and scorecards | Takes data from SAP | Now, in full |
| Recipe and formulation systems [TBC: names] | Formulas, recipes, process parameters | Masters the recipes that aren't in SAP | Owned and protected now; the other rules later |
| PLM [TBC] | Engineering data and specifications | Masters engineering attributes | Owned and protected now; the other rules later |
| CRM [TBC] | Customer contacts and segmentation, and copies of SAP customers | Masters sales contacts; takes customers from SAP | Owned and protected now; the other rules later |
| E-commerce or PIM [TBC] | Product content, and copies of SAP customers and materials | Masters marketing content; takes the rest from SAP | Owned and protected now; the other rules later |
| Procurement platform or supplier portal [TBC] | Supplier onboarding data | Sends create requests to SAP | Owned and protected now; the other rules later |
| Spreadsheets and local files | Price lists, recipes, local copies of master data | None; they should take data from the systems of record | Owned and protected now; replaced over time |

"Owned and protected now" means ownership, classification, access and the
trade secret rule apply from the start (R-01, R-02, R-16, R-21).

To bring a system in:

1. The GPDO who owns its data proposes it, and updates their domain profile
   with the fields it masters and their checks.
2. The GPDOs settle how it relates to SAP: it either masters some fields
   itself, or takes them from SAP and sends changes back as requests (R-04).
3. Checks start on the data platform, with the consistency checker comparing
   it with SAP. Checks at entry follow, through the system's own workflow or
   the unified app's request interface.
4. The other rules apply from the date the GPDOs agree.

## Agents

Agents are for work that needs judgement. A check with a fixed answer, such as
whether a bank account is already used by another supplier, or a reminder on a
set date, belongs in the app's rules instead (see the
[controls catalogue](controls.md)).

Until the unified app is live, agents don't create or change master data: they
work at levels 0 and 1 only, on requests in the current app and on the data
platform, and the vendor makes every change. After that, they can also prepare
requests in the unified app and make the non-sensitive change types owners
approve (level 2).

This is the agent register (R-18). Every agent has a named agent owner from
the data team, starts at a low autonomy level, and moves up only on evidence
from an independent sample. Data owners approve how far an agent may act in
their domain, in their domain profiles. Agents that don't touch master data
are approved by the Head of Data, AI & Development. Agents work with trade
secrets only where the data owner approves, and only on AI models in an
environment the organisation controls (R-21). The autonomy levels are defined
in the rulebook.

| Agent | What it does | Rules | Starts at | When | Agent owner |
| --- | --- | --- | --- | --- | --- |
| Duplicate finder | Finds likely duplicates among existing records, including near matches on names and addresses, and proposes which to keep | R-05, R-10 | 1. Propose | Pilot | [TBC] |
| Change reconciler | Matches SAP master data changes to approved requests in the current app, including those without a clear reference, and reports changes without one. Once the unified app records the request on every change, a fixed report takes over. | R-08 | 0. Observe | Pilot | [TBC] |
| Request pre-check | Reviews each request before it's processed: reads attachments, spots likely duplicates, and flags values that pass the checks but look wrong | R-05 | 1. Propose | Before Q2 2027, in the current app [TBC] | [TBC] |
| Quality triage | Groups failing records by cause, raises fix requests and proposes new checks to the owner | R-09, R-10 | 1. Propose | Before Q2 2027, on the data platform | [TBC] |
| Consistency checker | Works out which differences between non-SAP copies and SAP matter, and which side is right | R-04 | 0. Observe | Before Q2 2027, on the data platform | [TBC] |
| Inactive records | Prepares the monthly list of records to block, and flags those that may still be needed, such as seasonal suppliers | R-11 | 1. Propose | Before Q2 2027, on the data platform | [TBC] |

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
