# Material / Product Profile

**Status:** Draft v0.2 · **Approved by:** [TBC: the GPDO, with the attribute owners below for their fields] · **Rules:** [Rulebook](../rulebook.md)

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
| Governed process (R-03) | The unified master data app; until it's live, the vendor's request process |
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
| Personal data fields (R-16) | None |
| Payment data fields (R-16) | None |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
