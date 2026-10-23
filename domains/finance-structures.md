# Finance Structures Profile

**Status:** Draft v0.2 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Rulebook](../rulebook.md)

This profile holds the domain's validation and quality rules, and the other
settings the rulebook refers to. The business owns them: the data owner
approves the profile and can change it at any time, within the rulebook, and
attribute group owners approve changes to their fields. The data team turns
them into checks and can propose new ones. All values are defaults to confirm.
[TBC]

| Setting | Default |
| --- | --- |
| Data owner (R-01) | Financial Controller |
| Attribute group owners (R-02) | Head of Tax: tax category |
| Functions consulted | Business controllers (cost centres and profit centres in their area) |
| Governed process (R-03) | The unified master data app; until it's live, the vendor's request process |
| System of record (R-04) | SAP: chart of accounts, cost centres, profit centres, and cost elements on ECC [TBC: group reporting structure in a consolidation tool] |
| Turnaround times (R-06) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical fields (R-09) | Account type, account group, reconciliation account setting, tax category, cost centre category, person responsible, hierarchy assignment, validity dates |
| Conventions (R-09) | Names follow the chart of accounts and cost centre naming conventions [TBC] |
| Mandatory checks (R-05, R-09) | Each new GL account maps to the group reporting structure; each cost centre and profit centre has a valid person responsible and hierarchy node; validity dates set |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Similar description under the same hierarchy node |
| Inactivity period and block (R-11) | No postings for 24 months: posting block |
| Excluded from inactivity blocking (R-11) | Accounts used only at year-end or for rare events, such as impairments |
| Sensitive fields (R-13) | Account type, reconciliation account setting, posting controls |
| Sensitive changes confirmed by (R-13) | Someone in the Financial Controller's team, or the Head of Tax's team for tax category, other than the person who entered the change |
| One-time accounts and payee in document (R-13) | Not applicable |
| Personal data fields (R-16) | Person responsible for a cost centre or profit centre |
| Payment data fields (R-16) | None |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
