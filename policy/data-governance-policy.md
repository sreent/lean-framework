# Data Governance Policy

**Status:** Draft v0.3 · **Owner:** [TBC: executive sponsor] · **Approved by:** [TBC: CEO] · **Effective from:** [TBC] · **Review:** every three years, or after a major change

> [TBC] If an existing CEO-approved policy already covers data or information,
> such as an information security or information management policy, add the
> principles, controls and authority in sections 3 to 5 to it instead, and drop
> this document.

## 1. Purpose

Master data is the suppliers, customers, materials and finance structures that
every transaction relies on. It must be accurate, owned and controlled. This
policy sets the principles; the standards issued under it set the rules.

## 2. Scope

This policy covers the data that the data governance standards bring into
scope, in SAP and non-SAP systems. Today that is master data. It applies to
everyone who creates, changes or uses that data: employees, contractors, third
parties acting for us, and automation and AI agents through the people
accountable for them.

## 3. Principles

1. **Lightweight rules.** We keep only the rules that matter. Each has an owner
   and a control, and rules that can't be enforced are removed.
2. **Embedded controls.** Data is created and changed only through governed
   processes. Rules are enforced in the systems that handle the data,
   automatically wherever possible. Changes that carry financial or fraud risk
   are confirmed by a second, independent person.
3. **Agent-operated, people accountable.** Automation and AI agents may do
   routine governance work, but only within limits that data owners set, and
   every action is traceable to an accountable person.
4. **Named ownership.** Every data domain has a named business owner who is
   accountable for its data and approves exceptions.

## 4. Controls that can't be waived

These controls apply even when an exception is approved, and only the CEO can
change them:

- A change to bank details or other payment data is confirmed by a second
  person, outside the team that entered it, who can't also process payments.
- AI agents never approve requests, exceptions or access, and never change
  sensitive data.
- No one approves their own request, exception or agent.

## 5. Authority

- The executive sponsor [TBC: role] issues and changes the data governance
  standards under this policy, and appoints the data owners.
- Data owners maintain the profiles for their domains, within the standards.
- Exceptions to the standards are approved as the standards set out.

## 6. Compliance

Deliberately bypassing a governed process, or repeatedly breaching this policy
or its standards, is handled under [TBC: the normal disciplinary process].

## 7. Related documents

- [LEAN framework](../framework.md)
- [Data governance standard](../standards/data-governance.md)
- [Data classification standard](../standards/classification.md)
- [Master data standard](../standards/master-data.md)

## Change history

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 2026-10-23 | First draft |
| 0.2 | 2026-10-23 | P-10 and responsibilities updated for the simplified roles |
| 0.3 | 2026-10-23 | Reduced to principles, controls that can't be waived, and authority, so it rarely needs CEO re-approval. The rules moved to the data governance standard. |
