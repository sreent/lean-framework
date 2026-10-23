# Finance Profile

**Status:** Draft v0.1 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Master data standard](../standards/master-data.md)

This profile sets the parameters the master data standard refers to. The data
owner maintains it and can change it at any time within the standards;
attribute group owners approve changes to their fields. All values are
defaults to confirm. [TBC]

| Item | Default |
| --- | --- |
| Data owner | Financial Controller |
| Attribute group owners (DG-02) | Head of Tax: tax category |
| Functions consulted | Business controllers (cost centres and profit centres in their area) |
| Governed workflow (MD-06) | The unified master data app; until it's live, the vendor's request process |
| System of record (MD-01) | SAP: chart of accounts, cost centres, profit centres, and cost elements on ECC [TBC: group reporting structure in a consolidation tool] |
| Turnaround times (MD-09) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical attributes (MD-17) | Account type, account group, reconciliation account setting, tax category, cost centre category, person responsible, hierarchy assignment, validity dates |
| Mandatory checks | Each new GL account maps to the group reporting structure; each cost centre and profit centre has a valid person responsible and hierarchy node; validity dates set |
| Quality thresholds (MD-19) | 98% of records passing for critical attributes |
| Duplicate match rules (MD-22) | Similar description under the same hierarchy node |
| Sensitive attributes (MD-12) | Account type, reconciliation account setting, posting controls |
| One-time accounts and payee in document (MD-16) | Not applicable |
| Inactivity period and block (MD-24) | No postings for 24 months: posting block |
| Excluded from inactivity blocking | Accounts used only at year-end or for rare events, such as impairments |
| Request types approved for automatic processing (DG-12) | None yet |
| Agent changes approved at level 2 (DG-14) | None yet |
