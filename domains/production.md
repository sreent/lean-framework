# Production Data Profile

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
| Governed process (R-03) | The unified master data app, if it covers production data [TBC]; until then, the current engineering change process |
| System of record (R-04) | SAP bills of materials, routings or master recipes, work centres and production versions [TBC: PLM for engineering bills of materials] |
| Turnaround times (R-06) | [TBC] |
| Critical fields (R-09) | Bill of materials components, quantities, usage and validity; routing operations, work centres and standard values; production version validity and lot sizes; work centre capacity and cost centre |
| Conventions (R-09) | Changes to bills of materials and routings made with a change number [TBC] |
| Mandatory checks (R-05, R-09) | Every component exists and isn't blocked; quantities use units of measure the material supports; each production version points to a valid bill of materials and routing; each work centre has a cost centre and activity types |
| Quality thresholds (R-09) | 98% of records passing for critical fields |
| Duplicate match rules (R-05) | Two bills of materials or routings for the same material, plant and usage with overlapping validity |
| Inactivity period and block (R-11) | Bills of materials and routings for materials that are blocked or unused for 24 months |
| Excluded from inactivity blocking (R-11) | Bills of materials for spare parts held for maintenance [TBC] |
| Sensitive fields (R-13) | None by default [TBC] |
| Sensitive changes confirmed by (R-13) | Not applicable unless sensitive fields are added |
| One-time accounts and payee in document (R-13) | Not applicable |
| Personal data fields (R-16) | None |
| Payment data fields (R-16) | None |
| Request types approved automatically (R-06) | None yet |
| Agent changes approved at level 2 (R-18) | None yet |
