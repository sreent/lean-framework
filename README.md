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
and margins. The [charter](charter.md) says what each covers and who owns it,
and the [roadmap](roadmap.md) says how and when we get there.

## Documents

| Document | What it holds | Approved by |
| --- | --- | --- |
| [Charter](charter.md) | Who owns what, who decides what, and the controls we never switch off | The four GPDOs and the Head of Data, AI & Development, once |
| [Rulebook](rulebook.md) | 22 rules: what must be true, and why | Head of Data, AI & Development |
| [Operating model](operating-model.md) | Who does what (RACI), the platform, the data landscape, the agent register, requesters, rhythm and measures | Head of Data, AI & Development |
| [Roadmap](roadmap.md) | The one document with dates, and the one place that describes the move to the unified app: the timeline, the critical path and clean-up | Head of Data, AI & Development |
| [Controls catalogue](controls.md) | How each rule is enforced, including what the unified app must do | Head of Data, AI & Development |
| [Vendor requirements](vendor-requirements.md) | What the master data vendor must deliver until it leaves, and how it hands over | Head of Data, AI & Development, through the contract |
| Domain profiles: one per GPDO, from the [template](domains/template.md), with [starter material](domains/starters/) for common SAP master data | Each domain's breakdown and owners, its validation and quality rules, and its other settings | Proposed by each GPDO, agreed by the GPDOs together |

## How it works

- **The business defines good data; the data team enforces it.** Each data
  owner sets their domain's validation and quality rules in its profile. The
  data team turns them into checks in the app and on the data platform, and
  can propose new ones, but the owner decides.
- **Rules and controls are separate.** The rulebook says what must be true; the
  controls catalogue says how. As the app replaces manual work, the controls
  change and the rules don't.
- **Quality is built in at entry, and causes get fixed.** Checks run when data
  is entered, not weeks later in a report. When the same issue keeps coming
  back, the fix is a new check, not another clean-up.
- **A steward for every part of a domain.** Named by the part's owner from
  their own team, the steward does the day-to-day work, from answering
  questions to confirming sensitive changes; the charter lists it. One steward
  can cover several parts.
- **App rules and AI agents are treated differently.** The app's fixed rules
  behave the same way every time and can be tested, so they may approve the
  request types owners choose. AI agents' judgements vary, so they only check,
  propose or make small approved fixes, and a person decides (R-18).
- **The checks on the data team come from outside it.** The data team manages
  the vendor, builds the app and runs the agents, but the business owns the
  data, stewards confirm sensitive changes, every SAP change is traced to an
  approved request, and someone outside the team reviews emergency access.

## Open decisions

`[TBC]` marks a default to confirm or a gap to fill. They come down to these:

- **The signatories:** when the charter takes effect, which company policies
  it applies, and who holds each role.
- **Each GPDO:** their domain profile, starting from the starters, and the
  systems outside SAP that hold their data. Commercial and Procurement also
  agree who owns the business partner data they share.
- **The Head of Data, AI & Development:** the numbers in the rulebook, the
  classification scheme, the approved AI tools, the vendor's targets, scope and
  location, who reviews emergency access and SAP changes without a request,
  and the roadmap's later dates, including the fallback if the vendor's exit
  slips.
- **The data team:** how each control works in practice, such as whether SAP's
  own confirmation of bank changes stays on, and the masking tool; the current
  app's name and who runs it; and how requesters are trained.
- **This page:** a recent example and a rough cost of each problem.
