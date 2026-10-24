# Master Data Governance Charter

**Status:** Draft v0.1 · **Signed by:** the four GPDOs and the Head of Data, AI & Development · **Effective from:** [TBC] · **Review:** yearly, and whenever a signatory changes

## Purpose

Data quality problems across the business trace back to master data that is
incorrect or inconsistent. This charter is our agreement on who owns master
data, who decides what, and the few controls we never switch off. The
[rulebook](rulebook.md) holds the rules, the [controls catalogue](controls.md)
says how each one is enforced, the [operating model](operating-model.md) shows
who does what day to day, each domain's profile holds its settings, and the
[roadmap](roadmap.md) says how and when we get there.

It applies the company's existing policies on [TBC: information security, data
protection and internal controls] to master data. It doesn't replace them.

## Scope

The framework covers three kinds of data, across four domains, one per GPDO
(see below):

- **SAP master data,** governed in full from the start. Requests are raised in
  the current app and processed by the master data vendor until the unified
  master data app takes over, as the [roadmap](roadmap.md) sets out.
- **Non-SAP master data,** such as data in CRM, PLM or e-commerce systems:
  owned and protected now, and brought under the other rules one system at a
  time, when its GPDO proposes it.
- **Confidential and commercially sensitive data,** such as formulas,
  recipes, prices, margins and supplier terms, in SAP or not: owned,
  classified and protected now.

The [operating model](operating-model.md) lists the systems involved, the
[roadmap](roadmap.md) says when each comes in, and the rulebook says which
rules apply everywhere from the start.

## Principles

1. **Lightweight.** We keep only rules that address a real problem or risk.
   Each has an ID, an owner and a control.
2. **Embedded.** Rules are enforced in SAP and the app, not by asking people to
   remember them.
3. **Agent-operated.** Automation and AI agents do routine work, within limits
   the data owners set. People stay accountable.
4. **Named ownership.** Every domain has a named business owner.

## Who owns what

The data owners are the four GPDOs (global process and data owners):
Commercial, Manufacturing, Finance and Procurement. Each owns their own
domain in every system that holds its data, SAP or not, including confidential
data such as formulas and recipes. Each proposes how their domain breaks down:
the data it covers, and who owns each part, by subdomain, business unit or
group of fields (attribute owners). Where
data is shared between domains, such as the material master, the GPDOs agree
who owns which part.

The GPDOs agree the proposals together at the monthly owner review and record
them in the domain profiles, because the apps and the vendor need to know who
approves what. Every piece of data has exactly one owner (R-02). The data
governance specialist provides the [profile template](domains/template.md) and
flags anything with no owner or more than one, but doesn't propose the
breakdown.

## Who decides what

| Role | Held by [TBC] | Decides or does |
| --- | --- | --- |
| Data owner | The four GPDOs: Commercial, Manufacturing, Finance and Procurement | Decides how their data is classified and its validation and quality rules (conventions, mandatory checks, critical fields, duplicate rules and thresholds, held in the domain profiles), exceptions in their domains, which request types the app approves automatically, and what agents may do there. Proposes how their domain breaks down, delegates attribute owners, and names a steward for each part they keep. |
| Attribute owner | Whoever a GPDO delegates part of their domain to, by subdomain, business unit or group of fields | Decides for that part, within the domain's conventions and checks: exceptions, automatic approvals and what agents may do. Names the steward for that part. An owner of a group of fields also sets its conventions and checks. |
| Head of Data, AI & Development | [TBC: name] | Approves the rulebook, operating model, roadmap, controls catalogue and vendor requirements. Accountable for the data team's delivery: the app, the agents, the vendor and running this framework. |
| Data steward | One person or team for each part of a domain, named by its owner from their own team | Answers questions from the vendor and requesters, decides likely duplicates, and confirms sensitive changes. Once the unified app takes over, also approves the requests it can't approve automatically. |
| Master data vendor | A third party, until the unified app takes over | Processes requests raised in the current app, and approves routine ones within the rules. Sets no rules, approves no exceptions and confirms no sensitive changes. |
| Data governance specialist | The data team | Runs the framework, keeps the roadmap and owns the agents. Provides the profile template and flags gaps and overlaps in ownership. Decides nothing about data content. |
| Platform team | The data team (the apps and the data platform) and the SAP team | Runs the data platform and the current app [TBC], builds the unified app, and runs the controls and the agent infrastructure. Decides nothing about data content. |

## How documents are approved

| Document | Approved by |
| --- | --- |
| This charter | The four GPDOs and the Head of Data, AI & Development |
| Rulebook | The Head of Data, AI & Development. Every change goes in the change log and to the next monthly owner review. |
| Controls catalogue, vendor requirements, operating model and roadmap | The Head of Data, AI & Development. The operating model summarises this charter and the rulebook; where they differ, they win. |
| Domain profiles | Proposed by each GPDO for their own domain, and agreed by the GPDOs together. After that, each GPDO maintains theirs, and attribute owners approve changes to their part. |

## Controls we never switch off

These can't be waived by exception, and changing them needs every signatory:

- A sensitive change can't be used until the domain's steward or the field's
  owner confirms it, and the confirmer is never in the team that entered it
  (R-13). Payment data is kept apart from paying, and bank details are
  verified with the supplier (R-14, R-15).
- Agents never approve requests or exceptions, change sensitive fields, delete
  records or grant access (R-18).
- Trade secrets, such as formulas and recipes, never go to an AI model outside
  an environment the organisation controls (R-21).
- The data team can't change master data outside the governed process, except
  through emergency access that someone outside the team reviews. Every SAP
  change can be traced to an approved request (R-08, R-19).
- No one approves their own request, exception or agent.

## Escalation and visibility

- Questions go from the vendor or the requester to the steward, then the
  attribute owner, then the GPDO. If GPDOs disagree with each other or with
  the Head of Data, AI & Development, the executive they both report to
  decides.
- A one-page scorecard goes to the executive team every quarter.

## Signatures

| Role | Name | Date |
| --- | --- | --- |
| Commercial GPDO | | |
| Manufacturing GPDO | | |
| Procurement GPDO | | |
| Finance GPDO | | |
| Head of Data, AI & Development | | |
