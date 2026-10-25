# Master Data Governance Charter

**Status:** Draft v0.4 · **Signed by:** the four GPDOs and the Head of Data, AI & Development · **Effective from:** [TBC] · **Review:** yearly, and whenever a signatory changes

## Purpose

Data quality problems across the business trace back to master data that is
incorrect or inconsistent. This charter is our agreement on who owns master
data, who decides what, and the few controls we never switch off. The
[rulebook](rulebook.md) holds the rules, the [controls catalogue](controls.md)
says how each one is enforced, the [operating model](operating-model.md) shows
who does what day to day, and each domain's profile holds its settings.

It applies the company's existing policies to master data, and doesn't replace
them.

## Scope

The framework covers three kinds of data, across four domains, one per GPDO
(see below):

- **SAP master data,** governed in full from the start.
- **Non-SAP master data,** such as data in CRM, PLM or e-commerce systems:
  owned and protected now, and brought under the other rules one system at a
  time, when its GPDO proposes it.
- **Confidential data,** such as formulas, recipes, prices, margins and
  supplier terms, in SAP or not: owned, classified and protected now.

The [operating model](operating-model.md) lists the systems involved and how
each comes in, and the rulebook says which rules apply everywhere from the
start.

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

## Who owns what

The data owners are the four GPDOs (global process and data owners):
Commercial, Manufacturing, Finance and Procurement. Each owns their domain in
every system that holds its data, SAP or not, including confidential data such
as formulas and recipes, and stays accountable for all of it (R-01).

Each GPDO breaks their domain into parts, by subdomain, business unit or group
of fields, and delegates each part to an attribute owner, usually someone
closer to the data. The GPDO keeps what spans the domain: the breakdown and who
owns each part, the conventions that apply across it, data shared with other
domains, and anything escalated to them. The attribute owner decides the rest
for their part. A GPDO can keep a part, and is then its attribute owner.

Data that two domains share, such as business partner central data or views of
the material master, is agreed by the two GPDOs concerned. Every piece of data
has exactly one owner (R-02), and the governance coordinator agent flags any
field with no owner or more than one.

## Who decides what

| Role | Held by [TBC] | Decides or does |
| --- | --- | --- |
| Data owner | The four GPDOs: Commercial, Manufacturing, Finance and Procurement | Accountable for their whole domain. Approves its breakdown, who owns each part, the conventions that apply across it, and data shared with other domains. Decides what's escalated to them. |
| Attribute owner | Named by the GPDO for each part of their domain | Decides for their part: its settings in the domain profile (classification, checks, critical fields, duplicate rules, thresholds, which request types the app approves automatically, and what agents may do), its exceptions and mass changes, and who can see its classified data. An owner of a group of fields also sets its conventions. Decides the cases the app can't, or names delegates to decide them. |
| Head of Data, AI & Development | [TBC: name] | The platform owner: accountable for the unified app, the data platform and the agents, for the data team that builds and runs them, and for running this framework. Approves the rulebook, operating model and controls catalogue. Decides nothing about data content. |
| Data team | The data governance specialist, and the platform team, which includes the SAP team | The platform team builds and runs the unified app, the data platform and the agents. The specialist runs the framework, listed below. Decides nothing about data content. |
| Internal controls | The internal controls team [TBC: name] | Reviews emergency access, any change made without a request, and a sample of the change reconciler's matches (R-08, R-19). |

**Delegates.** An attribute owner can name delegates, from their own team or
another, at least two so that someone is always available, to decide the cases
the app can't:

- confirming sensitive changes, after calling the supplier back for bank
  details (R-13, R-15);
- deciding likely duplicates (R-05);
- approving requests the app doesn't approve automatically, and reviewing a
  monthly sample of those it does (R-06).

The owner stays accountable, and keeps settings, exceptions, mass changes and
access. Nobody confirms a change they requested or entered, and whoever
confirms payment data holds no rights to raise purchase orders, post invoices,
run payments or release credit (R-13, R-14). Agents prepare each case and
chase what's overdue. The [operating model](operating-model.md) lists each
role's tasks and how often they come up.

What the data governance specialist does. The governance coordinator agent
prepares and chases; the specialist:

- supervises the agents as their owner: keeps the register, checks their
  accuracy and handles what they escalate (R-18);
- runs the owner review, and keeps the rulebook, operating model and controls
  catalogue up to date, for the Head of Data, AI & Development to approve;
- provides the profile template and starters, and makes sure requesters,
  attribute owners and delegates are trained.

## How documents are approved

| Document | Approved by |
| --- | --- |
| This charter | The four GPDOs and the Head of Data, AI & Development |
| Rulebook | The Head of Data, AI & Development. Every change goes in the change log, and a change that adds work for owners or delegates goes to the owner review before it takes effect. |
| Operating model and controls catalogue | The Head of Data, AI & Development |
| Domain profiles | The GPDO approves the breakdown and the conventions across the domain, and each attribute owner their part's settings. Data two domains share needs both GPDOs. |

Where documents differ, this charter wins, then the rulebook.

## Controls we never switch off

These can't be waived by exception, and changing them needs every signatory:

- A sensitive change can't be used until its owner or their delegate confirms
  it, and nobody confirms a change they requested or entered (R-13). Payment
  data is kept apart from paying, and bank details are verified with the
  supplier (R-14, R-15).
- Agents never approve requests or exceptions, confirm sensitive changes,
  change sensitive fields, delete records or grant access (R-18).
- Trade secrets, such as formulas and recipes, never go to an AI model outside
  an environment the organisation controls: its own systems, or a provider's
  service under a contract that stops the provider keeping or training on the
  data (R-21).
- The data team can't change master data outside the governed process, except
  through emergency access that internal controls reviews. Every change can be
  traced to an approved request (R-08, R-19).
- No one approves their own request, exception or agent.

## Escalation and visibility

- Questions go to the request assistant first, then the attribute owner or
  their delegate, then the GPDO. If GPDOs disagree with each other or with the
  Head of Data, AI & Development, the executive they both report to decides.
- The GPDOs meet at the owner review: monthly at first, then quarterly.
- A one-page scorecard goes to the executive team every quarter.

## Signatures

| Role | Name | Date |
| --- | --- | --- |
| Commercial GPDO | | |
| Manufacturing GPDO | | |
| Finance GPDO | | |
| Procurement GPDO | | |
| Head of Data, AI & Development | | |
