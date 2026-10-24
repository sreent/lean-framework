# Interim Arrangements

**Status:** Draft v0.1 · **Approved by:** the Head of Data, AI & Development · **Ends:** when the last request type has moved to the unified master data app and the master data vendor has left (see the [roadmap](roadmap.md)). Then delete this document.

Until a request type moves to the unified master data app, it's raised in the
current app [TBC: its name, and who runs it] and processed in SAP by the master
data vendor. The rules still apply. This document says what's different until
then, and what the vendor must do. The other documents describe the target, so
they don't change when the vendor leaves.

## What's different until then

- **Requests** are raised in the current app, and the vendor makes the changes
  in SAP. Only the vendor's staff hold SAP change rights, and they lose them for
  each request type as it moves.
- **Approvals:** the vendor approves requests within the rules, with one person
  entering each change and another checking it. It never approves mass changes
  or exceptions, and never confirms sensitive changes (R-06, R-12).
- **Agents** coordinate, check and propose, but never create or change master
  data (R-18).

One agent works only during this period. It's part of the agent register, and
the data governance specialist owns it like the others:

| Agent | Works for | Does | Rules |
| --- | --- | --- | --- |
| Change reconciler | Internal controls | Matches the SAP changes that the monthly report can't match to a request in the current app, because the reference is missing or unclear | R-08 |

## How the rules are enforced until then

Rules not listed here are enforced as in the
[controls catalogue](controls.md), without the unified app's part.

| Rule | Until the request type moves | Evidence |
| --- | --- | --- |
| R-03 Governed process | Requests are raised in the current app; requests by email or spreadsheet are turned away | Request log |
| R-05 Checks before approval | The vendor's checklist and SAP mandatory fields. The quality agent flags likely duplicates, and the request assistant reviews requests in the current app [TBC]. | Check results stored with each request |
| R-06 Approval | The vendor's maker-checker; turnaround in the vendor's reports | Vendor reports |
| R-07 Mass changes | The data owner signs off by email [TBC]; tested in a non-production system first | Sign-off and test evidence |
| R-08 Traceability | Each month, a report matches SAP change documents to requests in the current app, the change reconciler agent matches those with a missing or unclear reference, and [TBC: the internal controls team] reviews any change left without one | Reconciliation report |
| R-09 Conventions and quality checks | The data platform runs the checks each domain profile defines on SAP data and publishes the scorecards monthly | Scorecards |
| R-10 Fix at source, fix the cause | The quality agent groups failing records by cause and proposes new checks; the vendor fixes the records in SAP | Issue log; checks added to the profile |
| R-11 Stale records | As in the target, except that the vendor blocks the records | Approved list |
| R-12 Third parties | The vendor's contract and the requirements below; a monthly performance review by the data governance specialist, from the governance coordinator's report | Performance report, exit records |
| R-13 Sensitive changes | SAP sensitive-field settings block payment until the steward confirms the change, for example with FK08/FK09 for suppliers and FD08/FD09 for customers [TBC: confirm for your release]. Other sensitive changes, including credit limits and unblocking, are confirmed before the vendor enters them. SAP settings limit one-time accounts and payee in document [TBC]. | Confirmation log |
| R-14 Payment data kept apart from paying | The platform team reviews the SAP roles of vendor staff and confirmers each quarter for conflicting rights [TBC: rule set] | Access review |
| R-15 Bank detail verification | The steward calls the supplier back on details already on file and records the call-back on the request; a report flags shared bank accounts | Call-back evidence, flag report |
| R-20 Exceptions | Exceptions are recorded in [TBC: location], and the governance coordinator reminds owners before they expire | Register |

## The master data vendor's requirements

Until it leaves, the quality of the vendor's work is the quality of our master
data. These requirements belong in its contract, including how it hands over.

### The work

- Process create and change requests for SAP master data in the domains in
  scope, following the [rulebook](rulebook.md) and each domain's profile.
- Work only from complete requests raised in the current app, and turn away
  requests by email or spreadsheet (R-03).
- Act on what the agents flag, such as likely duplicates, before processing a
  request (R-05).
- Apply each domain's conventions and checks (R-05, R-09). Every change is
  entered by one person and checked by another; nobody checks their own work
  (R-06).
- Never set rules, approve exceptions or confirm sensitive changes (R-12).
  Pass questions and sensitive changes to the steward (R-13).
- Fix issues in SAP, never in a downstream copy, and report the cause (R-10).

### Service levels

- Turnaround times as set in each domain profile.
- A first-time-right rate of at least [TBC], with each reworked request
  reported with its cause.
- A monthly report covering volumes, turnaround, first-time-right, quality
  issues and their root causes.

### Access and data protection

- SAP access for named individuals only, reviewed quarterly.
- No vendor staff hold rights to create purchase orders, post invoices, run
  payments or release credit (R-14). [TBC: if the vendor also does accounts
  payable work, use separate teams and separate access]
- Personal data is handled under a data processing agreement. Any work done
  outside [TBC: country or region] is agreed in advance.
- Trade secrets, such as formulas and recipes, are seen only by named
  individuals under a confidentiality agreement, and never from outside
  [TBC: country or region] unless agreed in advance (R-21).

### Evidence and audit

- Every change is linked to its approved request (R-08).
- The organisation and its auditors can review the vendor's work and records.

### Exit

- The vendor keeps full service for every request type until it moves to the
  unified app, as the [roadmap](roadmap.md) sets out.
- Before each domain moves, the vendor's remaining capacity goes into cleaning
  up its worst existing data, as mass changes the data owner signs off (R-07).
- Before each request type moves, write down the working rules and checks the
  team uses for it, so they can become the unified app's checks and agent
  instructions.
- Hand over all tickets and approval evidence before exit. They are the audit
  trail for R-08, R-13 and R-15.
- As each request type moves, vendor staff lose the SAP rights to change it,
  and they lose all SAP access the day their work ends.
- [TBC: a fallback for any request type the unified app isn't ready for, such
  as a short extension, and a pricing model that doesn't penalise the move]
