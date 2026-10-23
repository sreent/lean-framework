# Pricing Profile

**Status:** Draft v0.1 · **Phase:** [TBC: phase 1, or added after the first measurements] · **Approved by:** [TBC: the GPDO, with the attribute owners below for their fields] · **Rules:** [Rulebook](../rulebook.md)

This profile holds the domain's validation and quality rules, and the other
settings the rulebook refers to. The business owns them: the GPDO, as data owner,
approves the profile and can change it at any time, within the rulebook, and
attribute owners approve changes to their fields. The data team turns
them into checks and can propose new ones. All values are defaults to confirm.
[TBC]

| Setting | Default |
| --- | --- |
| Data owner (R-01) | [TBC: agreed by the GPDOs] |
| Attribute owners, delegated by the GPDO (R-02) | [TBC: delegated by the data owner] |
| Governed process (R-03) | The unified master data app, if it covers pricing [TBC]; until then, the current pricing request process |
| System of record (R-04) | SAP condition records for prices, discounts and surcharges [TBC: any pricing or quoting tool outside SAP] |
| Turnaround times (R-06) | [TBC] |
| Critical fields (R-09) | Condition type, price, currency, unit of measure, validity dates, customer or price list, material, sales area, scales |
| Conventions (R-09) | Prices in the sales unit of measure; validity periods without gaps or overlaps for the same key [TBC] |
| Mandatory checks (R-05, R-09) | Price within [TBC]% of the previous price or the list price; no overlapping validity for the same key; currency matches the sales area; material and customer exist and aren't blocked |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Same condition type and key with overlapping validity |
| Inactivity period and block (R-11) | Not applicable: condition records end on their validity date |
| Excluded from inactivity blocking (R-11) | Not applicable |
| Sensitive fields (R-13) | Prices and discounts that change by more than [TBC]% |
| Sensitive changes confirmed by (R-13) | The field's owner or someone in their team, other than the person who entered the change |
| One-time accounts and payee in document (R-13) | Not applicable |
| Personal data fields (R-16) | None |
| Payment data fields (R-16) | None |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
