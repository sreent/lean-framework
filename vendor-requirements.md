# Master Data Vendor Requirements

**Status:** Draft v0.1 · **Approved by:** [TBC: Head of Data, AI & Development] · **Applies through:** the vendor contract [TBC: renewal date]

The master data vendor holds the data steward role today, so the quality of
its work is the quality of our master data. These requirements belong in the
contract.

## The work

- Process create and change requests for SAP master data in the domains in
  scope, following the [rulebook](rulebook.md) and each domain's profile.
- Work only from complete requests received through the governed process, and
  turn away requests by email or spreadsheet (R-03).
- Apply each domain's conventions and checks (R-05, R-09). Every change is
  entered by one person and checked by another; nobody checks their own work
  (R-06).
- Never set rules, approve exceptions or confirm sensitive changes (R-12).
  Pass sensitive changes to the confirmer named in the domain profile (R-13).
- Fix issues in SAP, never in a downstream copy, and report the cause (R-10).

## Service levels

- Turnaround times as set in each domain profile.
- A first-time-right rate of at least [TBC], with each reworked request
  reported with its cause.
- A monthly report covering volumes, turnaround, first-time-right, quality
  issues and their root causes.

## Access and data protection

- SAP access for named individuals only, reviewed quarterly.
- No vendor staff hold rights to create purchase orders, post invoices, run
  payments or release credit (R-14). [TBC: if the vendor also does accounts
  payable work, use separate teams and separate access]
- Personal data is handled under a data processing agreement. Any work done
  outside [TBC: country or region] is agreed in advance.

## Evidence and audit

- Every change is linked to its approved request (R-08).
- The organisation and its auditors can review the vendor's work and records.

## Moving to automation

- Write down the working rules and checks the team uses, so they can become app
  validations and agent instructions.
- Support testing as the app takes over request types. Volumes will fall as it
  does. [TBC: a pricing model that doesn't penalise automation]
