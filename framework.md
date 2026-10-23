# LEAN Framework

**Status:** Draft v0.1 · **Owner:** [TBC: governance lead] · **Last updated:** 2026-10-23

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
flagging stale records and keeping definitions documented. Each agent works
within an approved autonomy level (section 7), has a named owner, and logs every
action.

### N — Named ownership

Every domain has a named data owner: a person, not a team or a committee. Owners
set the rules for their data, approve exceptions and answer for its quality.
Where different functions own different parts of a record, such as the finance
and planning views of a material, each attribute group also has a named owner.

## 5. Roles

| Role | Who [TBC] | Accountable for |
| --- | --- | --- |
| Data owner | One senior business leader per domain (see below) | Rules, quality targets and exceptions for the domain |
| Attribute group owner | Functional lead for part of a record, e.g. Finance for material valuation fields | Definitions and quality of that attribute group |
| Data steward | Master data specialists, central or in the business | Approving routine requests, resolving issues, maintaining definitions; first escalation point for agents |
| Platform team | SAP, integration and data platform teams | Building and running the controls; provisioning access |
| Requester | Any business user | Raising complete, correct requests |
| Agent owner | A named person for each agent | The agent's behaviour, autonomy level and action log |
| Governance lead | [TBC] | Running the framework: policy and standards, scorecards, the monthly owner review. Not accountable for any domain's data. |
| Executive sponsor | [TBC] | Settling escalations that owners can't resolve; backing the programme |

Default data owners:

| Domain | Data owner [TBC] |
| --- | --- |
| Supplier | Head of Procurement |
| Customer | Head of Order-to-Cash or Sales Operations |
| Material / product | Head of Supply Chain |
| Finance | Financial Controller |

### Who does what

R = responsible, A = accountable, C = consulted, I = informed.

| Activity | Data owner | Steward | Platform | Requester | Agent | Gov lead |
| --- | --- | --- | --- | --- | --- | --- |
| Raise a create or change request | – | I | – | A/R | – | – |
| Pre-check a request (completeness, validity, duplicates) | – | A | – | I | R | – |
| Approve a routine request | – | A/R | – | I | – | – |
| Verify a sensitive change (the second check) | A | R | – | I | C | – |
| Set rules, mandatory checks and quality thresholds | A | R | C | – | – | C |
| Build and run controls | C | C | A/R | – | – | I |
| Triage data quality issues | – | A | – | – | R | – |
| Fix data quality issues at source | A | R | C | – | C | – |
| Approve an exception | A/R | C | – | I | – | I |
| Maintain the policy and standards | C | C | C | – | – | A/R |

## 6. Decisions and escalation

- **Stewards** decide routine requests within the standards.
- **Data owners** decide anything outside the standards: exceptions, rule changes
  and disputes within their domain.
- **Owners together** settle disputes between domains or attribute groups, such as
  a material field that both supply chain and finance want to control. If they
  can't agree, the executive sponsor decides.

Escalation path: requester → steward → data owner → executive sponsor.

## 7. Agent autonomy levels

| Level | The agent may | Examples | Human role |
| --- | --- | --- | --- |
| 0. Observe | Read, measure and report | Data quality scorecards, lists of stale records | Reads the reports |
| 1. Propose | Prepare a change or decision for a person to approve | Duplicate merge proposals, suggested classifications, pre-filled request fields | A steward or owner approves each one |
| 2. Act and notify | Make low-risk, reversible changes within set limits, then report them | Standardising address formats, fixing capitalisation, filling fields that can be derived from other fields | A steward reviews the log and can reverse any change |
| Never | – | Change sensitive attributes, approve requests or exceptions, delete records, grant access | Always a person |

Rules for all agents:

- Each agent is registered with its purpose, autonomy level, owner and the systems
  it touches. [TBC: where the register lives]
- New agents start at level 0 or 1. Moving to level 2 needs the data owner's
  approval and evidence from a trial [TBC: e.g. 98% of proposals accepted over
  four weeks].
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
- Each exception is logged in the exception register [TBC: location] with its rule
  ID, the records affected, the reason, the approver, the expiry date and any
  compensating control.
- An agent tracks expiry dates and chases owners before exceptions lapse.
- If the same rule keeps needing exceptions, the rule or the process behind it is
  reviewed.

## 9. Governance rhythm

- **Monthly owner review (30 minutes):** scorecards, open exceptions and proposed
  rule changes.
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
