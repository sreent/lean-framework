# Customer Profile

**Status:** Draft v0.1 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Master data standard](../standards/master-data.md)

This profile sets the parameters the master data standard refers to. The data
owner maintains it and can change it at any time within the standards;
attribute group owners approve changes to their fields. All values are
defaults to confirm. [TBC]

| Item | Default |
| --- | --- |
| Data owner | Head of Order-to-Cash or Sales Operations |
| Attribute group owners (DG-02) | Credit Manager: credit limit and risk category, payment terms, bank details, reconciliation account |
| Functions consulted | Logistics (shipping data) |
| Governed workflow (MD-06) | The unified master data app; until it's live, the vendor's request process |
| System of record (MD-01) | SAP for legal, financial and logistics attributes; CRM for sales contacts and segmentation. In S/4HANA, central data is shared with the supplier role (MD-05). |
| Turnaround times (MD-09) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical attributes (MD-17) | Legal name; addresses for each partner function (sold-to, ship-to, bill-to, payer); tax ID; payment terms; credit limit; sales area data |
| Mandatory checks | Address validated; tax ID valid; screened against sanctions lists; each sold-to has a bill-to and a payer; credit limit set where credit management applies; sales area data exists for each sales area used; intercompany customers carry the trading partner |
| Quality thresholds (MD-19) | 98% of records passing for critical attributes |
| Duplicate match rules (MD-22) | Same tax ID; similar name with the same postcode; two SAP records with the same partner function linked to the same CRM ID |
| Sensitive attributes (MD-12) | Bank details, credit limit and risk category, payment terms, tax IDs |
| One-time accounts and payee in document (MD-16) | Allowed only for [TBC: named cases, below a set amount] |
| Inactivity period and block (MD-24) | No orders or invoices for 24 months: sales and posting block |
| Excluded from inactivity blocking | Customers with open items or open orders |
| Request types approved for automatic processing (DG-12) | None yet |
| Agent changes approved at level 2 (DG-14) | None yet |
