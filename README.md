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
unit or group of fields (see the [charter](charter.md)). SAP comes first,
and non-SAP copies are checked against SAP until the unified master data app
can take requests from those systems.

## Where we're heading

The master data vendor leaves in Q2 2027, and the unified master data app and
agents take over its work. Only creating and changing master data waits for
the unified app: the data platform and agents check, measure and propose from
now on.

| | Until Q2 2027 | From Q2 2027 |
| --- | --- | --- |
| Requests raised in | The current app | The unified master data app |
| Master data created and changed by | The master data vendor, in SAP | The unified app, posting approved requests to SAP |
| Requests approved by | The vendor, within the rules | The unified app, for request types the owner has approved; otherwise a person each owner names |
| Sensitive changes confirmed by | The owner's team | The owner's team |
| Platform | The data platform runs the checks and scorecards on SAP data while the unified app is built | The unified app also checks every request on entry |
| Agents | Check, measure and propose: they pre-check requests, find duplicates, triage quality issues, reconcile changes and compare copies. They never create or change master data. | Can also prepare requests and make approved, non-sensitive changes, through the unified app |

Request types move to the unified app one at a time, each once the app handles
it and requesters are trained, with a fallback for anything not ready by
Q2 2027. [TBC: the unified app's go-live plan]

## Documents

| Document | What it holds | Approved by |
| --- | --- | --- |
| [Charter](charter.md) | Who owns what, who decides what, and the controls we never switch off | The four GPDOs and the Head of Data, AI & Development, once |
| [Rulebook](rulebook.md) | 20 rules: what must be true, and why | Head of Data, AI & Development |
| [Operating model](operating-model.md) | Who does what (RACI), the platform, the agent register, rhythm and measures | Head of Data, AI & Development |
| [Controls catalogue](controls.md) | How each rule is enforced until Q2 2027 and once the unified app takes over. Doubles as the unified app's backlog. | Head of Data, AI & Development |
| [Vendor requirements](vendor-requirements.md) | What the master data vendor must deliver until it leaves in Q2 2027, and how it hands over | Head of Data, AI & Development, through the contract |
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
- **The steward role moves from the vendor to the app.** Until Q2 2027 the
  vendor processes requests raised in the current app, helped by what the
  agents flag. After that, the unified app approves routine request types
  automatically where the owner has agreed, agents prepare and pre-check the
  rest, and a person each owner names decides what can't be automated.
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
4. **Add the other agents before Q2 2027,** working on the current app's
   requests and on the data platform. They check and propose; the vendor still
   makes every change.
5. **Move to the unified app by Q2 2027,** one request type at a time,
   retiring the vendor as each type moves.
6. **Expand based on the results** to the other domains.
