# Master Data Standard

**Status:** Draft v0.1 · **Owner:** [TBC: governance lead, with the data owners] · **Implements:** P-02 to P-06, P-08, P-09

## Purpose

This standard sets the rules every master data domain follows, in SAP and non-SAP
systems: where each record is mastered, how it is requested and changed, how
quality and duplicates are controlled, and how records are retired. The domain
profiles at the end hold the detail for each domain.

## Systems of record

- **MD-01** Each domain profile names the system of record for each attribute
  group. By default SAP is the system of record for supplier, customer, material
  and finance master data. A non-SAP system may be the system of record for a
  specific attribute group, such as sales contacts in CRM or engineering
  attributes in PLM. [TBC]
- **MD-02** Data flows out from the system of record. A system that receives the
  data doesn't change its copy; it raises a change request at the source.
  Interfaces reject or quarantine inbound changes to attributes the sending
  system doesn't own.
- **MD-03** A non-SAP system that needs a new record, such as a new customer from
  e-commerce, sends a create request to the system of record, where the same
  checks apply. It doesn't create its own unmanaged version.
- **MD-04** Every copy of a record holds the record's key in the system of
  record, such as the SAP business partner number in CRM, so records can be
  matched exactly.

## Requests and approval

- **MD-05** Create and change requests go through the governed workflow
  [TBC: SAP MDG, or a workflow tool such as ServiceNow], not email or
  spreadsheets. Each request includes the domain's mandatory data.
- **MD-06** Every request is pre-checked for completeness, validity against
  reference data and possible duplicates before anyone approves it. An agent may
  run the pre-check at autonomy level 1.
- **MD-07** A data steward approves routine requests. The person who raises or
  enters a request can't also approve it.
- **MD-08** Requests are completed within [TBC: 2 business days for standard
  requests, 4 business hours for urgent ones]. Cycle times are reported monthly.
- **MD-09** A change to more than [TBC: 50] records is a mass change. It needs the
  data owner's sign-off, a test in a non-production system and a rollback plan,
  and it runs only through approved mass-change tools. Direct table updates are
  never allowed.

## Sensitive attributes

- **MD-10** Each domain profile lists its sensitive attributes. A change to one
  takes effect only after a second, independent person has verified it. In SAP,
  configure these as sensitive fields so the account is blocked for payment until
  a second user confirms the change, for example with FK08/FK09 for suppliers and
  FD08/FD09 for customers. [TBC: confirm for your SAP release]
- **MD-11** Before a change to a supplier's bank details is confirmed, the steward
  verifies it with the supplier using contact details already on file, never
  those given in the change request.
- **MD-12** A bank account that already belongs to another supplier or customer
  is flagged for review before the change is confirmed. [TBC: also check against
  employee bank accounts, which needs agreement with HR]

## Data quality

- **MD-13** Each domain profile names its critical attributes: those that, if
  wrong, stop or misdirect a transaction. Critical attributes are checked at
  entry, not only at rest.
- **MD-14** Checks cover five dimensions:
  - **completeness:** required fields are filled;
  - **validity:** values match formats and reference data, such as IBAN check
    digits, VAT numbers and units of measure;
  - **uniqueness:** there are no duplicates;
  - **consistency:** a record matches across the systems that hold it;
  - **timeliness:** records are reviewed when they go unused or out of date.
- **MD-15** The data owner sets a threshold for each check [TBC: by default, 98%
  of records passing for critical attributes]. Results are published monthly on
  each domain's scorecard.
- **MD-16** Issues are fixed in the system of record, never only in a downstream
  copy or report.

## Duplicates

- **MD-17** A duplicate check runs on every create, using the domain's match
  rules. A likely duplicate stops the request until a steward decides.
- **MD-18** When a duplicate is confirmed, one record is kept as the survivor.
  The other is blocked and points to the survivor, once its open transactions
  have been completed or moved.

## Lifecycle

- **MD-19** A record with no activity for [TBC: 24 months] is reviewed. It is
  blocked unless the data owner confirms it is still needed.
- **MD-20** A record that stays blocked with no activity for a further
  [TBC: 12 months] is flagged for archiving. Records are archived and deleted
  only through the archiving process and in line with legal retention
  requirements.

## Domain profiles

These are defaults to confirm with each data owner. [TBC]

### Supplier

| Item | Default |
| --- | --- |
| Data owner | Head of Procurement |
| System of record | SAP: business partner (supplier role) or vendor master. A procurement platform or supplier portal that collects onboarding data raises create requests under MD-03. |
| Critical attributes | Legal name, address, tax ID, bank details, payment terms, payment methods, reconciliation account, purchasing organisation data |
| Mandatory checks | VAT number valid (e.g. EU VIES); IBAN check digits and bank key valid; address validated; payment terms from the approved list |
| Duplicate match rules | Same tax ID; same bank account; similar name in the same country and postcode |
| Sensitive attributes | Bank details, alternative payee, payment terms, payment methods, tax IDs, name and address |
| Inactivity trigger | No purchase orders or invoices for 24 months: purchasing and posting block |

### Customer

| Item | Default |
| --- | --- |
| Data owner | Head of Order-to-Cash or Sales Operations |
| System of record | SAP for legal, financial and logistics attributes; CRM for sales contacts and segmentation |
| Critical attributes | Legal name; addresses for each partner function (sold-to, ship-to, bill-to, payer); tax ID; payment terms; credit limit; sales area data |
| Mandatory checks | Address validated; tax ID valid; each sold-to has a bill-to and a payer; credit limit set where credit management applies; sales area data exists for each sales area used |
| Duplicate match rules | Same tax ID; similar name with the same postcode; two SAP records linked to the same CRM ID |
| Sensitive attributes | Bank details, credit limit and risk category, payment terms, tax IDs |
| Inactivity trigger | No orders or invoices for 24 months: sales and posting block |

### Material / product

| Item | Default |
| --- | --- |
| Data owner | Head of Supply Chain. Attribute group owners: Finance (accounting and costing views), Procurement (purchasing view), Sales (sales views), Engineering (technical attributes) |
| System of record | SAP material master; PLM for engineering attributes; PIM or e-commerce for marketing content |
| Critical attributes | Material type, base unit of measure and conversions, description, material group, valuation class, plant planning (MRP) data, weight and volume, GTIN where used |
| Mandatory checks | Description follows the naming convention [TBC]; a conversion exists for every order and sales unit; valuation class allowed for the material type; GTIN check digit valid; required views exist for every plant where the material is used |
| Duplicate match rules | Same GTIN; same manufacturer and manufacturer part number; similar description in the same material group |
| Sensitive attributes | Standard price, valuation class |
| Inactivity trigger | No stock, movements or open orders for 24 months: blocked material status (cross-plant or plant-specific) |

### Finance

| Item | Default |
| --- | --- |
| Data owner | Financial Controller |
| System of record | SAP: chart of accounts, cost centres, profit centres [TBC: group reporting structure in a consolidation tool] |
| Critical attributes | Account type, account group, reconciliation account setting, tax category, cost centre category, person responsible, hierarchy assignment, validity dates |
| Mandatory checks | Each new GL account maps to the group reporting structure; each cost centre and profit centre has a valid person responsible and hierarchy node; validity dates set |
| Duplicate match rules | Similar description under the same hierarchy node |
| Sensitive attributes | Account type, reconciliation account setting, posting controls |
| Inactivity trigger | No postings for 24 months: posting block |
