# Customer Profile

**Status:** Draft v0.2 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Rulebook](../rulebook.md)

This profile holds the domain's validation and quality rules, and the other
settings the rulebook refers to. The business owns them: the data owner
approves the profile and can change it at any time, within the rulebook, and
attribute group owners approve changes to their fields. The data team turns
them into checks and can propose new ones. All values are defaults to confirm.
[TBC]

| Setting | Default |
| --- | --- |
| Data owner (R-01) | Head of Commercial |
| Attribute group owners (R-02) | Finance: credit limit and risk category [TBC: if credit management sits in Finance; otherwise the data owner keeps them], and reconciliation account |
| Functions consulted | Manufacturing (delivering plants and shipping data) [TBC] |
| Governed process (R-03) | The unified master data app; until it's live, the vendor's request process |
| System of record (R-04) | SAP for legal, financial and logistics fields; CRM for sales contacts and segmentation. In S/4HANA, central data is shared with the supplier role (R-02). |
| Turnaround times (R-06) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical fields (R-09) | Legal name; addresses for each partner function (sold-to, ship-to, bill-to, payer); tax ID; payment terms; credit limit; sales area data |
| Conventions (R-09) | Legal name as registered; addresses in the country's postal format; partner functions set up the same way for each account group [TBC] |
| Mandatory checks (R-05, R-09) | Address validated; tax ID valid; screened against sanctions lists; each sold-to has a bill-to and a payer; credit limit set where credit management applies; sales area data exists for each sales area used; intercompany customers carry the trading partner |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Same tax ID; similar name with the same postcode; two SAP records with the same partner function linked to the same CRM ID |
| Inactivity period and block (R-11) | No orders or invoices for 24 months: sales and posting block |
| Excluded from inactivity blocking (R-11) | Customers with open items or open orders |
| Sensitive fields (R-13) | Bank details, credit limit and risk category, payment terms, tax IDs |
| Sensitive changes confirmed by (R-13, R-14) | Credit limit and risk category: someone in credit management, not sales. Other sensitive fields: someone in the data owner's team. Neither holds credit release or payment rights. |
| One-time accounts and payee in document (R-13) | Allowed only for [TBC: named cases, below a set amount] |
| Personal data fields (R-16) | Contact names, emails and phone numbers; names and addresses of consumers |
| Payment data fields (R-16) | Bank details, payment terms, credit limit |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
