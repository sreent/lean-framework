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

Documents are split by who approves them, so the parts that change most need
the lightest sign-off.

| Tier | Document | Approved by | Status |
| --- | --- | --- | --- |
| Operating model | [LEAN framework](framework.md): scope, roles, automation and agents, measures | Executive sponsor, once | Draft v0.3 |
| Policy | [Data governance policy](policy/data-governance-policy.md): the four LEAN principles, controls that can't be waived, authority | CEO | Draft v0.3 |
| Standards | [Data governance standard](standards/data-governance.md) (DG-01 to DG-19) | Executive sponsor | Draft v0.1 |
| Standards | [Data classification standard](standards/classification.md) (CLS-01 to CLS-08) | Executive sponsor, with information security and the data protection officer | Draft v0.2 |
| Standards | [Master data standard](standards/master-data.md) (MD-01 to MD-26) | Executive sponsor, with the Financial Controller for payment controls | Draft v0.2 |
| Domain profiles | [Supplier](domains/supplier.md), [customer](domains/customer.md), [material](domains/material.md), [finance](domains/finance.md) | Each data owner | Draft v0.1 |
| To do | Controls catalogue, doubling as the app's backlog | Data governance specialist | – |
| To do | Rollout plan, including the clean-up of existing records | Executive sponsor | – |

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
