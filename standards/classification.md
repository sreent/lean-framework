# Data Classification Standard

**Status:** Draft v0.2 · **Owner:** [TBC: data governance specialist] · **Approved by:** [TBC: executive sponsor, with information security and the data protection officer] · **Implements:** DG-08

> [TBC] If the organisation already has a classification scheme, use its
> levels and handling rules, and keep only the master data defaults from this
> document.

## Purpose

Classification sets who can see a piece of data and how it is handled.
Applied to each attribute, it lets access, masking and sharing rules be
enforced in SAP, in non-SAP systems and on the data platform.

Classification is about who can see data. Which changes need a second check is
a separate question, answered by the sensitive attributes in each domain
profile (MD-12). Payment terms, for example, are Confidential, but changes to
them are still sensitive.

## Levels

| Level | Meaning | Master data examples |
| --- | --- | --- |
| Public | Approved for release outside the organisation | Published product names and descriptions |
| Internal | Everyday business data; little harm if disclosed | Material numbers, units of measure, plant codes, names and addresses of business suppliers and customers, cost centre structure |
| Confidential | Would cause harm if disclosed; access on business need | Contact names, emails and phone numbers; pricing conditions; payment terms; credit limits; standard costs |
| Restricted | Would cause serious financial, legal or fraud harm if disclosed or changed | Bank details; tax IDs of individuals, such as sole-trader suppliers |

### Personal data

Personal data is anything that identifies a person, such as a customer contact
or a sole-trader supplier. It carries a **personal data** flag in addition to
its level. The flag brings privacy obligations [TBC: GDPR by default]: a lawful
purpose, collecting only what is needed, retention limits (MD-26) and support
for data subject requests.

## Rules

- **CLS-01** Classification is applied to each attribute (field) and recorded
  in [TBC: the data catalogue]. Where SAP holds companies and individuals in
  the same fields, it is applied to the attribute and the record type
  together, using the business partner category (person or organisation) or
  the natural person indicator.
- **CLS-02** Attributes not listed in the default classifications below are
  Internal. An attribute that holds personal data or payment data must be
  listed before it is used.
- **CLS-03** Personal data is at least Confidential. The data owner and the
  data protection officer may agree a lower level for details already
  published internally, such as employee names in the company directory.
- **CLS-04** An agent or the data governance specialist proposes each
  classification; the data owner confirms it.
- **CLS-05** A report or extract takes the highest level of any attribute in
  it, so an extract that includes bank details is Restricted. Inside a system,
  access is controlled per attribute instead.
- **CLS-06** Classification travels with the data. A copy in a non-SAP system,
  on the data platform or in a spreadsheet is handled the same way as the
  original.
- **CLS-07** Restricted and personal data is masked or replaced with synthetic
  data in non-production systems, including SAP system copies used for
  testing.
- **CLS-08** Classifications are reviewed when attributes are added or
  changed, and at least once a year.

## Handling

| | Public | Internal | Confidential | Restricted |
| --- | --- | --- | --- | --- |
| Who can see it | Anyone | Employees and approved contractors | Roles with a business need | Named roles approved by the data owner |
| Access review | – | Yearly | Every six months | Quarterly |
| Non-production systems | As is | As is | Personal data masked | Masked or synthetic |
| Exports and downloads | Allowed | Allowed | Logged | Blocked unless the data owner approves, and logged. Approved interfaces, such as payment files, are exempt. |
| Sharing outside the organisation | Allowed | On business need | With a contract in place and the data owner's approval | Only where legally or contractually required, encrypted |
| Use by AI agents and tools | Allowed | Approved tools | Approved tools, with personal data minimised | Never sent to an AI model outside the organisation unless the data owner and the data protection officer approve |

Documents sent to the other party in the normal course of business, such as
purchase orders, invoices and statements, are exempt from the sharing rules.

How much of this SAP can enforce depends on the tools in place. SAP's download
controls work per user rather than per field, and logging or masking by field
needs tools such as SAP Read Access Logging or UI masking, which may need
separate licences. Where they aren't available, role-based access and
controls on reports and extracts do the job. [TBC]

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

## Change history

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 2026-10-23 | First draft |
| 0.2 | 2026-10-23 | Classified by record type where SAP mixes companies and individuals; unlisted attributes default to Internal; highest-level rule limited to reports and extracts; exemptions for payment files and business documents; dual control moved out to the master data standard |
