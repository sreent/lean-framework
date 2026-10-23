# LEAN Framework

**Lean AI Data Governance, built on the LEAN framework.**

LEAN is the operating framework for the Lean AI Data Governance programme. It has
four pillars, one for each letter:

| Pillar | Principle |
| --- | --- |
| **L**ightweight policies | Only the rules that matter, kept short. |
| **E**mbedded controls | Quality, access and classification enforced in the pipelines. |
| **A**gent-operated | AI agents handle the routine governance tasks. |
| **N**amed ownership | Data owners stay accountable and approve exceptions. |

The first phase focuses on master data, mainly in SAP, plus the non-SAP systems
that hold the same suppliers, customers, materials and finance structures.

## Documents

| Document | What it covers | Status |
| --- | --- | --- |
| [LEAN framework](framework.md) | Scope, roles, decision rights, agent autonomy levels, exceptions, measures | Draft v0.2 |
| [Data governance policy](policy/data-governance-policy.md) | The 11 policy statements (P-01 to P-11) | Draft v0.2 |
| [Data classification standard](policy/standards/classification.md) | Classification levels, handling rules, default classifications | Draft v0.1 |
| [Master data standard](policy/standards/master-data.md) | Systems of record, requests, sensitive changes, quality, duplicates, lifecycle, domain profiles | Draft v0.1 |
| Controls catalogue | Each rule mapped to the control that enforces it | To do |
| Agent playbook | Agent tasks, autonomy levels and escalation | To do |
| Rollout plan | Pilot domain, baseline measures, phases | To do |

Items marked `[TBC]` in the drafts are defaults to confirm or replace.

## How the pillars fit together

- **L** sets the few rules that matter.
- **E** enforces those rules automatically in the pipelines.
- **A** runs the routine work of applying and monitoring them.
- **N** keeps a named person accountable, and the approver of anything outside
  the rules.

## Why LEAN

- **It matches the programme name.** "Lean AI Data Governance, built on the
  LEAN framework" is easy to remember.
- **It answers the accountability question up front.** Automation and agents
  do the routine work, but the N pillar makes clear that a named data owner
  remains accountable and approves exceptions.
