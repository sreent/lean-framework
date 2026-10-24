# Supplier: Starter Settings

**Status:** Starter v0.1 · **Use:** input to a GPDO's [domain profile](../template.md) · **Rules:** [Rulebook](../../rulebook.md)

Starter material, not a decision: common SAP settings for supplier data.
The GPDO who owns this data can use, change or drop any of it when proposing
their domain profile. [TBC]

| Setting | Starter value |
| --- | --- |
| Governed process (R-03) | The unified master data app (until then, see the interim arrangements) |
| Request types (R-03) | Create; extend to a company code or purchasing organisation; change general, company code or purchasing data; change bank details; block or unblock |
| System of record (R-04) | SAP: business partner (supplier role) or vendor master. Onboarding data from a procurement platform or supplier portal arrives as create requests. In S/4HANA, central data is shared with the customer role (R-02), so its owner and its sensitive fields are a joint decision for the Commercial and Procurement GPDOs. |
| Turnaround times (R-06) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical fields (R-09) | Legal name, address, tax ID, bank details, payment terms, payment methods, reconciliation account, purchasing organisation data |
| Conventions (R-09) | Legal name as registered [TBC: casing]; addresses in the country's postal format; search term built from the name [TBC]; payment terms from the approved list |
| Mandatory checks (R-05, R-09) | VAT number valid (e.g. EU VIES); IBAN check digits and bank key valid; address validated; screened against sanctions lists; intercompany suppliers carry the trading partner |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Same tax ID; same bank account; similar name in the same country and postcode |
| Inactivity period and block (R-11) | No purchase orders or invoices for 24 months: purchasing and posting block |
| Excluded from inactivity blocking (R-11) | Suppliers with open items, open purchase orders or contracts |
| Sensitive fields (R-13) | Bank details, alternative payee, payment terms, payment methods, tax IDs, name and address, and the phone numbers and email addresses used to verify changes (R-15) |
| Sensitive changes confirmed by (R-13, R-14) | The steward, who holds no rights to create purchase orders, post invoices or run payments (R-14) |
| One-time accounts and payee in document (R-13) | Allowed only for [TBC: named cases, below a set amount] |
| Confidential and Restricted fields (R-14, R-16, R-21) | Confidential: contact names, emails and phone numbers, and names and addresses of sole traders (personal data); payment terms and methods (payment data). Restricted: bank details and alternative payee (payment data); tax IDs of sole traders (personal data). |
| Request types approved automatically (R-06) | Changes that touch no sensitive field, pass every check and raise no likely duplicate. New records and sensitive changes go to the steward. |
| Agent changes approved at level 2 (R-18) | None yet |
