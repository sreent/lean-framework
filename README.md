# LEAN Framework

**Lean AI Data Governance, built on the LEAN framework.**

| Pillar | Principle |
| --- | --- |
| **L**ightweight policies | Only the rules that matter, and as few people as possible. |
| **E**mbedded controls | The app decides by default and logs its own evidence. |
| **A**gent-operated | AI agents do the coordination and routine work. |
| **N**amed ownership | Every piece of data has one named owner, who sets its rules. |

## The problem

Data quality issues across the business trace back to master data that is:

- **Incorrect:** missing or wrong values, such as units of measure, payment
  terms, addresses or valuation, that break transactions and mislead reports.
- **Inconsistent:** the same supplier, customer or material recorded
  differently. It may be duplicated, follow different conventions, or differ
  between SAP and non-SAP systems.

[TBC: add a recent example and a rough cost for each.]

Twelve of the twenty-two rules address these two problems. The other ten
manage risks that come with master data: trade secrets, payment fraud,
privacy and audit.

## The target setup

Technology runs governance, and people decide.

| Layer | Who or what | Does |
| --- | --- | --- |
| Own | The four GPDOs, and the attribute owners they delegate each part of their domain to | GPDOs set the domain's breakdown and conventions. Attribute owners set their part's rules as settings in the unified app, and decide what the app can't, themselves or through delegates. |
| Enforce | The unified app, SAP and the data platform | Check every request, approve what passes, hold sensitive changes, measure quality and log the evidence |
| Coordinate | AI agents | Prepare, chase, route, draft and propose, and flag what needs a person's judgement |
| Run | The data team, under the Head of Data, AI & Development | Build and run the app, the data platform and the agents, and run the framework |
| Assure | Internal controls | Review emergency access and any change made without a request |

Requesters enter the data themselves. A routine change involves one person,
the requester. A sensitive change involves two: the requester, and the
attribute owner or their delegate who confirms it.

## Scope

Four domains, one per GPDO (global process and data owner): Commercial,
Manufacturing, Finance and Procurement. The framework covers SAP master data,
non-SAP master data, and confidential data such as formulas, recipes, prices
and margins. The [charter](charter.md) says who owns what, and the
[template](domains/template.md) suggests which data each domain starts with.

## Documents

| Document | What it holds | Approved by |
| --- | --- | --- |
| [Charter](charter.md) | Who owns what, who decides what, and the controls we never switch off | The four GPDOs and the Head of Data, AI & Development, once |
| [Rulebook](rulebook.md) | 22 rules: what must be true, and why | Head of Data, AI & Development |
| [Operating model](operating-model.md) | Who does what and how often, the platform, the agents, the data landscape, requesters, rhythm and measures | Head of Data, AI & Development |
| [Controls catalogue](controls.md) | How each rule is enforced, and the evidence each control logs | Head of Data, AI & Development |
| Domain profiles: one per GPDO, from the [template](domains/template.md), with [starter material](domains/starters/) for common SAP master data | Each domain's breakdown and owners, its validation and quality rules, and its other settings | The GPDO approves the breakdown, and each attribute owner their part's settings |

## Open decisions

`[TBC]` marks a default to confirm or a gap to fill. None of them needs
settling before the charter is signed:

- **At signing:** who holds each role, and the date the charter takes effect.
- **In the domain profiles, after signing:** each GPDO's breakdown and
  attribute owners, each part's settings and delegates, and who owns the
  business partner data that Commercial and Procurement share.
- **As the setup is built:** the numbers and classification scheme in the
  rulebook, the approved AI tools, and how each control works in practice.
- **This page:** a recent example and a rough cost of each problem.
