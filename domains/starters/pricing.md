# Pricing: Starter Settings

**Status:** Starter v0.1 · **Use:** input to a GPDO's [domain profile](../template.md) · **Rules:** [Rulebook](../../rulebook.md)

Starter material, not a decision: common SAP settings for pricing data.
Its owners can use, change or drop any of it in their domain profile. [TBC]

| Setting | Starter value |
| --- | --- |
| Governed process (R-03) | The pricing request process [TBC: its name, or the current app]. The unified app may cover pricing later [TBC]. |
| Request types (R-03) | Create or change condition records; mass price updates (R-07) |
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
| Sensitive changes confirmed by (R-13) | The attribute owner or their delegates |
| One-time accounts and payee in document (R-13) | Not applicable |
| Confidential and Restricted fields (R-14, R-16, R-21) | Confidential: prices, discounts, surcharges and margins. Restricted: none by default [TBC]. |
| Request types approved automatically (R-06) | Not applicable while pricing follows its own process; then, changes that touch no sensitive field and pass every check |
| Agent changes approved at level 2 (R-18) | None yet |
