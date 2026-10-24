# Production Data: Starter Settings

**Status:** Starter v0.1 · **Use:** input to a GPDO's [domain profile](../template.md) · **Rules:** [Rulebook](../../rulebook.md)

Starter material, not a decision: common SAP settings for production data data.
The GPDO who owns this data can use, change or drop any of it when proposing
their domain profile. [TBC]

| Setting | Starter value |
| --- | --- |
| Governed process (R-03) | The current engineering change process until Q2 2027 [TBC: or the current app]; then the unified master data app, if it covers production data [TBC] |
| System of record (R-04) | SAP bills of materials, routings or master recipes, work centres and production versions [TBC: PLM for engineering bills of materials] |
| Turnaround times (R-06) | [TBC] |
| Critical fields (R-09) | Bill of materials components, quantities, usage and validity; routing operations, work centres and standard values; production version validity and lot sizes; work centre capacity and cost centre |
| Conventions (R-09) | Changes to bills of materials and routings made with a change number [TBC] |
| Mandatory checks (R-05, R-09) | Every component exists and isn't blocked; quantities use units of measure the material supports; each production version points to a valid bill of materials and routing; each work centre has a cost centre and activity types |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Two bills of materials or routings for the same material, plant and usage with overlapping validity |
| Inactivity period and block (R-11) | Bills of materials and routings for materials that are blocked or unused for 24 months |
| Excluded from inactivity blocking (R-11) | Bills of materials for spare parts held for maintenance [TBC] |
| Sensitive fields (R-13) | Formula and recipe components, quantities and process parameters |
| Sensitive changes confirmed by (R-13) | The field's owner or someone in their team, such as R&D or quality, other than the person who entered the change |
| One-time accounts and payee in document (R-13) | Not applicable |
| Personal data fields (R-16) | None |
| Payment data fields (R-16) | None |
| Trade secret fields (R-16, R-21) | Formula and recipe components, quantities and process parameters in master recipes and bills of materials |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
