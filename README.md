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

Twelve of the twenty rules address these two problems. The other eight manage
risks that come with master data: payment fraud, privacy and audit.

## Scope

Four domains, one per GPDO (global process and data owner): Commercial,
Manufacturing, Finance and Procurement. Each GPDO proposes what master data
their domain covers, such as customers, pricing, materials, production data,
suppliers or finance structures, and how it breaks down by subdomain, business
unit or group of fields (see the [charter](charter.md)). SAP comes first: the
unified master data app covers SAP master data, and non-SAP copies are checked
against SAP until the app can take requests from those systems.

## Documents

| Document | What it holds | Approved by |
| --- | --- | --- |
| [Charter](charter.md) | Who owns what, who decides what, and the controls we never switch off | The four GPDOs and the Head of Data, AI & Development, once |
| [Rulebook](rulebook.md) | 20 rules: what must be true, and why | Head of Data, AI & Development |
| [Operating model](operating-model.md) | Who does what (RACI), the platform, the agent register, rhythm and measures | Head of Data, AI & Development |
| [Controls catalogue](controls.md) | How each rule is enforced today and once the app is live. Doubles as the app backlog. | Head of Data, AI & Development |
| [Vendor requirements](vendor-requirements.md) | What the master data vendor must deliver | Head of Data, AI & Development, through the contract |
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
- **The steward role moves from people to the app.** Today the vendor
  processes requests. Once the app is live, it approves routine request types
  automatically where the data owner has agreed, and agents pre-check the rest.
  A small exceptions team handles what's left.
- **App rules and AI agents are treated differently.** The app's fixed rules
  behave the same way every time and can be tested, so they may approve
  routine requests. AI agents' judgements vary, so they only check, propose or
  make small approved fixes, and a person decides (R-18).
- **The checks on the data team come from outside it.** The data team manages
  the vendor, builds the app and runs the agents. The business owns the data
  and its settings, the owner's team confirms sensitive changes, every SAP
  change is traced to an approved request, and someone outside the team
  reviews emergency access.

The [operating model](operating-model.md) has the detail: who does what, the
platform, the agents, and the rhythm and measures.

## Getting started

1. **Measure first.** Run the starter checks across the master data in scope as
   read-only scorecards. This needs little from the business beyond access to
   the data, and shows where the data is worst.
2. **Each GPDO proposes their domain profile,** using the template and the
   scorecards: how the domain breaks down, who owns each part, what's in scope
   first, and its validation and quality rules. The GPDOs agree the proposals
   together.
3. **Pilot one domain for about 90 days,** where the scorecards and the
   downstream impact are worst. Switch on its checks, and add the first two
   agents: the duplicate finder and the change reconciler.
4. **Expand based on the results,** as the app takes over request types.
