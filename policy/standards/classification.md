# Data Classification Standard

**Status:** Draft v0.1 · **Owner:** [TBC: governance lead, with information security and the data protection officer] · **Implements:** P-07

## Purpose

Classification tells every control and every person how to handle a piece of
data. Applied to each attribute, it lets access, masking and sharing rules be
enforced automatically in SAP, in non-SAP systems and on the data platform.

## Levels

| Level | Meaning | Master data examples |
| --- | --- | --- |
| Public | Approved for release outside the organisation | Published product names and descriptions |
| Internal | Everyday business data; little harm if disclosed | Material numbers, units of measure, plant codes, names and addresses of business suppliers and customers, cost centre structure |
| Confidential | Would cause harm if disclosed; access on business need | Contact names, emails and phone numbers; pricing conditions; payment terms; credit limits; standard costs |
| Restricted | Would cause serious financial, legal or fraud harm if disclosed or changed | Bank details; tax IDs of individuals, such as sole-trader suppliers |

### Personal data

Personal data is anything that identifies a person, such as a customer contact or
a sole-trader supplier. It carries a **personal data** flag in addition to its
level. The flag brings privacy obligations [TBC: GDPR by default]: a lawful
purpose, collecting only what is needed, retention limits and support for data
subject requests.

## Rules

- **CLS-01** Classification is applied to each attribute (field) and recorded in
  [TBC: the data catalogue], not to whole tables or systems.
- **CLS-02** An attribute that hasn't been classified is treated as Confidential
  until it is.
- **CLS-03** Personal data is at least Confidential. The data owner and the data
  protection officer may agree a lower level for details already published
  internally, such as employee names in the company directory.
- **CLS-04** An agent or a steward proposes the classification; the data owner
  confirms it.
- **CLS-05** A record, report or extract takes the highest level of any attribute
  in it. An extract that includes bank details is Restricted.
- **CLS-06** Classification travels with the data. A copy in a non-SAP system, on
  the data platform or in a spreadsheet is handled the same way as the original.
- **CLS-07** Restricted and personal data is masked or replaced with synthetic
  data in non-production systems, including SAP system copies used for testing.
- **CLS-08** Classifications are reviewed when attributes are added or changed,
  and at least once a year.

## Handling

| | Public | Internal | Confidential | Restricted |
| --- | --- | --- | --- | --- |
| Who can see it | Anyone | Employees and approved contractors | Roles with a business need | Named roles approved by the data owner |
| Access review | – | Yearly | Every six months | Quarterly |
| Changes | Governed process (P-02) | Governed process | Governed process | Governed process plus dual control (P-06) |
| Non-production systems | As is | As is | Personal data masked | Masked or synthetic |
| Exports and downloads | Allowed | Allowed | Logged | Blocked unless the data owner approves; logged |
| Sharing outside the organisation | Allowed | On business need | With a contract in place and the data owner's approval | Only where legally or contractually required, encrypted |
| Use by AI agents and tools | Allowed | Approved tools | Approved tools, with personal data minimised | Not allowed unless the data owner and data protection officer approve |

## Default classifications for common master data attributes

[TBC: confirm with each data owner.] (PD) marks personal data.

| Domain | Attribute | Level |
| --- | --- | --- |
| Supplier | Name and address of a company | Internal |
| Supplier | Name and address of an individual or sole trader | Confidential (PD) |
| Supplier | Contact person's name, email and phone | Confidential (PD) |
| Supplier | Company VAT number or tax ID | Internal |
| Supplier | Tax ID of an individual | Restricted (PD) |
| Supplier | Bank details | Restricted |
| Supplier | Payment terms and payment methods | Confidential |
| Customer | Name and address of a business | Internal |
| Customer | Name and address of a consumer or individual | Confidential (PD) |
| Customer | Contact person's name, email and phone | Confidential (PD) |
| Customer | Credit limit and risk category | Confidential |
| Customer | Pricing conditions | Confidential |
| Customer | Bank details, e.g. for direct debit | Restricted |
| Material | Number, description, type, group, units of measure | Internal |
| Material | Standard price and valuation data | Confidential |
| Material | Published product content | Public |
| Finance | GL accounts, cost centres, profit centres and their hierarchies | Internal |
| Finance | Person responsible for a cost centre or profit centre | Internal (PD), by agreement under CLS-03 |
