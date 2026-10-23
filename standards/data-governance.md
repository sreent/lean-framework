# Data Governance Standard

**Status:** Draft v0.1 · **Owner:** [TBC: data governance specialist] · **Approved by:** [TBC: executive sponsor] · **Issued under:** [Data governance policy](../policy/data-governance-policy.md)

## Purpose

This standard sets the rules that apply to every master data domain: ownership,
how data is changed, third parties, automation and agents, and exceptions. The
[classification standard](classification.md) and the
[master data standard](master-data.md) add the detail, and the
[LEAN framework](../framework.md) explains how it all fits together.

## Scope

It applies to everyone who creates, changes, uses or distributes master data in
scope, in SAP and non-SAP systems: employees, contractors and third parties
such as the master data vendor. It applies to automation and AI agents through
the people accountable for them.

## Ownership

- **DG-01** Every master data domain has a named data owner, appointed by the
  executive sponsor. The data owner is accountable for the domain's data,
  however it is changed: by people, a vendor, the app or agents.
- **DG-02** A data owner may delegate ownership of a group of fields to another
  named leader, an attribute group owner, when that leader's function carries
  the financial, legal or tax risk of those fields. The domain profile records
  the delegation and the fields, and both owners sign it.

## Changing master data

- **DG-03** Master data is created and changed only through the governed
  process for its domain, starting with a complete request. Direct table
  updates are not allowed, except through logged emergency access (DG-17).
- **DG-04** Each domain, or each attribute group within it, has one system of
  record. Other systems take the data from it and send changes back as
  requests; they don't maintain their own version.
- **DG-05** A record passes its domain's mandatory checks before it can be used
  in a transaction.
- **DG-06** Every new record is checked for duplicates before it is created.
- **DG-07** A change to a sensitive attribute, such as bank details, payment
  terms or a credit limit, can't be used until a second person, outside the
  team that entered it, has confirmed it.

## Access, lifecycle and quality

- **DG-08** Every master data attribute is classified under the classification
  standard. Access follows the classification and is limited to what each role
  needs.
- **DG-09** Records unused for a set period are reviewed and blocked. Records
  are archived and deleted only in line with legal retention requirements.
- **DG-10** Data quality is measured against the owners' thresholds and
  published monthly for each domain. Issues are fixed in the system of record.

## Third parties

- **DG-11** Third parties that maintain master data, such as the master data
  vendor, work only within the standards, under a contract that includes them.
  They never set rules, approve exceptions or confirm sensitive changes. The
  data governance specialist manages their performance against the standards.

## Automation and agents

- **DG-12** The app may approve a request automatically only if the data owner
  has approved that request type for automatic processing and every check
  passes. Automatic approvals are logged, and a sample is reviewed each month.
- **DG-13** Every AI agent is registered with its purpose, domains, autonomy
  level, version, the systems it touches and a named agent owner in the data
  team. It acts only within the autonomy level approved by the data owner of
  each domain it works in. An agent that doesn't touch master data, such as one
  that chases exception expiry dates, is approved by the executive sponsor.
- **DG-14** New agents start at level 0 or 1. Moving up a level needs the agent
  owner's recommendation, accuracy checked on an independent sample [TBC: e.g.
  at least 98% over four weeks] and the owner's approval. An agent drops a
  level after a serious error, or when its sampled accuracy falls below the
  threshold. A change to an agent's model, instructions or tools is tested
  before release, and the owner re-approves its level if the change affects
  what it does. At level 2, an agent makes only the change types the owner has
  approved, which never include sensitive attributes. Each change goes through
  the app, and each run stays below the mass-change size (MD-10).
- **DG-15** Agents never approve requests or exceptions, change sensitive
  attributes, delete records or grant access. Their access is granted through
  the normal access approval, never by the people who build them. Content from
  outside the organisation, such as supplier emails and documents, is treated
  as data to check, never as instructions to follow.
- **DG-16** Every agent action is logged with its input, output and reason, and
  kept for at least as long as the related SAP change documents [TBC]. Any
  steward, owner or agent owner can pause an agent in their domain; the agent
  owner then investigates.

## Separation of duties in the data team

- **DG-17** People who build or change the app or the agents can't change
  production master data outside the app's workflow, except through logged
  emergency access. Someone outside the data team reviews every use of
  emergency access [TBC: e.g. the internal controls team]. Changes to the app
  and the agents are tested and released through change management, never
  edited directly in production.

## Exceptions

- **DG-18** Exceptions to any standard are approved by the data owner, or by
  the attribute group owner for delegated fields, and never by the person who
  asked for them. Each one is recorded in the exception register with the rule
  ID, the records affected, the reason, the approver, the expiry date and any
  compensating control. Every exception expires after at most [TBC: 90 days]
  and can be renewed once; after that, only the executive sponsor can extend
  it. These can't be waived: DG-07, DG-15, DG-17, MD-11 to MD-16, and the ban
  on approving your own request, exception or agent.

## Effective date

- **DG-19** This standard takes effect on [TBC: date]. From then, its rules
  apply to every new and changed record. Existing records are brought into
  line domain by domain under the clean-up plan in the rollout plan. Until
  then, gaps in existing records are tracked on the scorecards rather than
  treated as breaches.

## Compliance

Controls are designed to detect breaches automatically and report them to the
data owner. Deliberately bypassing a governed process, or repeatedly breaching
this standard, is handled under [TBC: the normal disciplinary process].

## Change history

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 2026-10-23 | First draft, from the rules previously in the policy (P-01 to P-11) and the framework, with fixes from the first review |
