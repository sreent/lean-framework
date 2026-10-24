# Material / Product: Starter Settings

**Status:** Starter v0.1 · **Use:** input to a GPDO's [domain profile](../template.md) · **Rules:** [Rulebook](../../rulebook.md)

Starter material, not a decision: common SAP settings for material / product data.
The GPDO who owns this data can use, change or drop any of it when proposing
their domain profile. [TBC]

| Setting | Starter value |
| --- | --- |
| Governed process (R-03) | The current app and the vendor until Q2 2027; then the unified master data app |
| System of record (R-04) | SAP material master; PLM for engineering attributes; PIM or e-commerce for marketing content |
| Turnaround times (R-06) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical fields (R-09) | Material type, base unit of measure and conversions, description, material group, valuation class, plant planning (MRP) data, weight and volume, GTIN where used |
| Conventions (R-09) | Descriptions follow a noun, modifier, attributes pattern [TBC]; units of measure and material groups from the approved lists |
| Mandatory checks (R-05, R-09) | A conversion exists for every order and sales unit; valuation class allowed for the material type; GTIN check digit valid; required views exist for every plant where the material is used |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Same GTIN; same manufacturer and manufacturer part number; similar description in the same material group |
| Inactivity period and block (R-11) | No stock, movements or open orders for 24 months: blocked material status (cross-plant or plant-specific) |
| Excluded from inactivity blocking (R-11) | Materials in active bills of materials, and spare parts held for maintenance |
| Sensitive fields (R-13) | Standard price, valuation class, price control |
| Sensitive changes confirmed by (R-13) | The field's owner or someone in their team, other than the person who entered the change |
| One-time accounts and payee in document (R-13) | Not applicable |
| Confidential and Restricted fields (R-14, R-16, R-21) | Confidential: standard price and valuation data. Restricted: specifications that reveal a product's formulation (trade secrets) [TBC]. |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
