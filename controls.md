# Controls Catalogue

**Status:** Draft v0.2 · **Approved by:** the Head of Data, AI & Development · **Rules:** [Rulebook](rulebook.md)

How each rule is enforced in the target setup, and the evidence each control
logs. Until a request type moves to the unified master data app, the
[interim arrangements](interim.md) say how its rules are enforced. Controls
change here as the app grows; the rules don't.

Every setting in the unified app changes only with its owner's approval, which
the app logs, and each domain profile keeps its version history. Evidence is
kept for [TBC: the company's retention period].

| Rule | How it's enforced | Evidence |
| --- | --- | --- |
| R-01 Named owner | The GPDOs sign the charter, and the owner of each part of each domain is recorded in the unified app | Signed charter, ownership settings |
| R-02 Delegation | Each field's owner is a setting in the unified app, and the governance coordinator flags any field with no owner or more than one | Ownership settings, gap report |
| R-03 Governed process | All requests go through the unified app. Non-SAP systems raise requests through its request interface [TBC: on the app roadmap]. | Request log |
| R-04 One system of record | Data flows from SAP over interfaces, which reject or quarantine bad records, and non-SAP copies hold the SAP key [TBC]. As each non-SAP system comes in, the data platform compares its copies with SAP and the quality agent sorts the differences. | Consistency scorecard |
| R-05 Checks before approval | The unified app's checks at entry: the domain's conventions and duplicate match rules, and checks such as VIES, IBAN and GTIN. Likely duplicates go to the data owner or their delegate. Once it starts, the request assistant also flags values that pass the checks but look wrong. | Check results stored with each request |
| R-06 Approval | The unified app approves owner-approved request types automatically, routes the rest to the data owner or their delegates, and stops anyone approving their own request. Each month, the owner or a delegate reviews a random sample of [TBC: 25] automatic approvals and records the result. | Approval log, sample results |
| R-07 Mass changes | The unified app's mass-change function, with the owner's sign-off, the test and the rollback plan built in | Sign-off and test evidence |
| R-08 Traceability | Only the unified app's service identity holds change rights in SAP, and the app records the request behind every change. A daily report on the data platform finds any change without one, for internal controls to review. | Reconciliation report |
| R-09 Conventions and quality checks | Checks run in the unified app at entry and on the data platform on stored data; scorecards update daily [TBC] | Scorecards |
| R-10 Fix at source, fix the cause | The quality agent groups failing records by cause, raises fix requests in the unified app and proposes new checks, which the owner adds to the profile | Issue log; checks added to the profile |
| R-11 Stale records | A monthly report lists the records unused for the profile's period, the quality agent asks their last users whether they're still needed, the data owner approves the list, and the app blocks the records | Approved list |
| R-12 Third parties | Any third party that maintains master data works under a contract that holds it to these rules, with a monthly performance review by the data governance specialist | Contract, performance reports |
| R-13 Sensitive changes | The app holds each sensitive change until its data owner or their delegate confirms it, never letting anyone confirm a change they requested or entered, then posts it to SAP. SAP settings limit one-time accounts and payee in document. [TBC: whether the app's confirmation replaces SAP's own (FK08/FD08), or SAP's stays on and needs a second confirmation] | Confirmation log |
| R-14 Payment data kept apart from paying | The platform team reviews the SAP roles of confirmers and of the unified app's service identity each quarter for conflicting rights [TBC: rule set] | Access review |
| R-15 Bank detail verification | The owner or their delegate calls the supplier back on details already on file, or for a new supplier on details from an independent source, and records who called, when, the number used and who confirmed. The app won't take the confirmation without that record, and checks each new bank account against every other supplier and customer. | Call-back evidence, flag report |
| R-16 Classified fields and access | Classified fields are settings in the profile. The unified app limits who can see them to the roles the owner approves, and the owner reviews who has access in SAP and other systems [TBC]. Extracts of Restricted data need the owner's approval, and data is masked when SAP is copied to test systems [TBC: tool]. | Settings, access reviews, approvals, masking log |
| R-17 Personal data lifecycle | [TBC: SAP Information Lifecycle Management end-of-purpose checks] | Blocking and deletion log |
| R-18 Agents | [Agent register](operating-model.md#agents) kept by the data governance specialist; design review before go-live; logs kept as long as SAP change documents. An agent moves up a level, with the data owner's approval, on accuracy checked against an independent sample, and drops a level after a serious error. Changes to its model, instructions or tools are tested and re-approved. | Register, logs, sample results |
| R-19 Data team | Emergency access is logged and reviewed by internal controls; app and agent changes go through change management | Review log, release records |
| R-20 Exceptions | Exceptions are recorded in the unified app, which reminds owners before they expire, and the governance coordinator chases renewals and closures | Register |
| R-21 Trade secrets | Trade secrets are marked in the profiles. The unified app limits who can see them, and the owner reviews access in SAP and in the recipe systems and files that hold them [TBC]. They're kept off the data platform and out of extracts unless the owner approves, and agents use AI models only in an environment the organisation controls [TBC]. | Access reviews, approvals, agent register |
| R-22 AI tools and data | Approved AI tools listed [TBC]; agents are tested at design review to treat outside content as data, never as instructions; the owner's approval, and the data protection officer's for personal data, recorded before Confidential or Restricted data goes to an outside model | Approved-tools list, approvals, agent register |
