# Master Data Vendor Requirements

**Status:** Draft v0.1 · **Approved by:** [TBC: Head of Data, AI & Development] · **Applies through:** the vendor contract, until the vendor leaves in Q2 2027 [TBC: date]

The master data vendor holds the data steward role until it leaves in
Q2 2027, so the quality of its work is the quality of our master data. These
requirements belong in the contract, including how the vendor hands over.

## The work

- Process create and change requests for SAP master data in the domains in
  scope, following the [rulebook](rulebook.md) and each domain's profile.
- Work only from complete requests raised in the current app, and turn away
  requests by email or spreadsheet (R-03).
- Act on what the agents flag, such as likely duplicates and pre-check
  findings, before processing a request (R-05).
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
- Trade secrets, such as formulas and recipes, are seen only by named
  individuals under a confidentiality agreement, and never from outside
  [TBC: country or region] unless agreed in advance (R-21).

## Evidence and audit

- Every change is linked to its approved request (R-08).
- The organisation and its auditors can review the vendor's work and records.

## Exit by Q2 2027

- Request types move to the unified master data app one at a time, each once
  the app handles it and requesters are trained. The vendor keeps full service
  for every request type until it has moved.
- Before each request type moves, write down the working rules and checks the
  team uses for it, so they can become the unified app's checks and agent
  instructions.
- Hand over all tickets and approval evidence before exit. They are the audit
  trail for R-08, R-13 and R-15.
- Vendor staff lose SAP access the day their work ends.
- [TBC: a fallback for any request type the unified app isn't ready for, such
  as a short extension, and a pricing model that doesn't penalise the move]
