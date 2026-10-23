# Supplier Profile

**Status:** Draft v0.1 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Master data standard](../standards/master-data.md)

This profile sets the parameters the master data standard refers to. The data
owner maintains it and can change it at any time within the standards;
attribute group owners approve changes to their fields. All values are
defaults to confirm. [TBC]

| Item | Default |
| --- | --- |
| Data owner | Head of Procurement |
| Attribute group owners (DG-02) | Head of Accounts Payable or Financial Controller: bank details, payment terms and methods, reconciliation account, withholding tax |
| Functions consulted | None by default |
| Governed workflow (MD-06) | The unified master data app; until it's live, the vendor's request process |
| System of record (MD-01) | SAP: business partner (supplier role) or vendor master. Onboarding data from a procurement platform or supplier portal arrives as create requests (MD-03). In S/4HANA, central data is shared with the customer role (MD-05). |
| Turnaround times (MD-09) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical attributes (MD-17) | Legal name, address, tax ID, bank details, payment terms, payment methods, reconciliation account, purchasing organisation data |
| Mandatory checks | VAT number valid (e.g. EU VIES); IBAN check digits and bank key valid; address validated; payment terms from the approved list; screened against sanctions lists; intercompany suppliers carry the trading partner |
| Quality thresholds (MD-19) | 98% of records passing for critical attributes |
| Duplicate match rules (MD-22) | Same tax ID; same bank account; similar name in the same country and postcode |
| Sensitive attributes (MD-12) | Bank details, alternative payee, payment terms, payment methods, tax IDs, name and address, and the phone numbers and email addresses used to verify changes (MD-14) |
| One-time accounts and payee in document (MD-16) | Allowed only for [TBC: named cases, below a set amount] |
| Inactivity period and block (MD-24) | No purchase orders or invoices for 24 months: purchasing and posting block |
| Excluded from inactivity blocking | Suppliers with open items, open purchase orders or contracts |
| Request types approved for automatic processing (DG-12) | None yet |
| Agent changes approved at level 2 (DG-14) | None yet |
