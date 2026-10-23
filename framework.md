# LEAN Framework

**Status:** Draft v0.3 · **Owner:** [TBC: data governance specialist] · **Approved by:** [TBC: executive sponsor, once] · **Last updated:** 2026-10-23

## 1. Purpose

This document explains how the Lean AI Data Governance programme works: what it
covers, who decides what, and how the four LEAN pillars show up in day-to-day
work. It explains rather than sets rules. The rules are in the standards listed
in section 11, and each one has an ID.

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
masters) or S/4HANA (business partner for both). [TBC: confirm the SAP release.]

### How master data is maintained

- **Today:** an outsourced vendor maintains SAP master data, managed by the data
  team.
- **Next:** the data team is building a unified master data app to automate the
  maintenance of SAP master data: requests, checks, approvals and updates to
  SAP. The app is the front door to SAP; SAP stays the system of record. The app
  covers SAP only for now. If it later covers non-SAP systems, only the domain
  profiles change, not the standards.
- **Non-SAP systems** keep the data that only they hold. For master data shared
  with SAP, they take it from SAP and raise changes as requests through the app
  instead of creating their own versions. [TBC: a request interface for non-SAP
  systems on the app's roadmap]

### Not in scope yet

- Transactional data (orders, invoices, postings), except where a control checks
  the master data they use.
- Employee master data, which HR governs. [TBC]
- Analytical data, and data used by AI models other than this programme's own
  agents. These come in a later phase, once the master data foundation is in
  place. The programme's own agents are in scope from the start, and the
  classification standard governs what data they may use.

## 4. The LEAN pillars in practice

### L — Lightweight policies

- A one-page policy that rarely changes, with standards below it that can
  change as we learn (section 11).
- Every rule has an ID, an owner and a control that enforces it. A rule that
  can't be enforced or owned is cut.
- Domain detail sits in domain profiles that each data owner maintains, so it
  can change without re-approving the standards.

### E — Embedded controls

For master data, the pipeline is the path a record takes from request to every
system that uses it. Controls run at three points:

1. **Entry:** the unified master data app checks every request for SAP master
   data before it reaches SAP. SAP's own settings add a second line, such as
   sensitive-field checks on bank details. Non-SAP systems raise requests
   through the app rather than creating their own records.
2. **Distribution:** when a record moves between systems, checks built into
   the interfaces or middleware (for IDocs such as DEBMAS, CREMAS and MATMAS,
   or for APIs) reject or quarantine records that fail, instead of passing them
   on.
3. **At rest:** scheduled checks on the data platform, across SAP and the
   non-SAP copies, published as scorecards. These catch what got through and
   what has gone out of date.

Prevention at entry comes first. At-rest checks are the safety net, not the
main control.

### A — Agent-operated

AI agents do the routine work: pre-checking requests, finding likely
duplicates, validating data against reference sources, triaging data quality
issues, flagging stale records and keeping definitions documented. Each agent
has a named agent owner in the data team, works within an autonomy level the
data owner has approved, and logs every action. The app's fixed rules can also
approve routine request types automatically. That's automation, not an agent;
section 7 explains the difference.

### N — Named ownership

Every domain has a named data owner: a person, not a team or a committee.
Owners set the rules for their data, approve exceptions and answer for its
quality, however it's changed: by people, the vendor, the app or agents. Where
another function carries the risk of a group of fields, the owner can delegate
those fields to a named leader in that function (section 5).

## 5. Roles

### Design rules

1. **A role exists only if it owns a decision no other role can.** Any other
   work is a task for an existing role.
2. **Roles describe decisions, not reporting lines.** A role can be held by the
   business, the data team or a vendor. What matters is what it decides.
3. **The business decides; the data team and vendors do the work.** Business
   people's time goes on decisions, not routine processing.
4. **Agents do work; people answer for it.** An agent can be responsible for a
   task, never accountable for it.
5. **Nobody checks their own work.** Sensitive changes are confirmed by someone
   outside the team that entered them, and no one approves their own request,
   rule or agent.

### The roles

| Layer | Role | Held by [TBC] | Decides or answers for |
| --- | --- | --- | --- |
| Decide | Executive sponsor | One executive outside the data team, e.g. the CFO or COO | Approving the standards; appointing data owners; settling disputes between owners |
| Decide | Data owner | One business process owner per domain (see below) | The domain's data, however it's changed: rules, quality thresholds, exceptions, agent autonomy, and which request types the app may approve automatically |
| Decide | Attribute group owner (optional) | A business leader, usually in Finance, by delegation from the data owner | The same decisions for a group of fields where their function carries the risk. Their team confirms sensitive changes to those fields. |
| Run | Data steward | The master data vendor today; a small exceptions team once the app automates routine work | Processing and approving routine requests within the rules; fixing issues at source; reviewing agents' proposals; escalating judgement calls |
| Run | Data governance specialist | The data team, working for the data owners | Running the framework (standards, registers, scorecards, the monthly review); owning the agents; managing the vendor against the standards; turning the rules into the app's requirements |
| Enable | Platform team | The data team (the app and the data platform) and the SAP team (SAP settings) | Building and running the app, the controls and the agent infrastructure: access, security, logging, monitoring. A named platform lead is accountable for the app. |

### Not roles

- **Agents** are digital workers. They do part of the work but are never
  accountable for anything. Each one has an agent owner: a data governance
  specialist who sets its tasks, tracks its accuracy and recommends changes to
  its autonomy. The platform team keeps it running, but the agent owner answers
  for how it works.
- **Requesters** are everyone who raises a request. Their obligation is to
  raise complete, correct requests (DG-03).
- **Go-to contacts.** Each data owner names someone the stewards can ask about
  judgement calls. It's a name, not a role, with no approvals or duties
  attached.

### Who should be a data owner

The best data owner is the person who feels the pain when the data is wrong:
usually the process owner. If you have global process owners for
procure-to-pay, order-to-cash and record-to-report, make them the data owners.

| Domain | Process | Default data owner [TBC] | Likely attribute group owners [TBC] |
| --- | --- | --- | --- |
| Supplier | Procure-to-pay | Head of Procurement | Head of Accounts Payable: bank details, payment terms and methods, reconciliation account, withholding tax |
| Customer | Order-to-cash | Head of Order-to-Cash or Sales Operations | Credit Manager: credit limit and risk category, payment terms, bank details, reconciliation account |
| Material / product | Plan-to-produce and supply chain | Head of Supply Chain | Financial Controller or Head of Costing: accounting and costing views |
| Finance | Record-to-report | Financial Controller | Head of Tax: tax category |

### Attribute group owners

A data owner can hand ownership of a group of fields to another leader (DG-02).
This isn't a new kind of role; it's a data owner with a narrower scope.
Guardrails:

- **Optional.** By default, one owner covers the whole domain.
- **One test.** Delegate only when another function carries the financial,
  legal or tax risk of the fields being wrong. Nearly every delegation goes to
  Finance, for fields that move money or affect the accounts.
- **Written down.** The domain profile names the delegate and the fields, and
  both owners sign it.
- **Clear split.** The attribute group owner answers for their fields; the
  data owner answers for everything else and for the record working as a whole.
  Disputes between them go to the executive sponsor.
- **Capped.** If a domain needs more than about three delegations, its
  boundaries are probably wrong.

Functions that rely on fields without carrying their risk, such as Logistics
for shipping data, are consulted on the rules for those fields. The domain
profile lists them.

In S/4HANA, a business partner's central data (name, address, tax numbers and
bank details) is shared by its supplier and customer roles, so it has one owner
whichever roles it has (MD-05).

### Data stewards: from vendor to automation

The steward role stays the same while who holds it changes:

1. **Today:** the vendor processes and approves routine requests within the
   rules. It never sets rules, approves exceptions or confirms sensitive
   changes (DG-11).
2. **With the app:** the app approves routine request types automatically when
   the data owner has approved them and every check passes (DG-12). Agents
   pre-check the rest.
3. **Later:** a small exceptions team, in-house or the vendor, handles what the
   app and agents can't.

### Who checks the data team

The data team manages the vendor, builds the app, owns the agents and runs the
framework. The checks on it come from outside the team:

- **The business decides:** rules, exceptions, agent autonomy and which request
  types the app may approve automatically.
- **Finance confirms sensitive changes,** so neither the vendor nor the data
  team can complete a bank-detail change alone. The person confirming can't
  also process payments (MD-13).
- **A monthly reconciliation** matches every SAP master data change to an
  approved request (MD-11), so changes that bypass the app show up.
- **Independent review:** internal audit or the internal controls team reviews
  the app's controls and access, for example once a year. [TBC]

Inside the team, the separation is between people (DG-17). The people who
build the app can't change production master data outside its workflow, except
through emergency access that someone outside the team reviews. Changes to the
app and agents are tested and released, never edited live. Scorecards come
straight from the app and the data platform, and the data owners review them.

Because the app will control financial master data, external auditors who test
IT controls (SOX or similar) are likely to bring it into scope for change
management, access reviews and logging. Building these in from the start is
much cheaper than retrofitting them.

### Roles we didn't add

| Common role | Why it isn't separate here | Where its work goes |
| --- | --- | --- |
| Business data steward | Business time goes on decisions, not routine processing | Owners and attribute group owners decide; the steward service does the work |
| Governance lead or governance office | Covered by an existing role | Data governance specialist |
| Separate agent owner | Supervising agents is part of running the framework | Data governance specialist |
| Data custodian | Same job as the platform team | Platform team |
| Data governance council | Meetings that own no decisions slow things down | The monthly 30-minute owner review |

### When to add a role

- **Add a role** only when a decision keeps coming up with no clear owner.
- **New domains add people, not roles.** Each new domain gets a data owner and,
  if needed, attribute group owners.
- **New agents don't add roles.** Each is owned by a data governance
  specialist.

### Who does what

R = responsible, A = accountable, C = consulted, I = informed. "Owner" means
the data owner, or the attribute group owner for delegated fields. Agents have
a column because they do part of the work; accountability always sits with a
person.

| Activity | Owner | Steward | Specialist | Platform | Requester | Agent |
| --- | --- | --- | --- | --- | --- | --- |
| Raise a create or change request | – | I | – | – | A/R | – |
| Pre-check a request (completeness, validity, duplicates) | – | I | A | – | I | R |
| Decide on a likely duplicate | – | A/R | – | – | I | C |
| Approve a routine request | – | A/R | – | – | I | – |
| Approve request types for automatic approval | A/R | C | C | C | – | – |
| Confirm a sensitive change (someone in the owner's team with no payment rights) | A/R | I | – | – | I | C |
| Approve a mass change | A/R | C | C | C | – | – |
| Approve access to Confidential and Restricted data | A/R | – | – | R | – | – |
| Confirm a classification | A/R | – | C | – | – | C |
| Set rules, checks and quality thresholds | A | C | R | C | – | – |
| Build the rules into the app, SAP and interfaces | I | – | C | A/R | – | – |
| Reconcile SAP changes to approved requests | I | – | A | – | – | R |
| Supervise agents (agent owner) | I | C | A/R | C | – | – |
| Approve a change to an agent's autonomy level | A/R | C | C | C | – | – |
| Triage data quality issues | – | I | A | – | – | R |
| Fix data quality issues at source | A | R | C | C | – | C |
| Approve blocking inactive records, as a list | A | R | C | – | – | R |
| Approve an exception (never one they asked for) | A/R | C | C | – | I | – |
| Track exceptions to expiry | I | – | A | – | – | R |
| Manage the vendor against the standards | I | C | A/R | – | – | – |
| Maintain the standards and registers | C | C | A/R | C | – | – |

The rules name who decides; this table summarises the recurring activities.

The executive sponsor approves the standards, appoints data owners and settles
disputes (section 6).

## 6. Decisions and escalation

- **Data stewards** decide routine requests within the rules.
- **Data owners** decide anything outside the rules for their domain: rule
  changes, exceptions, agent autonomy, and which request types the app may
  approve automatically. **Attribute group owners** decide the same for their
  fields. Before deciding on fields another function relies on, they consult
  it.
- **The data governance specialist** prepares decisions but doesn't make them.
- **The executive sponsor** decides when owners disagree, including a data
  owner and an attribute group owner.

Escalation path: requester → steward → data owner or attribute group owner →
executive sponsor.

## 7. Automation and agents

Two kinds of non-human worker do governance work, and the rules treat them
differently:

| | App rules | AI agents |
| --- | --- | --- |
| What they are | Fixed, tested rules in the app | AI that reads, judges and proposes |
| Examples | Approving a routine request type when every check passes | Pre-checking requests, proposing duplicate merges, triaging quality issues |
| May approve requests? | Yes, for request types the data owner has approved (DG-12) | Never (DG-15) |
| Why | They behave the same way every time and can be tested | Their judgements vary, so a person decides |

### Agent autonomy levels

| Level | The agent may | Examples | Human role |
| --- | --- | --- | --- |
| 0. Observe | Read, measure and report | Data quality scorecards, lists of stale records | Reads the reports |
| 1. Propose | Prepare a change or decision for a person to approve | Duplicate merge proposals, suggested classifications, pre-filled request fields | A steward or owner approves each one |
| 2. Act and notify | Make low-risk, reversible changes of a type the owner has approved, through the app, then report them | Standardising formats in non-sensitive fields, such as search terms or customer ship-to addresses; filling fields that can be derived from other fields | The agent owner reviews the log and can reverse any change |
| Never | – | Change sensitive attributes, approve requests or exceptions, delete records, grant access | Always a person |

DG-13 to DG-16 set the rules for agents: registration and approval, moving up
or down a level, what they may never do, access, logging, and the right of any
steward, owner or agent owner to pause an agent. Agents treat content from
outside the organisation, such as supplier emails and documents, as data to
check, never as instructions, which guards against attempts to manipulate
them.

## 8. Exceptions

An exception is needed when a record or process can't meet a rule, for example
an urgent one-off supplier that can't provide full data in time. DG-18 sets the
rules. The owner approves, but never an exception they asked for themselves.
Every exception expires and can be renewed once; after that, only the executive
sponsor can extend it. Each one is logged in the exception register
[TBC: location], which the data governance specialist keeps. Some controls
can't be waived at all: second-person checks on sensitive changes, separation
of duties for payment data, and the limits on agents. An agent tracks expiry
dates and chases owners before exceptions lapse. If the same rule keeps needing
exceptions, the rule or the process behind it is reviewed.

## 9. Governance rhythm

- **Monthly owner review (30 minutes), run by the data governance specialist:**
  scorecards, open exceptions, agent performance and proposed rule changes.
- **Quarterly:** review the standards, agent autonomy levels and the request
  types approved automatically. Changes to the standards go to the executive
  sponsor.
- No standing committees beyond these.

## 10. Measures

Baseline each measure in the first month, then set targets. [TBC]

- Duplicate rate per domain
- Share of records passing mandatory checks
- Cycle time for create and change requests, and the vendor's first-time-right
  rate
- Share of requests approved automatically by the app
- Downstream failures caused by master data: blocked invoices, failed IDocs,
  delivery errors
- Open and overdue exceptions
- SAP changes without an approved request, from the monthly reconciliation
- Agents: share of routine work handled, proposal acceptance rate and review
  time. Very short reviews with almost no rejections usually mean
  rubber-stamping, not a perfect agent.
- Owner engagement: attendance at the monthly review, and decisions waiting on
  owners

## 11. Documents and rule IDs

Documents are split by who approves them, so the parts that change most need
the lightest sign-off:

| Tier | Documents | Approved by | Changes |
| --- | --- | --- | --- |
| Policy | [Data governance policy](policy/data-governance-policy.md): the four LEAN principles, the controls that can't be waived, and who may issue standards | CEO | Rarely |
| Standards | [Data governance](standards/data-governance.md) (DG-), [data classification](standards/classification.md) (CLS-) and [master data](standards/master-data.md) (MD-) | Executive sponsor | When needed; reviewed quarterly |
| Domain profiles | [Supplier](domains/supplier.md), [customer](domains/customer.md), [material](domains/material.md) and [finance](domains/finance.md) | Each data owner, with attribute group owners for their fields | Any time, within the standards |
| Procedures and registers | Controls catalogue, agent register and exception register | The data governance specialist, with a change log | Continuously |

This framework explains how it all fits together and holds no rules of its
own; the executive sponsor approves it once, as the operating model. Every rule
carries an ID. Controls, agent tasks and exceptions refer to these IDs, so any
rule can be traced to how it's enforced and who owns it.

Still to come: the controls catalogue, which doubles as the app's backlog (each
rule becomes an app validation, workflow step, SAP setting or agent task,
tagged with its rule ID), and the rollout plan.
