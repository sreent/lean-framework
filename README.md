# LEAN Framework

**Lean AI Data Governance, built on the LEAN framework.**

| Pillar | Principle |
| --- | --- |
| **L**ightweight policies | Only the rules that matter, kept short. |
| **E**mbedded controls | Rules enforced in SAP and the app, not left to memory. |
| **A**gent-operated | Automation and AI agents handle routine governance work. |
| **N**amed ownership | Data owners stay accountable and approve exceptions. |

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

## Scope

Four domains, one per GPDO (global process and data owner): Commercial,
Manufacturing, Finance and Procurement. The framework covers SAP master data,
non-SAP master data, and confidential data such as formulas, recipes, prices
and margins. The [charter](charter.md) says what each covers and which GPDO
owns it.

## Roadmap

The [roadmap](roadmap.md) says how and when we get there: the move from the
current app and the master data vendor to the unified master data app,
customer and supplier first, the critical path, cleaning up existing data, and
preparing requesters.

## Documents

| Document | What it holds | Approved by |
| --- | --- | --- |
| [Charter](charter.md) | Who owns what, who decides what, and the controls we never switch off | The four GPDOs and the Head of Data, AI & Development, once |
| [Rulebook](rulebook.md) | 22 rules: what must be true, and why | Head of Data, AI & Development |
| [Operating model](operating-model.md) | Who does what (RACI), the platform, the data landscape, the agent register, requesters, rhythm and measures | Head of Data, AI & Development |
| [Roadmap](roadmap.md) | The one document with dates: the move to the unified app, the critical path, clean-up and preparing requesters | Head of Data, AI & Development |
| [Controls catalogue](controls.md) | How each rule is enforced, before and after the unified app takes over. Doubles as the unified app's backlog. | Head of Data, AI & Development |
| [Vendor requirements](vendor-requirements.md) | What the master data vendor must deliver until it leaves, and how it hands over | Head of Data, AI & Development, through the contract |
| Domain profiles: one per GPDO, from the [template](domains/template.md), with [starter material](domains/starters/) for common SAP master data | Each domain's breakdown and owners, its validation and quality rules, and its other settings | Proposed by each GPDO, agreed by the GPDOs together |

Items marked `[TBC]` are defaults to confirm.

## How it works

- **The business defines good data; the data team enforces it.** Each data
  owner sets the validation and quality rules for their domain in its profile:
  conventions, mandatory checks, critical fields, duplicate rules and quality
  thresholds. The data team turns them into checks in the app and on the data
  platform, and can propose new ones, but the owner decides.
- **Rules and controls are separate.** The rulebook says what must be true; the
  controls catalogue says how. As the app replaces manual work, the controls
  change and the rules don't.
- **Quality is built in at entry, and causes get fixed.** Each domain agrees
  conventions for its key fields, and the checks that enforce them run when
  data is entered, not weeks later in a report. When the same issue keeps
  coming back, the fix is a new check, not another clean-up.
- **One steward for each part of a domain.** Each owner names a steward who
  answers questions, confirms sensitive changes and, once the unified app
  takes over, approves the requests it can't approve automatically. Until then,
  the master data vendor processes requests raised in the current app, helped
  by what the agents flag.
- **App rules and AI agents are treated differently.** The app's fixed rules
  behave the same way every time and can be tested, so they may approve
  routine requests. AI agents' judgements vary, so they only check, propose or
  make small approved fixes, and a person decides (R-18).
- **The checks on the data team come from outside it.** The data team manages
  the vendor, builds the app and runs the agents. The business owns the data
  and its settings, the steward confirms sensitive changes, every SAP
  change is traced to an approved request, and someone outside the team
  reviews emergency access.

The [operating model](operating-model.md) has the detail: who does what, the
platform, the agents, requesters, and the rhythm and measures.
