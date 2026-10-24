# Customer: Starter Settings

**Status:** Starter v0.1 · **Use:** input to a GPDO's [domain profile](../template.md) · **Rules:** [Rulebook](../../rulebook.md)

Starter material, not a decision: common SAP settings for customer data.
The GPDO who owns this data can use, change or drop any of it when proposing
their domain profile. [TBC]

| Setting | Starter value |
| --- | --- |
| Governed process (R-03) | The unified master data app (until then, see the interim arrangements) |
| Request types (R-03) | Create; extend to a company code or sales area; change general, company code or sales data; change bank details or credit limit; block or unblock |
| System of record (R-04) | SAP for legal, financial and logistics fields; CRM for sales contacts and segmentation. In S/4HANA, central data is shared with the supplier role (R-02), so its owner and its sensitive fields are a joint decision for the Commercial and Procurement GPDOs. |
| Turnaround times (R-06) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical fields (R-09) | Legal name; addresses for each partner function (sold-to, ship-to, bill-to, payer); tax ID; payment terms; credit limit; sales area data |
| Conventions (R-09) | Legal name as registered; addresses in the country's postal format; partner functions set up the same way for each account group [TBC] |
| Mandatory checks (R-05, R-09) | Address validated; tax ID valid; screened against sanctions lists; each sold-to has a bill-to and a payer; credit limit set where credit management applies; sales area data exists for each sales area used; intercompany customers carry the trading partner |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Same tax ID; similar name with the same postcode; two SAP records with the same partner function linked to the same CRM ID |
| Inactivity period and block (R-11) | No orders or invoices for 24 months: sales and posting block |
| Excluded from inactivity blocking (R-11) | Customers with open items or open orders |
| Sensitive fields (R-13) | Bank details, credit limit and risk category, payment terms, tax IDs |
| Sensitive changes confirmed by (R-13, R-14) | The steward, who holds no credit release or payment rights (R-14). Credit limits are confirmed by [TBC: credit management], never by sales. |
| One-time accounts and payee in document (R-13) | Allowed only for [TBC: named cases, below a set amount] |
| Confidential and Restricted fields (R-14, R-16, R-21) | Confidential: contact names, emails and phone numbers, and names and addresses of consumers (personal data); credit limit and payment terms (payment data). Restricted: bank details (payment data). |
| Request types approved automatically (R-06) | Changes that touch no sensitive field, pass every check and raise no likely duplicate. New records and sensitive changes go to the steward. |
| Agent changes approved at level 2 (R-18) | None yet |
