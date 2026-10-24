# Operating Model

**Status:** Draft v0.1 · **Approved by:** the Head of Data, AI & Development · **Under:** [Master data governance charter](charter.md)

How the framework runs day to day: who does what, the systems that enforce the
rules, the agents, and the rhythm and measures that keep it on track.

## Who does what

R = responsible, A = accountable, C = consulted, I = informed.

- **Owner:** the GPDO, or the attribute owner for their part of the domain.
- **Steward:** the person or team the owner names for that part.
- **Head of Data:** the Head of Data, AI & Development.
- **Specialist:** the data governance specialist.
- **Platform:** the platform team.
- **Vendor:** the master data vendor, until it leaves.

| Activity | Owner | Steward | Head of Data | Specialist | Platform | Vendor | Requester |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Agree and change the domain profile: breakdown, classification, checks, automatic approvals and what agents may do | A/R | C | I | C | C | C | – |
| Approve a request, before the unified app | A | C | – | – | – | R | I |
| Approve a request the unified app can't approve automatically | A | R | – | – | – | – | I |
| Decide on a likely duplicate | C | A/R | – | – | – | I | I |
| Confirm a sensitive change | A | R | – | – | – | I | I |
| Approve a mass change, including a list of records to block | A/R | C | – | C | C | C | – |
| Approve an exception | A/R | C | – | C | – | – | I |
| Approve access to Confidential or Restricted data | A/R | – | – | – | R | – | – |
| Fix data quality issues at source | A | R | – | C | – | R | – |
| Build checks into the apps, SAP and interfaces | I | – | A | C | R | – | – |
| Own and supervise the agents | I | C | I | A/R | C | – | – |
| Train and support requesters | I | C | – | A/R | C | – | I |
| Manage the vendor against its requirements | I | – | A | R | – | C | – |

Agents aren't in the table. They do part of some of this work but are never
accountable, and the [agent register](#agents) says what each one does.

## The platform

Four systems enforce the rules. The [controls catalogue](controls.md) shows
how.

| System | Its job in governance |
| --- | --- |
| Current app | Where requests are raised until the unified app takes over, for the master data vendor to process in SAP. [TBC: its name, and who runs it] |
| Unified master data app | The front door for SAP master data, built by the data team. It checks every request on entry, routes approvals, approves owner-approved request types automatically, and holds sensitive changes until they're confirmed. Later, it can take requests from non-SAP systems. |
| SAP | The system of record. Only the master data vendor's staff, and later the unified app, can change its master data. Its sensitive-field settings act as a second line, and its change documents record every change (R-08). |
| Data platform | Runs the checks on stored data, builds the scorecards, compares non-SAP copies with SAP, and holds the data agents read. |

## The data landscape

The platform above is governed in full from the start. Other systems hold
master data or confidential data too. The rows below are examples to start
from: the GPDOs confirm the systems that hold their data, and the data
governance specialist keeps the list. Each system is owned and protected now,
under the five rules that apply everywhere (R-01, R-02, R-16, R-21 and R-22),
and comes under the other rules when its GPDO proposes it.

| System | What it holds | Relationship to SAP |
| --- | --- | --- |
| Recipe and formulation systems [TBC: names] | Formulas, recipes, process parameters | Masters the recipes that aren't in SAP |
| PLM | Engineering data and specifications | Masters engineering attributes |
| CRM | Customer contacts and segmentation, and copies of SAP customers | Masters sales contacts; takes customers from SAP |
| E-commerce or PIM | Product content, and copies of SAP customers and materials | Masters marketing content; takes the rest from SAP |
| Procurement platform or supplier portal | Supplier onboarding data | Sends create requests to SAP |
| Spreadsheets and local files | Price lists, recipes, local copies of master data | None; to be replaced by data from the systems of record |

To bring a system in:

1. The GPDO who owns its data proposes it, and adds the fields it masters, and
   their checks, to their domain profile.
2. The GPDOs settle how it relates to SAP: it either masters some fields
   itself, or takes them from SAP and sends changes back as requests (R-04).
3. Checks start on the data platform, including a comparison with SAP. Checks
   at entry follow, through the system's own workflow or the unified app.
4. The other rules apply from the date the GPDOs agree.

## Agents

Agents are for work that needs judgement. A check with a fixed answer, such as
whether a bank account is already used by another supplier, or a list drawn
by a fixed rule, such as inactive records, belongs in the app or on the data
platform instead (see the [controls catalogue](controls.md)). Until the
unified app is live, agents only observe and propose (R-18). The
[roadmap](roadmap.md) says when each one starts.

This is the agent register (R-18). The data governance specialist owns the
agents. Data owners approve how far an agent may act in their domain, in their
domain profiles; agents that don't touch master data are approved by the Head
of Data, AI & Development. The autonomy levels are in the
[rulebook](rulebook.md).

| Agent | What it does | Rules | Starts at | Works on |
| --- | --- | --- | --- | --- |
| Duplicate finder | Finds likely duplicates among existing records, including near matches on names and addresses, and proposes which to keep | R-05, R-10 | 1. Propose | SAP data, on the data platform |
| Change reconciler | Matches SAP master data changes to approved requests in the current app, including those without a clear reference, and reports changes without one. A fixed report takes over once the unified app records the request on every change. | R-08 | 0. Observe | SAP change documents and the requests behind them |
| Request pre-check | Reviews each request before it's processed: reads attachments, spots likely duplicates, and flags values that pass the checks but look wrong | R-05 | 1. Propose | Requests in the current app [TBC], then in the unified app |
| Quality triage | Groups failing records by cause, raises fix requests and proposes new checks to the owner | R-09, R-10 | 1. Propose | The scorecards on the data platform |

A consistency checker, which works out which differences between a non-SAP
system and SAP matter, joins when the first non-SAP system comes in.

## Requesters

Once their request types move to the unified app, requesters enter the data
themselves, so quality at entry depends on them. Four things support them:

- **Guidance at entry.** The unified app shows each field's conventions, from
  the domain profile, as it's filled in.
- **Instant feedback.** The request pre-check agent flags what looks wrong
  before the request goes any further.
- **Training before the move.** Requesters are trained [TBC: format] before
  their request types move.
- **Measured by team.** First-time-right is measured for each requesting team
  and shared monthly with its GPDO, so the teams that struggle get help.

## Rhythm

- **Monthly owner review, 30 minutes,** run by the data governance specialist:
  scorecards, exceptions, ownership gaps, changes to domain profiles, agent
  performance and rule changes.
- **Quarterly:** a one-page scorecard to the executive team.

## Measures

Baseline each one in the first month, then set targets.

- Records passing their domain's checks (incorrect data)
- Duplicates, and differences between SAP and non-SAP copies (inconsistent
  data)
- Downstream issues traced back to master data, such as blocked invoices,
  failed deliveries and report corrections
- Request turnaround, and first-time-right by requesting team
- Share of requests approved automatically
- SAP changes without an approved request
- Agents: work handled, proposal acceptance and review time. Almost no
  rejections combined with very short reviews usually means rubber-stamping.
