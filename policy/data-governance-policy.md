# Data Governance Policy

**Status:** Draft v0.1 · **Owner:** [TBC: executive sponsor] · **Approved by:** [TBC] · **Review:** yearly

## Purpose

Master data is the suppliers, customers, materials and finance structures that
every transaction relies on. It must be accurate, owned and controlled. This
policy sets the rules. The [LEAN framework](../framework.md) explains how they
are run, and the standards add the detail.

## Scope

This policy applies to everyone who creates, changes, uses or distributes master
data that is in scope, in SAP and non-SAP systems: employees, contractors, third
parties acting for us, and AI agents. The framework lists the domains in scope.

## Policy statements

- **P-01 Named ownership.** Every master data domain has a named data owner who
  is accountable for its quality and approves exceptions.
- **P-02 Governed change.** Master data is created and changed only through the
  governed process for its domain. Direct table updates are not allowed. Mass
  changes use the approved mass-change process.
- **P-03 One system of record.** Each domain, or each attribute group within it,
  has one system of record. Other systems take the data from it and send changes
  back as requests; they don't maintain their own version.
- **P-04 Quality at entry.** A record passes its domain's mandatory checks before
  it can be used in a transaction.
- **P-05 Search before create.** Every new record is checked for duplicates
  before it is created.
- **P-06 Dual control for sensitive changes.** A change to a sensitive attribute,
  such as bank details, payment terms or a credit limit, takes effect only after
  a second person has verified it.
- **P-07 Classification and least-privilege access.** Every master data attribute
  is classified under the classification standard. Access follows the
  classification and is limited to what each role needs.
- **P-08 Managed lifecycle.** Records unused for a set period are reviewed and
  blocked. Records are archived and deleted only in line with legal retention
  requirements.
- **P-09 Measured quality.** Data quality is measured against the owner's
  thresholds and published monthly for each domain. Issues are fixed in the
  system of record.
- **P-10 Governed AI agents.** AI agents act only within their approved autonomy
  level, under a named owner, with every action logged. Agents never approve
  requests or exceptions, change sensitive attributes or grant access.
- **P-11 Time-limited exceptions.** Exceptions to this policy or its standards
  are approved by the relevant data owner, expire, and are recorded in the
  exception register.

## Responsibilities

Roles are defined in section 5 of the framework. In short: data owners are
accountable for their domain, data stewards run it day to day, the platform team
builds and runs the controls, requesters raise complete and correct requests,
and the governance lead keeps this policy current.

## Compliance

Controls detect most breaches automatically and report them to the data owner.
Deliberately bypassing a governed process, or repeatedly breaching this policy,
is handled under [TBC: the normal disciplinary process].

## Related documents

- [LEAN framework](../framework.md)
- [Data classification standard](standards/classification.md)
- [Master data standard](standards/master-data.md)

## Change history

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 2026-10-23 | First draft |
