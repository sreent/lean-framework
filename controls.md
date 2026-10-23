# Controls Catalogue

**Status:** Draft v0.1 · **Approved by:** [TBC: Head of Data, AI & Development] · **Rules:** [Rulebook](rulebook.md)

How each rule is enforced: today, with the vendor working in SAP, and once the
unified master data app is live. The target column doubles as the app's
backlog. Controls change here as the app grows; the rules don't.

| Rule | Today (vendor and SAP) | Target (app and agents) | Evidence |
| --- | --- | --- | --- |
| R-01 Named owner | Owners sign the charter and their domain profiles | Same | Signed charter and profiles |
| R-02 Delegation | Delegations recorded in the domain profiles | Same | Signed profiles |
| R-03 Governed process | Requests go through the vendor's ticketing process [TBC]; requests by email or spreadsheet are turned away | All requests go through the app. Non-SAP systems raise requests through its request interface. [TBC: on the app roadmap] | Request log |
| R-04 One system of record | Data flows from SAP over interfaces; non-SAP copies hold the SAP key [TBC] | Interface or middleware checks reject or quarantine bad records. The data platform compares each non-SAP copy with SAP, and an agent triages the differences. | Consistency scorecard |
| R-05 Checks before approval | Vendor checklist and SAP mandatory fields; manual duplicate search | App validations at entry, such as VIES, IBAN and GTIN checks and the domain's conventions. An agent pre-checks each request and runs fuzzy duplicate matching. | Check results stored with each request |
| R-06 Approval | Vendor maker-checker; turnaround in the vendor's reports | The app routes each request to a steward, or approves owner-approved request types automatically. A sample of automatic approvals is reviewed monthly. | Approval log, sample results |
| R-07 Mass changes | The data owner signs off by email [TBC]; tested in a non-production system first | Mass-change function in the app, with the sign-off built in | Sign-off and test evidence |
| R-08 Traceability | Only the vendor's stewards hold SAP change rights. Each month, SAP change documents are matched to tickets. | Only the app's service identity holds change rights. An agent matches change documents to requests daily. [TBC] | Reconciliation report |
| R-09 Conventions and quality checks | The data team runs the checks each domain profile defines on SAP extracts monthly and publishes scorecards | Checks run in the app at entry and on the data platform at rest; scorecards update daily [TBC] | Scorecards |
| R-10 Fix at source, fix the cause | A steward fixes the record in SAP; the data team logs the cause and proposes new checks to the data owner | Each issue becomes a fix request in the app. An agent groups recurring issues and proposes new checks for the data owner to approve. | Issue log; checks added to the profile |
| R-11 Stale records | The data team lists inactive records quarterly [TBC]; the owner approves the list | An agent prepares the list monthly; the owner approves it in the app | Approved list |
| R-12 Vendor | Vendor contract and [requirements](vendor-requirements.md); monthly performance review | Same, with the vendor's volumes falling as the app takes over | Performance report |
| R-13 Sensitive changes | SAP sensitive-field settings block payment until the confirmer named in the domain profile confirms the change, for example with FK08/FK09 for suppliers and FD08/FD09 for customers [TBC: confirm for your release]. Other sensitive changes, including credit limits and unblocking, are confirmed before the vendor enters them. SAP settings limit one-time accounts and payee in document. [TBC] | The app holds each sensitive change until it's confirmed, then posts it to SAP. SAP's settings stay as a second line. | Confirmation log |
| R-14 Payment data kept apart from paying | SAP roles of vendor staff and confirmers reviewed for conflicting rights [TBC: rule set] | Same, and the app stops the person who entered a change from confirming it | Access review |
| R-15 Bank detail verification | The confirmer calls the supplier back on details already on file and keeps the evidence; a report flags shared bank accounts | The app requires call-back evidence before confirmation. An agent checks for shared accounts, comparing masked values. | Call-back evidence, flag report |
| R-16 Access and masking | SAP roles reviewed for access to flagged fields; extracts of Restricted data need owner approval; data masked when SAP is copied to test systems [TBC: tool] | Same | Access review, approvals, masking log |
| R-17 Personal data lifecycle | [TBC: SAP Information Lifecycle Management end-of-purpose checks] | Same | Blocking and deletion log |
| R-18 Agents | Agent register kept by the data governance specialist; design review before go-live; logs kept as long as SAP change documents | An agent moves up a level on accuracy checked against an independent sample, and drops a level after a serious error. Changes to its model, instructions or tools are tested and re-approved. | Register, logs, sample results |
| R-19 Data team | Emergency access is logged and reviewed by [TBC: the internal controls team]; app and agent changes go through change management | Same | Review log, release records |
| R-20 Exceptions | Exception register [TBC: location] | Register in the app; an agent chases expiry dates | Register |
