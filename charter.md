# Master Data Governance Charter

**Status:** Draft v0.1 · **Signed by:** the data owners and the Head of Data, AI & Development · **Effective from:** [TBC] · **Review:** yearly, and whenever a signatory changes

## Purpose

Data quality problems across the business trace back to master data that is
incorrect or inconsistent. This charter is our agreement on who owns master
data, who decides what, and the few controls we never switch off. The [rulebook](rulebook.md) holds the
rules, the [controls catalogue](controls.md) says how each one is enforced, and
each domain's profile holds its settings.

It applies the company's existing policies on [TBC: information security, data
protection and internal controls] to master data. It doesn't replace them.

## Scope

Supplier, customer, material and finance master data in SAP, and the non-SAP
systems that hold copies of it. SAP comes first: the unified master data app
covers SAP master data, and non-SAP copies are checked against SAP until the
app can take requests from those systems.

## Principles

1. **Lightweight.** We keep only rules that address a real problem or risk.
   Each has an ID, an owner and a control.
2. **Embedded.** Rules are enforced in SAP and the app, not by asking people to
   remember them.
3. **Agent-operated.** Automation and AI agents do routine work, within limits
   the data owners set. People stay accountable.
4. **Named ownership.** Every domain has a named business owner.

## Who decides what

| Role | Held by [TBC] | Decides or does |
| --- | --- | --- |
| Data owner | One business process owner per domain: Head of Procurement (supplier), Head of Order-to-Cash (customer), Head of Supply Chain (material), Financial Controller (finance structures) | Decides the validation and quality rules for their data (conventions, mandatory checks, critical fields, duplicate rules and thresholds, held in their domain profile), exceptions in their domain, which request types the app approves automatically, and what agents may do there. Their team confirms sensitive changes to their fields. |
| Attribute group owner | A leader in another function, by delegation from a data owner, for a group of fields that function knows best and relies on most | Decides the same for those fields, and their team confirms sensitive changes to them |
| Head of Data, AI & Development | [TBC: name] | Approves the rulebook, the controls catalogue and the vendor requirements. Accountable for the data team's delivery: the app, the agents, the vendor and running this framework. |
| Data steward | The master data vendor today; a small exceptions team once the app automates routine work | Decides routine requests, within the rules |
| Data governance specialist | The data team | Runs the framework and owns the agents. Decides nothing about data content. |
| Platform team | The data team (the app) and the SAP team | Builds and runs the app, the controls and the agent infrastructure. Decides nothing about data content. |

## How documents are approved

| Document | Approved by |
| --- | --- |
| This charter | All data owners and the Head of Data, AI & Development |
| Rulebook | The Head of Data, AI & Development. Every change goes in the change log and to the next monthly owner review. |
| Controls catalogue and vendor requirements | The Head of Data, AI & Development |
| Domain profiles | Each data owner, with attribute group owners for their fields |

## Controls we never switch off

These can't be waived by exception, and changing them needs every signatory:

- A sensitive change can't be used until the field's owner, or someone in
  their team, confirms it, and the confirmer is never in the team that entered
  it (R-13). Payment data is kept apart from paying, and bank
  details are verified with the supplier (R-14, R-15).
- Agents never approve requests or exceptions, change sensitive fields, delete
  records or grant access (R-18).
- The data team can't change master data outside the governed process, except
  through emergency access that someone outside the team reviews. Every SAP
  change can be traced to an approved request (R-08, R-19).
- No one approves their own request, exception or agent.

## Escalation and visibility

- Requests go from steward to data owner. If data owners disagree with each
  other or with the Head of Data, AI & Development, the executive they both
  report to decides.
- A one-page scorecard goes to the executive team every quarter.

## Signatures

| Role | Name | Date |
| --- | --- | --- |
| Data owner, supplier | | |
| Data owner, customer | | |
| Data owner, material | | |
| Data owner, finance structures | | |
| Head of Data, AI & Development | | |
