# Transition Notes

**Status:** Working notes for the data team, outside the governance framework · **Owner:** the data team · **Ends:** when the master data vendor has left and nothing is raised in the current app. Then archive them, as the record of how the rules were applied until then.

Until a request type moves to the unified master data app, it's raised in the
current app [TBC: its name, and who runs it] and processed in SAP by the master
data vendor. The rules still apply. These notes say what's different until
then, how each request type moves, and what the vendor must do. The framework
itself describes only the target, so it doesn't change when the vendor leaves.

Customer and supplier requests move first, in December 2026, once their
profiles are approved in early November. The rest, including the material
master, follow one request type at a time, and the vendor leaves by Q2 2027.
The programme plan [TBC: where it's kept] has the detailed dates.

## What's different until then

- **Requests** are raised in the current app, and the vendor makes the changes
  in SAP. For the request types it handles, only the vendor's staff hold SAP
  change rights, and they lose them for each request type as it moves. Data
  with its own governed process, such as engineering changes or pricing [TBC],
  keeps that process (R-03).
- **Approvals:** the vendor approves requests within the rules, with one person
  entering each change and another checking it. It never approves mass changes
  or exceptions, and never confirms sensitive changes (R-06, R-12).
- **Agents** coordinate, check and propose, but never create or change master
  data (R-18). Until the request assistant and the owner assistant start,
  attribute owners and their delegates prepare their own cases.

## How a request type moves

Each request type follows the same steps, because the unified app's checks come
from the domain profiles:

1. Its owners approve the domain profile: the GPDO the breakdown and any shared
   data, and the attribute owner the settings and request types.
2. The data team builds and tests what the unified app needs for it: the
   checks, routing to the attribute owner and their delegates, holding
   sensitive changes until they're confirmed, recording the request behind
   every change, and posting to SAP.
3. Requesters, attribute owners and delegates are trained [TBC: format].
4. The request type moves. The vendor stops processing it and loses the SAP
   rights to change it.

Nothing moves on a date alone. If a profile isn't approved, or the app fails
its tests, the request type stays with the vendor until it's ready. [TBC: the
fallback if that runs past the vendor's exit date]

## Cleaning up existing data

The rules apply to new and changed records, and existing records are cleaned
up domain by domain, in the order their request types move.

- Before each domain moves, its worst data is cleaned up first, using the
  scorecards: duplicates and critical fields come first, because they break
  transactions and trip the unified app's checks.
- The vendor's remaining capacity goes into this clean-up before it leaves, as
  mass changes the attribute owner signs off (R-07).
- After the vendor leaves, the quality agent and the attribute owners handle
  what remains.

## How the rules are enforced until then

Rules not listed here are enforced as in the
[controls catalogue](../controls.md). Where a control there relies on the
unified app, ownership and settings are recorded in the domain profiles
instead.

| Rule | Until the request type moves | Evidence |
| --- | --- | --- |
| R-03 Governed process | Requests are raised in the current app; requests by email or spreadsheet are turned away | Request log |
| R-05 Checks before approval | The vendor's checklist and SAP's mandatory fields, with likely duplicates flagged by the quality agent | Check results with each request |
| R-06 Approval | The vendor's maker-checker; turnaround in the vendor's reports | Vendor reports |
| R-07 Mass changes | The attribute owner signs off, and the change is tested before it's made | Sign-off and test evidence |
| R-08 Traceability | Each month, SAP changes are matched to requests in the current app, with the change reconciler agent's help. Internal controls reviews any change left unmatched, and a sample of the agent's matches. | Reconciliation report |
| R-09 Conventions and quality checks | The data platform runs the checks each domain profile defines on SAP data and publishes the scorecards monthly | Scorecards |
| R-10 Fix at source, fix the cause | The quality agent groups failing records by cause and proposes new checks; the vendor fixes the records in SAP | Issue log; checks added to the profile |
| R-11 Stale records | As in the target, except that the vendor blocks the records | Approved list |
| R-12 Third parties | The vendor's contract and the requirements below, with a monthly performance review by the data team | Performance report, exit records |
| R-13 Sensitive changes | SAP's settings block payment after a bank-detail change until the attribute owner or their delegate confirms it, and limit one-time accounts and payees entered on invoices. Other sensitive changes are confirmed before the vendor enters them, and the monthly matching checks what was entered. | Confirmation log |
| R-14 Payment data kept apart from paying | The data team checks each quarter that vendor staff and confirmers hold no buying or payment rights | Access review |
| R-15 Bank detail verification | The attribute owner or their delegate calls the supplier back on contact details already on file, and records it on the request. A report flags bank accounts already used by another supplier or customer. | Call-back record, flag report |
| R-16 Classified fields and access | As in the target, with access to the current app reviewed alongside SAP's | Access reviews |
| R-20 Exceptions | Exceptions are recorded in a register [TBC: where], and the governance coordinator reminds owners before they expire | Register |

## The master data vendor's requirements

Until it leaves, the quality of the vendor's work is the quality of our master
data. These requirements belong in its contract, including how it hands over.

### The work

- Process create and change requests for SAP master data in the domains in
  scope, following the [rulebook](../rulebook.md) and each domain's profile.
- Work only from complete requests raised in the current app, and turn away
  requests by email or spreadsheet (R-03).
- Act on what the agents flag, such as likely duplicates, before processing a
  request (R-05).
- Apply each domain's conventions and checks (R-05, R-09). Every change is
  entered by one person and checked by another; nobody checks their own work
  (R-06).
- Never set rules, approve exceptions or confirm sensitive changes (R-12).
  Pass questions and sensitive changes to the attribute owner or their
  delegate (R-13).
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
  unified app, as set out above.
- Before each domain moves, the vendor's remaining capacity goes into the
  clean-up above.
- Before each request type moves, write down the working rules and checks the
  team uses for it, so they can become the unified app's checks and agent
  instructions.
- Hand over all tickets and approval evidence before exit. They are the audit
  trail for R-08, R-13 and R-15.
- As each request type moves, vendor staff lose the SAP rights to change it,
  and they lose all SAP access the day their work ends.
- [TBC: a fallback for any request type the unified app isn't ready for, such
  as a short extension, and a pricing model that doesn't penalise the move]
