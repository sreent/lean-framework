# Master Data Governance Charter

**Status:** Draft v0.2 · **Signed by:** the four GPDOs and the Head of Data, AI & Development · **Effective from:** [TBC] · **Review:** yearly, and whenever a signatory changes

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

1. **Lightweight.** We keep only rules that address a real problem or risk,
   each with an ID, a reason and a control, and we involve as few people as
   possible.
2. **Embedded.** The unified master data app decides by default, and every
   control logs its own evidence. A person decides only where judgement or a
   fraud check needs one.
3. **Agent-operated.** AI agents do the coordination and routine work: they
   prepare, chase, route, draft and propose. People decide, and stay
   accountable.
4. **Named ownership.** Every piece of data has one named business owner, who
   sets its rules as settings in the app.

This charter describes the target setup. Until each request type moves to the
unified app, the [interim arrangements](interim.md) say how the rules apply.

## Who owns what

The data owners are the four GPDOs (global process and data owners):
Commercial, Manufacturing, Finance and Procurement. Each owns their domain in
every system that holds its data, SAP or not, including confidential data such
as formulas and recipes.

Each GPDO approves their own domain's profile: how it breaks down, who owns
each part, and its settings. They can delegate parts to attribute owners, by
subdomain, business unit or group of fields, but don't have to. Data that two
domains share, such as business partner central data or views of the material
master, is agreed by the two GPDOs concerned. Every piece of data has exactly
one owner (R-02), and the governance coordinator agent flags any field with no
owner or more than one.

## Who decides what

| Role | Held by [TBC] | Decides or does |
| --- | --- | --- |
| Data owner | The four GPDOs: Commercial, Manufacturing, Finance and Procurement | Decides, in their domain profile, how their data is classified, its validation and quality rules (conventions, checks, critical fields, duplicate rules and thresholds), which request types the app approves automatically, and what agents may do. Approves exceptions, mass changes, and which roles can see their Confidential and Restricted data. Names the steward. |
| Attribute owner | Optional: whoever a GPDO delegates part of their domain to | Decides for that part what the data owner would, within the domain's conventions and checks. |
| Data steward | One person or team per domain, named by its GPDO from their own team; more only where volume needs it | Decides what the app can't, listed below. Sets no rules and approves no exceptions. |
| Head of Data, AI & Development | [TBC: name] | Approves the rulebook, operating model, controls catalogue, roadmap and interim arrangements. Accountable for the data team's delivery: the app, the data platform, the agents, the move to the target, and running this framework. |
| Data team | The data governance specialist, and the platform team, which includes the SAP team | The platform team builds and runs the unified app, the data platform and the agents. The specialist runs the framework, listed below. Decides nothing about data content. |
| Internal controls | [TBC: the internal controls team] | Reviews emergency access and any change made without a request (R-08, R-19). |

What a steward does. Agents prepare each decision and chase what's overdue;
the steward decides:

- confirms sensitive changes, after calling the supplier back on new bank
  details (R-13, R-15);
- decides likely duplicates, and the requests the app can't approve
  automatically (R-05, R-06);
- reviews a monthly sample of automatic approvals (R-06);
- approves fixes, and the list of records to block (R-10, R-11);
- answers the questions the request assistant can't.

What the data governance specialist does. The governance coordinator agent
prepares and chases; the specialist:

- supervises the agents as their owner: keeps the register, checks their
  accuracy and handles what they escalate (R-18);
- runs the owner review, and keeps the rulebook, operating model, controls
  catalogue and roadmap up to date, for the Head of Data, AI & Development to
  approve;
- provides the profile template and starters, and makes sure requesters are
  trained.

## How documents are approved

| Document | Approved by |
| --- | --- |
| This charter | The four GPDOs and the Head of Data, AI & Development |
| Rulebook | The Head of Data, AI & Development. Every change goes in the change log and to the next owner review. |
| Operating model, controls catalogue, roadmap and interim arrangements | The Head of Data, AI & Development |
| Domain profiles | Each GPDO, for their own domain; data two domains share needs both GPDOs. Attribute owners approve changes to their part. |

Where documents differ, this charter wins, then the rulebook.

## Controls we never switch off

These can't be waived by exception, and changing them needs every signatory:

- A sensitive change can't be used until its steward or the field's owner
  confirms it, and nobody confirms a change they requested or entered (R-13).
  Payment data is kept apart from paying, and bank details are verified with
  the supplier (R-14, R-15).
- Agents never approve requests or exceptions, confirm sensitive changes,
  change sensitive fields, delete records or grant access (R-18).
- Trade secrets, such as formulas and recipes, never go to an AI model outside
  an environment the organisation controls (R-21).
- The data team can't change master data outside the governed process, except
  through emergency access that internal controls reviews. Every change can be
  traced to an approved request (R-08, R-19).
- No one approves their own request, exception or agent.

## Escalation and visibility

- Questions go to the request assistant first, then the steward, then the
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
