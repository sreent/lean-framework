# Material / Product Profile

**Status:** Draft v0.1 · **Approved by:** [TBC: the data owner, with the attribute group owners below for their fields] · **Rules:** [Master data standard](../standards/master-data.md)

This profile sets the parameters the master data standard refers to. The data
owner maintains it and can change it at any time within the standards;
attribute group owners approve changes to their fields. All values are
defaults to confirm. [TBC]

| Item | Default |
| --- | --- |
| Data owner | Head of Supply Chain |
| Attribute group owners (DG-02) | Financial Controller or Head of Costing: accounting and costing views (valuation class, price control, standard price) |
| Functions consulted | Procurement (purchasing view), Sales (sales views), Engineering (technical attributes) |
| Governed workflow (MD-06) | The unified master data app; until it's live, the vendor's request process |
| System of record (MD-01) | SAP material master; PLM for engineering attributes; PIM or e-commerce for marketing content |
| Turnaround times (MD-09) | 2 business days for standard requests; 4 business hours for urgent ones |
| Critical attributes (MD-17) | Material type, base unit of measure and conversions, description, material group, valuation class, plant planning (MRP) data, weight and volume, GTIN where used |
| Mandatory checks | Description follows the naming convention [TBC]; a conversion exists for every order and sales unit; valuation class allowed for the material type; GTIN check digit valid; required views exist for every plant where the material is used |
| Quality thresholds (MD-19) | 98% of records passing for critical attributes |
| Duplicate match rules (MD-22) | Same GTIN; same manufacturer and manufacturer part number; similar description in the same material group |
| Sensitive attributes (MD-12) | Standard price, valuation class, price control |
| One-time accounts and payee in document (MD-16) | Not applicable |
| Inactivity period and block (MD-24) | No stock, movements or open orders for 24 months: blocked material status (cross-plant or plant-specific) |
| Excluded from inactivity blocking | Materials in active bills of materials, and spare parts held for maintenance |
| Request types approved for automatic processing (DG-12) | None yet |
| Agent changes approved at level 2 (DG-14) | None yet |
