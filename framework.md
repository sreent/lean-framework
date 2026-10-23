# LEAN Framework

**Status:** Draft v0.2 · **Owner:** [TBC: lead steward] · **Last updated:** 2026-10-23

## 1. Purpose

This document describes how the Lean AI Data Governance programme works: what it
covers, who is accountable, how decisions are made, and how the four LEAN pillars
show up in day-to-day work. The rules themselves are in the
[data governance policy](policy/data-governance-policy.md) and its standards.

Items marked `[TBC]` are defaults to confirm or replace.

## 2. The problem

The programme starts with master data: mainly in SAP, plus the non-SAP systems that
create, hold or use the same suppliers, customers, materials and finance structures.
Typical symptoms:

[TBC: replace with your own pain points, ideally with a recent example and a rough
cost for each. They set the priority order for phase 1.]

- **Duplicates.** The same supplier, customer or material exists more than once,
  within SAP and across systems.
- **Bad records break transactions.** Missing or wrong data leads to blocked
  invoices, wrong prices, failed deliveries and payment errors.
- **No single version of the truth.** SAP and non-SAP systems hold different
  versions of the same record, with no rule for which one wins.
- **Slow, manual requests.** Create and change requests travel by email and
  spreadsheet, with rework and no visible status.
- **Unclear ownership.** No one can say who decides the right value for a field,
  or who can approve an exception.
- **Stale records.** Suppliers, customers and materials unused for years are
  still open for use.
- **Uncontrolled sensitive changes.** Bank details and payment terms can be
  changed without a second check, which is a payment-fraud risk.

## 3. Scope

### Phase 1 domains

| Domain | SAP objects | Non-SAP systems [TBC] |
| --- | --- | --- |
| Supplier | Business partner (supplier role) or vendor master | Procurement platform, supplier portal |
| Customer | Business partner (customer role) or customer master | CRM, e-commerce |
| Material / product | Material master | PLM, product information management (PIM), e-commerce |
| Finance | GL accounts, cost centres, profit centres | Consolidation and planning tools |

The framework applies whether you run SAP ECC (separate vendor and customer
masters) or S/4HANA (business partner for both). [TBC: confirm the SAP release,
and whether SAP Master Data Governance (MDG) is in use.]

### Not in scope yet

- Transactional data (orders, invoices, postings), except where a control checks
  the master data they use.
- Employee master data, which HR governs. [TBC]
- Analytical data, and data used to train or prompt AI models. These come in a
  later phase, once the master data foundation is in place.

## 4. The LEAN pillars in practice

### L — Lightweight policies

- One policy of about two pages, plus a short standard for each topic.
- Every rule has an ID, a named owner and a control that enforces it. A rule that
  can't be enforced or owned is cut.
- Field-level detail sits in the domain profiles of the
  [master data standard](policy/standards/master-data.md), not in long manuals.

### E — Embedded controls

For master data, the pipeline is the path a record takes from request to every
system that uses it. Controls run at three points:

1. **Entry:** when a record is created or changed. Examples: SAP MDG validation
   rules, mandatory fields and checks in the SAP create transaction, form
   validation in non-SAP systems.
2. **Distribution:** when a record moves between systems. Interfaces (IDocs such
   as DEBMAS, CREMAS and MATMAS, APIs or middleware) reject or quarantine records
   that fail their checks instead of passing them on.
3. **At rest:** scheduled data quality checks over all records, published as
   scorecards. These catch what got through and what has gone out of date.

Prevention at entry comes first. At-rest checks are the safety net, not the main
control.

### A — Agent-operated

AI agents do the routine work: pre-checking requests, finding likely duplicates,
validating data against reference sources, triaging data quality issues,
flagging stale records and keeping definitions documented. Each agent has a
named agent owner who supervises it (section 5), works within an autonomy level
the data owner has approved (section 7), and logs every action.

### N — Named ownership

Every domain has a named data owner: a person, not a team or a committee. Owners
set the rules for their data, approve exceptions and answer for its quality,
including changes made by agents. A domain has one owner even when several
functions maintain parts of its records.

## 5. Roles

### How the roles were chosen

Five rules keep the role model small and stable:

1. **A role exists only if it owns a decision no other role can.** Any other
   work is a task for an existing role.
2. **Roles are hats, not jobs.** They're held by people already in the
   organisation, so the programme starts with no new headcount.
3. **The business owns the data; IT enables.** Ownership sits with the
   business processes that depend on the data, not with the SAP team.
4. **Agents do work; people answer for it.** An agent can be responsible for a
   task, never accountable for it.
5. **Nobody checks their own work.** A request, a sensitive change or a step up
   in an agent's autonomy is always approved by someone other than whoever
   proposed it.

### Four roles

| Layer | Role | Held by [TBC] | Decides or answers for |
| --- | --- | --- | --- |
| Decide | Executive sponsor | One executive, e.g. the CFO or COO | Appointing data owners; approving the standards; settling disputes that owners can't resolve |
| Decide | Data owner | One senior business leader per domain (see below) | The domain's data, including changes made by agents: rules, checks, quality thresholds, exceptions, and how much autonomy agents get |
| Run | Data steward | The existing master data team, plus nominated experts in other functions | Approving routine requests; the second check on sensitive changes; supervising agents; fixing issues at source. At least two per domain, so one can check the other. |
| Enable | Platform team | SAP, integration and data platform teams | Building and running the controls and the agents: access, security, logging and monitoring |

### Two hats, worn by stewards

- **Lead steward.** One steward, usually the head of the master data team, runs
  the framework: keeps the standards and registers current and runs the monthly
  owner review [TBC: about a day a week]. Scorecards come from automated checks
  and agents and are reviewed by the owners, so the lead steward isn't marking
  their own work.
- **Agent owner.** Every agent has one named agent owner: the steward who
  supervises it, the way a team leader supervises a member of the team. The
  agent owner sets its tasks, reviews its work, tracks its accuracy, and asks
  the data owner to raise or lower its autonomy level. The lead steward owns
  every agent until there are enough to hand over to domain stewards.

An agent and its agent owner are different things: the agent does the work, and
the agent owner answers for how it does it. The agent owner isn't the platform
team either. The platform team keeps an agent running and secure, as IT does for
a laptop, but only someone who knows the work can judge whether the agent's
proposals are right.

### Not roles

- **Agents** are digital workers. They appear in the table below because they
  do part of the work, but they're never accountable for anything.
- **Requesters** are everyone else who raises a request or uses master data.
  Their obligation is to raise complete, correct requests (P-02).

### Who should be a data owner

The best data owner is the person who feels the pain when the data is wrong. In
an SAP organisation that's usually the process owner. If you already have
global process owners for procure-to-pay, order-to-cash and record-to-report,
make them the data owners: that adds no new role. [TBC]

| Domain | Process | Default data owner [TBC] |
| --- | --- | --- |
| Supplier | Procure-to-pay | Head of Procurement |
| Customer | Order-to-cash | Head of Order-to-Cash or Sales Operations |
| Material / product | Plan-to-produce and supply chain | Head of Supply Chain |
| Finance | Record-to-report | Financial Controller |

### Shared records

Some records are maintained by several functions: a material has finance,
purchasing, sales and planning views. The domain still has one owner. The other
functions:

- are consulted on the rules for the fields they rely on, which each domain
  profile lists;
- nominate stewards who approve changes to those fields (MD-07).

If a function disagrees with the owner's decision on its fields, the executive
sponsor decides (section 6).

### Roles we didn't add

| Common role | Why it isn't separate here | Where its work goes |
| --- | --- | --- |
| Attribute group owner | It splits accountability for one record across several people | The data owner answers for the whole record; stewards from each function approve changes to their fields |
| Governance lead or governance office | It coordinates but owns no decision | The lead steward hat |
| Data custodian | It's the same job as the platform team | Platform team |
| Data governance council | Meetings that own no decisions slow things down | The monthly 30-minute owner review |

### When to add a role

- **Add a role** only when a decision keeps coming up with no clear owner.
- **Turn a hat into a job** when it grows past about a day a week. For example,
  the lead steward becomes a full-time governance manager.
- **New domains add people, not roles.** Each new domain gets a data owner and
  stewards.
- **New agents add agent owner hats, not a new team.**

As agents take on routine work, stewards spend less time keying and checking
data and more on judgement: reviewing proposals, handling exceptions and
supervising agents. The roles stay the same; the work inside them changes.

### Who does what

R = responsible, A = accountable, C = consulted, I = informed. Agents have a
column because they do part of the work; accountability always sits with a
person.

| Activity | Data owner | Steward | Platform | Requester | Agent |
| --- | --- | --- | --- | --- | --- |
| Raise a create or change request | – | I | – | A/R | – |
| Pre-check a request (completeness, validity, duplicates) | – | A | – | I | R |
| Approve a routine request | – | A/R | – | I | – |
| Verify a sensitive change (a second steward) | A | R | – | I | C |
| Set rules, mandatory checks and quality thresholds | A | R | C | – | – |
| Build and run controls and agents | C | C | A/R | – | – |
| Supervise an agent's work (agent owner) | I | A/R | C | – | – |
| Approve a change to an agent's autonomy level | A/R | C | C | – | – |
| Triage data quality issues | – | A | – | – | R |
| Fix data quality issues at source | A | R | C | – | C |
| Approve an exception | A/R | C | – | I | – |
| Track exceptions to expiry | I | A | – | – | R |
| Maintain the standards and registers (lead steward) | C | A/R | C | – | – |

The executive sponsor appoints data owners, approves the standards and settles
disputes (section 6).

## 6. Decisions and escalation

- **Stewards** decide routine requests within the standards.
- **Data owners** decide anything outside the standards: exceptions, rule
  changes, agent autonomy levels and disputes within their domain. On fields
  another function relies on, they consult that function first.
- **The executive sponsor** decides when owners disagree with each other, or
  when a function disagrees with an owner's decision on fields it relies on.

Escalation path: requester → steward → data owner → executive sponsor.

## 7. Agent autonomy levels

| Level | The agent may | Examples | Human role |
| --- | --- | --- | --- |
| 0. Observe | Read, measure and report | Data quality scorecards, lists of stale records | Reads the reports |
| 1. Propose | Prepare a change or decision for a person to approve | Duplicate merge proposals, suggested classifications, pre-filled request fields | A steward or owner approves each one |
| 2. Act and notify | Make low-risk, reversible changes within set limits, then report them | Standardising address formats, fixing capitalisation, filling fields that can be derived from other fields | The agent owner reviews the log and can reverse any change |
| Never | – | Change sensitive attributes, approve requests or exceptions, delete records, grant access | Always a person |

Rules for all agents:

- Each agent is registered with its purpose, the domains it works in, its
  autonomy level, the systems it touches, its agent owner and its contact in
  the platform team. The lead steward keeps the register. [TBC: where the
  register lives]
- The platform team builds and runs each agent, and its agent owner supervises
  its work. The data owner of each domain it works in stays accountable for the
  data, as for any change made by a person.
- New agents start at level 0 or 1. Moving to level 2 needs the agent owner's
  recommendation, evidence from a trial [TBC: e.g. 98% of proposals accepted
  over four weeks] and the data owner's approval.
- Agents use their own service identities with least-privilege access. The
  [classification standard](policy/standards/classification.md) applies to them
  as it does to people.
- Every action is logged with its input, output and reason, and the log is kept
  for [TBC: 12 months].

## 8. Exceptions

An exception is needed when a record or process can't meet a rule, for example an
urgent one-off supplier that can't provide full data in time.

- The domain's data owner approves it, or a delegate they have named in writing.
- Every exception expires after at most [TBC: 90 days]. By then the issue is fixed
  or the owner renews the exception.
- Each exception is logged in the exception register [TBC: location], which the
  lead steward keeps, with its rule ID, the records affected, the reason, the approver, the expiry date and any
  compensating control.
- An agent tracks expiry dates and chases owners before exceptions lapse.
- If the same rule keeps needing exceptions, the rule or the process behind it is
  reviewed.

## 9. Governance rhythm

- **Monthly owner review (30 minutes), run by the lead steward:** scorecards,
  open exceptions and proposed rule changes.
- **Quarterly:** review the policy, the standards and agent autonomy levels.
- No standing committees beyond these.

## 10. Measures

Baseline each measure in the first month, then set targets. [TBC]

- Duplicate rate per domain
- Share of records passing mandatory checks
- Cycle time for create and change requests
- First-time-right rate for requests (approved without rework)
- Downstream failures caused by master data: blocked invoices, failed IDocs,
  delivery errors
- Open and overdue exceptions
- Share of routine tasks handled by agents, and the acceptance rate of agent
  proposals

## 11. Rule IDs and documents

Every rule carries an ID. Controls, agent tasks and exceptions refer to these IDs,
so any rule can be traced to how it's enforced and who owns it.

| Prefix | Document |
| --- | --- |
| P- | [Data governance policy](policy/data-governance-policy.md) |
| CLS- | [Data classification standard](policy/standards/classification.md) |
| MD- | [Master data standard](policy/standards/master-data.md) |

Still to come: the controls catalogue (C-), the agent playbook (AG-) and the
rollout plan.
