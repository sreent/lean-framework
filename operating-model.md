# Operating Model

**Status:** Draft v0.3 · **Approved by:** the Head of Data, AI & Development · **Under:** [Master data governance charter](charter.md)

How the target setup runs day to day: who does what, the systems that enforce
the rules, the agents that coordinate the work, and the rhythm and measures
that keep it on track. Until each request type moves to the unified master
data app, the [interim arrangements](interim.md) apply.

## Who does what

R = responsible, A = accountable, C = consulted, I = informed. The GPDO stays
accountable for the whole domain (R-01); A below is who answers for each
decision. An attribute owner can hand the rows marked \* to their delegates.
The data team is the data governance specialist and the platform team, and
Head of Data is the Head of Data, AI & Development. Agents do much of this
work but are never accountable, so they aren't in the table; the
[agent register](#agents) says what each does.

| Activity | GPDO | Attribute owner | Data team | Head of Data | How often |
| --- | --- | --- | --- | --- | --- |
| Approve the domain's breakdown, who owns each part, and the conventions across it | A/R | C | C | I | Once, then when it changes |
| Agree data shared with another domain, with its GPDO | A/R | C | C | – | Once, then when it changes |
| Approve a part's settings: classification, checks, automatic approvals and what agents may do | I | A/R | C | – | Once, then when they change |
| Approve an exception or a mass change, including the list of records to block | I | A/R | C | – | As they arise; the list monthly |
| Approve which roles can see classified data, review who has access, and approve extracts of Restricted data | – | A/R | R | – | Roles once; reviews [TBC: twice a year]; extracts as they arise |
| Confirm a sensitive change \* | – | A/R | – | – | Daily |
| Decide a likely duplicate, or approve a request the app can't \* | – | A/R | – | – | Daily |
| Review a sample of automatic approvals \* | – | A/R | – | – | Monthly |
| Build and run the app, the data platform and the agents | I | – | R | A | Ongoing |
| Supervise the agents | I | I | R | A | Ongoing |
| Keep the rulebook, operating model, controls catalogue and roadmap up to date | C | C | R | A | As they change |

Expected effort: [TBC: hours a week for GPDOs, attribute owners and delegates,
estimated from the vendor's current volumes].

## The platform

Three systems enforce the rules, and the [controls catalogue](controls.md)
shows how.

| System | Its job in governance |
| --- | --- |
| Unified master data app | The front door for SAP master data, built by the data team. It holds each domain's settings, checks every request on entry, approves the request types owners have approved, routes the rest to the part's owner or their delegates, holds sensitive changes until they're confirmed, and records the request behind every change. Later, it can take requests from non-SAP systems. |
| SAP | The system of record. Only the unified app's service identity changes its master data, and its change documents record every change (R-08). |
| Data platform | Runs the checks on stored data, builds the scorecards, compares non-SAP copies with SAP, finds changes without a request, and holds the data agents read. |

## Agents

Agents do the coordination and routine work that would otherwise fall on
people: they prepare, chase, route, draft and propose. They also flag what
needs a person's judgement, such as a likely duplicate, and propose an answer.
A check with a fixed answer belongs in the app, and a decision belongs to a
person.

This is the agent register (R-18). The agent owner for every agent is the data
governance specialist, [TBC: name]. All four start at level 1: they propose,
and a person decides. At any level they can remind, chase and route, because
that changes no data. Attribute owners approve how far an agent may act in
their part, including each move up a level, in the domain profile; agents that
don't touch master data, such as the governance coordinator, are approved by
the Head of Data, AI & Development. The autonomy levels are in the
[rulebook](rulebook.md), and the [roadmap](roadmap.md) says when each agent
starts. One temporary agent, the change reconciler, is listed in the
[interim arrangements](interim.md).

| Agent | Works for | Does | Rules |
| --- | --- | --- | --- |
| Request assistant | Requesters | Helps fill in requests, pre-filling them from documents such as a bank letter. Explains failed checks, answers questions from the domain profile, and flags values that pass the checks but look wrong. | R-03, R-05 |
| Owner assistant | Attribute owners and their delegates | Prepares each case: duplicate comparisons, bank-detail call-backs, and the evidence. Chases anything overdue, and prepares the monthly sample of automatic approvals. | R-05, R-06, R-13, R-15 |
| Quality agent | Attribute owners | Finds duplicates in existing data, groups failures by cause, raises fix requests and proposes new checks. Runs the clean-up, sorts differences between non-SAP copies and SAP, and asks whether inactive records are still needed. | R-04, R-09, R-10, R-11 |
| Governance coordinator | GPDOs and the Head of Data, AI & Development | Prepares the owner review and the quarterly scorecard. Tracks decisions, exceptions and ownership gaps, and reminds owners. Drafts changes to profiles and documents, keeps the list of systems in the data landscape, and assembles audit evidence. | R-02, R-20 |

## The data landscape

The platform above is governed in full from the start. Other systems hold
master data or confidential data too. The rows below are examples to start
from: the GPDOs confirm the systems that hold their data, and the governance
coordinator keeps the list. Each system is owned and protected now, under the
five rules that apply everywhere (R-01, R-02, R-16, R-21 and R-22), and comes
under the other rules when its GPDO proposes it.

| System | What it holds | Relationship to SAP |
| --- | --- | --- |
| Recipe and formulation systems [TBC: names] | Formulas, recipes, process parameters | Masters the recipes that aren't in SAP |
| PLM | Engineering data and specifications | Masters engineering attributes |
| CRM | Customer contacts and segmentation, and copies of SAP customers | Masters sales contacts; takes customers from SAP |
| E-commerce or PIM | Product content, and copies of SAP customers and materials | Masters marketing content; takes the rest from SAP |
| Procurement platform or supplier portal | Supplier onboarding data | Sends create requests to the unified app |
| Spreadsheets and local files | Price lists, recipes, local copies of master data | None; to be replaced by data from the systems of record |

To bring a system in:

1. The GPDO who owns its data proposes it, and its attribute owner adds the
   fields it masters, and their checks, to the domain profile.
2. The GPDOs concerned settle how it relates to SAP: it either masters some
   fields itself, or takes them from SAP and sends changes back as requests
   (R-04).
3. Checks start on the data platform, including a comparison with SAP that the
   quality agent sorts. Checks at entry follow, through the system's own
   workflow or the unified app.
4. The other rules apply from a date its GPDO agrees with the data team.

## Requesters

Requesters enter the data themselves in the unified app, so quality at entry
depends on them. Three things support them:

- **Guidance at entry.** The app shows each field's conventions, from the
  domain profile, as it's filled in, and rejects what fails a check.
- **The request assistant.** It pre-fills requests from documents, explains
  failed checks and answers questions, so requesters rarely need a person.
- **Measured by team.** First-time-right is measured for each requesting team
  and shared with its GPDO, so the teams that struggle get help.

## Rhythm

- **Decisions happen in the app, not in meetings.** Owners and their delegates
  decide there, prompted by the agents.
- **Owner review,** run by the data governance specialist for the GPDOs, with
  attribute owners joining for their own items, from the pack the governance
  coordinator prepares. It's monthly while request types are moving, then
  quarterly, and covers scorecards, exceptions, ownership gaps, profile
  changes, agent performance and rule changes.
- **Quarterly:** a one-page scorecard to the executive team.

## Measures

The first three show how little people have to do. Baseline each measure in
the first month, then set targets.

- Share of requests the app approves without a person
- Decisions owners and delegates make each week, and how long requests wait
  for them
- Time from request to use, and first-time-right by requesting team
- Records passing their domain's checks (incorrect data)
- Duplicates, and differences between SAP and non-SAP copies (inconsistent
  data)
- Downstream issues traced back to master data, such as blocked invoices,
  failed deliveries and report corrections
- SAP changes without an approved request
- Agents: work handled, proposal acceptance and review time. Almost no
  rejections combined with very short reviews usually means rubber-stamping.
