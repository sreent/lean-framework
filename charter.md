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

- **SAP master data,** governed in full from the start.
- **Non-SAP master data,** such as data in CRM, PLM or e-commerce systems:
  owned and protected now, and brought under the other rules one system at a
  time, when its GPDO proposes it.
- **Confidential data,** such as formulas, recipes, prices, margins and
  supplier terms, in SAP or not: owned, classified and protected now.

The [operating model](operating-model.md) lists the systems involved, the
[roadmap](roadmap.md) says when each comes in, and the rulebook says which
rules apply everywhere from the start.

## Principles

1. **Lightweight.** We keep only rules that address a real problem or risk.
   Each has an ID, a reason and a control.
2. **Embedded.** Rules are enforced in SAP and the app, not by asking people to
   remember them.
3. **Agent-operated.** Automation and AI agents do routine work, within limits
   the data owners set. People stay accountable.
4. **Named ownership.** Every domain has a named business owner.

## Who owns what

The data owners are the four GPDOs (global process and data owners):
Commercial, Manufacturing, Finance and Procurement. Each owns their domain in
every system that holds its data, SAP or not, including confidential data such
as formulas and recipes.

Each GPDO proposes how their domain breaks down: the data it covers, and who
owns each part, by subdomain, business unit or group of fields (attribute
owners). Where data is shared between domains, such as the material master,
the GPDOs agree who owns which part. They agree the proposals together, at the
monthly owner review or a working session, and record them in the domain
profiles, so that every piece of data has exactly one owner (R-02). The
data governance specialist provides the [profile template](domains/template.md)
and flags gaps and overlaps, but doesn't propose the breakdown.

## Who decides what

| Role | Held by [TBC] | Decides or does |
| --- | --- | --- |
| Data owner | The four GPDOs: Commercial, Manufacturing, Finance and Procurement | Decides, in their domain profile, how their data is classified, its validation and quality rules (conventions, checks, critical fields, duplicate rules and thresholds), which request types the app approves automatically, and what agents may do. Approves exceptions, and which roles can see their Confidential and Restricted data. Proposes how their domain breaks down, delegates attribute owners, and names the stewards for the parts they keep. |
| Attribute owner | Whoever a GPDO delegates part of their domain to, by subdomain, business unit or group of fields | Decides for that part, within the domain's conventions and checks: exceptions, automatic approvals and what agents may do. Names its steward. An owner of a group of fields also sets its conventions and checks. |
| Head of Data, AI & Development | [TBC: name] | Approves the rulebook, operating model, roadmap, controls catalogue and vendor requirements. Accountable for the data team's delivery: the app, the agents, the vendor and running this framework. |
| Data steward | A person or team named by each part's owner from their own team. One steward can cover several parts, or a whole domain. | Does the day-to-day work for their parts, listed below. Sets no rules and approves no exceptions. |
| Master data vendor | A third party, until the unified app takes over | Processes requests raised in the current app, and approves them within the rules. Sets no rules, approves no exceptions or mass changes, and confirms no sensitive changes. |
| Data governance specialist | The data team | Runs the framework day to day, listed below. Decides nothing about data content. |
| Platform team | The data team (the apps and the data platform) and the SAP team | Runs the data platform and the current app [TBC], builds the unified app, and runs the controls and the agent infrastructure. Decides nothing about data content. |

What a steward does, for their parts of a domain:

- answers questions from the vendor and requesters;
- decides likely duplicates;
- confirms sensitive changes, calling the supplier back before confirming new
  bank details (R-13, R-15);
- approves the requests the unified app doesn't approve automatically, and
  reviews a monthly sample of those it does (R-06);
- checks the monthly list of records to block before the owner approves it
  (R-11);
- agrees how data quality issues are fixed at source, and helps finish the
  clean-up of existing data after the vendor leaves (R-10).

What the data governance specialist does:

- runs the monthly owner review and the working sessions where the GPDOs
  agree profiles, and prepares the quarterly scorecard for the executive team;
- keeps the rulebook, operating model, controls catalogue and roadmap up to
  date, for the Head of Data, AI & Development to approve;
- provides the profile template and starters, and flags data with no owner
  or more than one (R-02);
- owns the agents: keeps the register, checks their accuracy and proposes
  changes to how far they may act (R-18);
- manages the master data vendor day to day, including its monthly
  performance review (R-12);
- trains and supports requesters, tracks exceptions until they expire
  (R-20), and keeps the list of systems in the data landscape.

## How documents are approved

| Document | Approved by |
| --- | --- |
| This charter | The four GPDOs and the Head of Data, AI & Development |
| Rulebook | The Head of Data, AI & Development. Every change goes in the change log and to the next monthly owner review. |
| Controls catalogue, vendor requirements, operating model and roadmap | The Head of Data, AI & Development |
| Domain profiles | Proposed by each GPDO for their own domain, and agreed by the GPDOs together. After that, each GPDO maintains theirs, and attribute owners approve changes to their part. |

Where documents differ, this charter wins, then the rulebook.

## Controls we never switch off

These can't be waived by exception, and changing them needs every signatory:

- A sensitive change can't be used until its steward or the field's owner
  confirms it, and nobody confirms a change they requested or entered (R-13).
  Payment data is kept apart from paying, and bank details are verified with
  the supplier (R-14, R-15).
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
| Finance GPDO | | |
| Procurement GPDO | | |
| Head of Data, AI & Development | | |
