# Supplier Profile

**Status:** Draft v0.2 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Rulebook](../rulebook.md)

This profile holds the domain's validation and quality rules, and the other
settings the rulebook refers to. The business owns them: the data owner
approves the profile and can change it at any time, within the rulebook, and
attribute group owners approve changes to their fields. The data team turns
them into checks and can propose new ones. All values are defaults to confirm.
[TBC]

| Setting | Default |
| --- | --- |
| Data owner (R-01) | Head of Procurement |
| Attribute group owners (R-02) | Finance (accounts payable): reconciliation account and withholding tax [TBC]. The data owner keeps bank details and payment terms. |
| Functions consulted | None by default |
| Governed process (R-03) | The unified master data app; until it's live, the vendor's request process |
| System of record (R-04) | SAP: business partner (supplier role) or vendor master. Onboarding data from a procurement platform or supplier portal arrives as create requests. In S/4HANA, central data is shared with the customer role (R-02). |
| Turnaround times (R-06) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical fields (R-09) | Legal name, address, tax ID, bank details, payment terms, payment methods, reconciliation account, purchasing organisation data |
| Conventions (R-09) | Legal name as registered [TBC: casing]; addresses in the country's postal format; search term built from the name [TBC]; payment terms from the approved list |
| Mandatory checks (R-05, R-09) | VAT number valid (e.g. EU VIES); IBAN check digits and bank key valid; address validated; screened against sanctions lists; intercompany suppliers carry the trading partner |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Same tax ID; same bank account; similar name in the same country and postcode |
| Inactivity period and block (R-11) | No purchase orders or invoices for 24 months: purchasing and posting block |
| Excluded from inactivity blocking (R-11) | Suppliers with open items, open purchase orders or contracts |
| Sensitive fields (R-13) | Bank details, alternative payee, payment terms, payment methods, tax IDs, name and address, and the phone numbers and email addresses used to verify changes (R-15) |
| Sensitive changes confirmed by (R-13, R-14) | Someone in the data owner's team, such as supplier management, without rights to create purchase orders, post invoices or run payments |
| One-time accounts and payee in document (R-13) | Allowed only for [TBC: named cases, below a set amount] |
| Personal data fields (R-16) | Contact names, emails and phone numbers; names, addresses and tax IDs of sole traders |
| Payment data fields (R-16) | Bank details, alternative payee, payment terms and methods |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
