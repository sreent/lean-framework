# Controls Catalogue

**Status:** Draft v0.4 · **Approved by:** the Head of Data, AI & Development · **Rules:** [Rulebook](rulebook.md)

How each rule is enforced, and the evidence it leaves. The detail of each
control belongs in the app's design and the domain profiles; controls change
here as the app grows, and the rules don't.

Every setting in the unified app changes only with its owner's approval, which
the app logs, and each domain profile keeps its version history.

| Rule | How it's enforced | Evidence |
| --- | --- | --- |
| R-01 Named owner | The GPDOs sign the charter, and each part's owner is recorded in the unified app | Signed charter, ownership settings |
| R-02 Delegation | Each field's owner is a setting in the unified app, and the governance coordinator flags gaps and overlaps | Ownership settings, gap report |
| R-03 Governed process | All requests go through the unified app, or through a domain's own governed process where its profile names one, such as engineering change | Request log |
| R-04 One system of record | Interfaces carry data from SAP and reject bad records. The data platform compares non-SAP copies with SAP as each system comes in. | Consistency scorecard |
| R-05 Checks before approval | The unified app checks every request at entry against the domain's conventions, duplicate rules and mandatory checks | Check results with each request |
| R-06 Approval | The unified app approves the request types owners have approved, routes the rest to the owner or their delegates, and stops anyone approving their own request. A sample of automatic approvals is reviewed each month. | Approval log, sample reviews |
| R-07 Mass changes | The unified app's mass-change function, with the owner's sign-off, a test and a rollback plan | Sign-off and test evidence |
| R-08 Traceability | Only the unified app, or a domain's own governed process, can change master data in SAP. A daily report on the data platform shows any change without a request, for internal controls to review. | Reconciliation report |
| R-09 Conventions and quality checks | Checks run in the unified app at entry and on the data platform on stored data, and feed the scorecards | Scorecards |
| R-10 Fix at source, fix the cause | The quality agent groups failures by cause and raises fix requests in the unified app; owners add checks for issues that recur | Issue log, profile changes |
| R-11 Stale records | A monthly report lists inactive records, the owner approves the list, and the app blocks them | Approved list |
| R-12 Third parties | A contract holds any third party to these rules, and the data team reviews its performance monthly | Contract, performance reports |
| R-13 Sensitive changes | The unified app holds each sensitive change until the attribute owner or their delegate confirms it, and never lets anyone confirm their own change. SAP's settings limit one-time accounts and payees entered on invoices. | Confirmation log |
| R-14 Payment data kept apart from paying | The data team checks each quarter that confirmers, and the unified app, hold no buying or payment rights | Access review |
| R-15 Bank detail verification | The owner or their delegate calls the supplier back on contact details already on file, and records it on the request. The app flags bank accounts already used by another supplier or customer. | Call-back record, flag report |
| R-16 Classified fields and access | The unified app limits who sees classified fields to the roles the owner approves. The owner reviews who has access and approves extracts of Restricted data, and Restricted and personal data is masked outside live systems. | Settings, access reviews, approvals |
| R-17 Personal data lifecycle | SAP blocks personal data when its purpose ends and deletes it when its retention period ends [TBC: how] | Blocking and deletion log |
| R-18 Agents | The agent register, a design review before each agent starts, including approval of its AI model (R-21, R-22), and a log of every action. An agent moves up a level only with the owner's approval, on evidence from a sample of its work. | Register, logs, sample results |
| R-19 Data team | Emergency access is logged and reviewed by internal controls, and changes to the app and agents go through change management | Review log, release records |
| R-20 Exceptions | The unified app records each exception and reminds its owner before it expires | Exception register |
| R-21 Trade secrets | Owners review who can see trade secrets in SAP and in the systems and files that hold them. Trade secrets stay off the data platform and out of extracts unless the owner approves, and agents use AI models only in an environment the organisation controls. | Access reviews, approvals, agent register |
| R-22 AI tools and data | Only approved AI tools are used, and the owner's approval, and the data protection officer's for personal data, is recorded before Confidential or Restricted data goes to an outside model | Approved-tools list, approvals |
