# Master Data Governance Charter

**Status:** Draft v0.1 · **Signed by:** the four GPDOs and the Head of Data, AI & Development · **Effective from:** [TBC] · **Review:** yearly, and whenever a signatory changes

## Purpose

Data quality problems across the business trace back to master data that is
incorrect or inconsistent. This charter is our agreement on who owns master
data, who decides what, and the few controls we never switch off. The
[rulebook](rulebook.md) holds the rules, the [controls catalogue](controls.md)
says how each one is enforced, and each domain's profile holds its settings.

It applies the company's existing policies on [TBC: information security, data
protection and internal controls] to master data. It doesn't replace them.

## Scope

Master data in SAP across four domains, one per GPDO (see below), and the
non-SAP systems that hold copies of it. SAP comes first: the unified master
data app covers SAP master data, and non-SAP copies are checked against SAP
until the app can take requests from those systems.

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
Commercial, Manufacturing, Finance and Procurement. Each owns their own domain
and proposes how it breaks down: the master data it covers, and who owns each
part, by subdomain, business unit or group of fields (attribute owners). Where
data is shared between domains, such as the material master, the GPDOs agree
who owns which part.

The GPDOs agree the proposals together at the monthly owner review and record
them in the domain profiles, because the app and the vendor need to know who
approves what. Every piece of data has exactly one owner (R-02). The data
governance specialist provides the [profile template](domains/template.md) and
flags anything with no owner or more than one, but doesn't propose the
breakdown.

## Who decides what

| Role | Held by [TBC] | Decides or does |
| --- | --- | --- |
| Data owner | The four GPDOs: Commercial, Manufacturing, Finance and Procurement | Decides the validation and quality rules for their data (conventions, mandatory checks, critical fields, duplicate rules and thresholds, held in the domain profiles), exceptions in their domains, which request types the app approves automatically, and what agents may do there. Proposes how their domain breaks down, and delegates attribute owners. Their team confirms sensitive changes to their fields. |
| Attribute owner | Whoever a GPDO delegates part of their domain to, by subdomain, business unit or group of fields | Decides for that part, within the domain's conventions and checks: exceptions, automatic approvals and what agents may do. An owner of a group of fields also sets its conventions and checks. They, or someone in their team, confirm sensitive changes to it. |
| Head of Data, AI & Development | [TBC: name] | Approves the rulebook, the controls catalogue and the vendor requirements. Accountable for the data team's delivery: the app, the agents, the vendor and running this framework. |
| Data steward | The master data vendor today; a small exceptions team once the app automates routine work | Decides routine requests, within the rules |
| Data governance specialist | The data team | Runs the framework and owns the agents. Provides the profile template and flags gaps and overlaps in ownership. Decides nothing about data content. |
| Platform team | The data team (the app) and the SAP team | Builds and runs the app, the controls and the agent infrastructure. Decides nothing about data content. |

## How documents are approved

| Document | Approved by |
| --- | --- |
| This charter | The four GPDOs and the Head of Data, AI & Development |
| Rulebook | The Head of Data, AI & Development. Every change goes in the change log and to the next monthly owner review. |
| Controls catalogue and vendor requirements | The Head of Data, AI & Development |
| Domain profiles | Proposed by each GPDO for their own domain, and agreed by the GPDOs together. After that, each GPDO maintains theirs, and attribute owners approve changes to their part. |

## Controls we never switch off

These can't be waived by exception, and changing them needs every signatory:

- A sensitive change can't be used until the field's owner, or someone in
  their team, confirms it, and the confirmer is never in the team that entered
  it (R-13). Payment data is kept apart from paying, and bank details are
  verified with the supplier (R-14, R-15).
- Agents never approve requests or exceptions, change sensitive fields, delete
  records or grant access (R-18).
- The data team can't change master data outside the governed process, except
  through emergency access that someone outside the team reviews. Every SAP
  change can be traced to an approved request (R-08, R-19).
- No one approves their own request, exception or agent.

## Escalation and visibility

- Questions go from the steward to the attribute owner, then the GPDO. If
  GPDOs disagree with each other or with the Head of Data, AI & Development,
  the executive they both report to decides.
- A one-page scorecard goes to the executive team every quarter.

## Signatures

| Role | Name | Date |
| --- | --- | --- |
| Commercial GPDO | | |
| Manufacturing GPDO | | |
| Procurement GPDO | | |
| Finance GPDO | | |
| Head of Data, AI & Development | | |
