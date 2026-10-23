# Master Data Standard

**Status:** Draft v0.2 · **Owner:** [TBC: data governance specialist, with the data owners] · **Approved by:** [TBC: executive sponsor, with the Financial Controller for the payment controls in MD-12 to MD-16] · **Implements:** DG-03 to DG-07, DG-09, DG-10

## Purpose

This standard sets the rules every master data domain follows, in SAP and
non-SAP systems: where each record is mastered, how it is requested and
changed, how sensitive changes, quality and duplicates are controlled, and how
records are retired. Each domain's profile, maintained by its data owner, sets
the parameters these rules refer to (see the end of this document).

## Systems of record

- **MD-01** Each domain profile names the system of record for each attribute
  group. By default SAP is the system of record for supplier, customer,
  material and finance master data. A non-SAP system is the system of record
  for attributes that exist only there, such as sales contacts in CRM or
  engineering attributes in PLM. Those attributes are governed through
  ownership, classification and scheduled quality checks. [TBC: if there is
  more than one SAP system, name the one that is the system of record]
- **MD-02** Data flows out from the system of record. A system that receives
  the data doesn't change its copy; it raises a change request at the source.
  Interfaces reject or quarantine inbound changes to attributes the sending
  system doesn't own, using checks built into the interface or middleware.
- **MD-03** A non-SAP system that needs a new record that SAP holds, such as a
  new customer from e-commerce, raises a create request through the governed
  workflow, where the same checks apply. It doesn't create its own unmanaged
  version.
- **MD-04** Every copy of a record holds the record's key in the system of
  record, such as the SAP business partner number in CRM, so records can be
  matched exactly.
- **MD-05** In S/4HANA, a business partner's central data (name, address, tax
  numbers and bank details) is shared by its supplier and customer roles. It
  has one owner, whichever roles the business partner has. [TBC: for example
  the Financial Controller as attribute group owner, with the supplier and
  customer data owners consulted]

## Requests and approval

- **MD-06** Create and change requests go through the governed workflow that
  the domain profile names, not email or spreadsheets. Each request includes
  the domain's mandatory data. Extending a record to a new company code, sales
  area or plant is a request like any other.
- **MD-07** Every request is pre-checked for completeness, validity against
  reference data and possible duplicates before anyone approves it. An agent
  may run the pre-check at autonomy level 1.
- **MD-08** A data steward approves routine requests within the rules set by
  the data owner, or by the attribute group owner for delegated fields. Request
  types the data owner has approved for automatic processing are approved by
  the app instead (DG-12). The person who raises or enters a request can't also
  approve it.
- **MD-09** Requests are completed within the turnaround times in the domain
  profile, and cycle times are reported monthly. Urgency never waives the
  sensitive-change rules (MD-12 to MD-16).
- **MD-10** A change to more than [TBC: 50] records is a mass change. It needs
  the data owner's sign-off, a test in a non-production system and a rollback
  plan, and it runs only through approved mass-change tools.
- **MD-11** In SAP, only the app's service identity and named stewards hold
  authorisations to create or change master data, apart from emergency access
  (DG-17). Each month, SAP change documents are reconciled to approved
  requests, and any change without one is investigated.

## Sensitive attributes

- **MD-12** Each domain profile lists its sensitive attributes. A change to one
  can't be used until a second person, outside the team that entered it, has
  confirmed it (DG-07). Once the app is live, it holds the change until it is
  confirmed and only then posts it to SAP; until then, the change is confirmed
  before the vendor enters it. For suppliers and customers, SAP's
  sensitive-field settings are a second line: the account stays blocked for
  payment until a second user confirms the change, for example with FK08/FK09
  for suppliers and FD08/FD09 for customers. Credit limits, and material and
  finance attributes, fall outside that SAP mechanism, so confirmation before
  posting and the MD-11 reconciliation are the controls. [TBC: confirm for
  your SAP release]
- **MD-13** Whoever enters or confirms a change to payment data holds no rights
  to create purchase orders, post invoices, run payments or release credit.
- **MD-14** Before a change to a supplier's bank details is confirmed, the
  person confirming it verifies it with the supplier, using contact details
  that were on file before the request and haven't changed in the last
  [TBC: 90 days], or that come from an independent source. Evidence of the
  verification is kept with the request.
- **MD-15** A bank account that already belongs to another supplier or
  customer is flagged for review before the change is confirmed. [TBC: also
  check against employee bank accounts, which needs agreement with HR]
- **MD-16** Routes around these controls are treated as sensitive changes:
  unblocking a blocked supplier or customer, and bank details entered on a
  one-time account or as a payee in a document. Their use is limited to the
  cases set in the domain profile.

## Data quality

- **MD-17** Each domain profile names its critical attributes: those that, if
  wrong, stop or misdirect a transaction. Critical attributes are checked at
  entry, not only at rest.
- **MD-18** Checks cover six dimensions:
  - **completeness:** required fields are filled;
  - **validity:** values match formats and reference data, such as IBAN check
    digits, VAT numbers and units of measure;
  - **accuracy:** values match the real world, checked against external
    sources or by sampling;
  - **uniqueness:** there are no duplicates;
  - **consistency:** a record matches across the systems that hold it;
  - **timeliness:** records are reviewed when they go unused or out of date.
- **MD-19** The data owner sets a threshold for each check in the domain
  profile. Results are published monthly on each domain's scorecard.
- **MD-20** Issues are fixed in the system of record, never only in a
  downstream copy or report.
- **MD-21** The reference lists that checks rely on, such as payment terms,
  material groups and account groups, belong to the owner of the fields that
  use them. In SAP they are configuration, so they change through SAP change
  management.

## Duplicates

- **MD-22** A duplicate check runs on every create, using the domain's match
  rules. A likely duplicate stops the request until a steward decides.
- **MD-23** When a duplicate is confirmed, one record is kept as the survivor.
  The other is blocked and points to the survivor, once its open transactions
  have been completed or moved.

## Lifecycle

- **MD-24** Each month, records with no activity for the period in the domain
  profile are listed. Each one is blocked unless a steward or the business
  confirms it is still needed. The data owner approves the list as a whole, not
  record by record. Records with open items, open orders or contracts, and
  those the domain profile excludes, aren't blocked.
- **MD-25** A blocked record with no further activity is flagged for deletion.
  It is archived once SAP allows, after its transactions have been archived,
  and in line with legal retention requirements.
- **MD-26** Personal data in master data is blocked once the purpose for
  holding it has ended, and deleted when its retention period ends.
  [TBC: SAP Information Lifecycle Management end-of-purpose checks]

## Domain profiles

Each domain has a profile that sets the parameters these rules refer to:
owners, the governed workflow, systems of record, critical and sensitive
attributes, checks and thresholds, duplicate match rules, inactivity periods
and exclusions, and the request types and agent changes the owner has
approved. The data owner maintains and approves it, with attribute group
owners for their fields, within this standard.

- [Supplier](../domains/supplier.md)
- [Customer](../domains/customer.md)
- [Material / product](../domains/material.md)
- [Finance](../domains/finance.md)

## Change history

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 2026-10-23 | First draft |
| 0.2 | 2026-10-23 | Rules renumbered and domain profiles moved to their own files. Added business partner central data, SAP authorisations and reconciliation, separation of duties for payment data, routes around the controls, accuracy, reference lists and end-of-purpose blocking. |
