# Master Data Rulebook

**Status:** Draft v0.1 · **Approved by:** [TBC: Head of Data, AI & Development] · **Under:** [Master data governance charter](charter.md)

Each rule says what must be true, not how it's enforced. The
[controls catalogue](controls.md) covers how, today and once the app is live.
The business owns what good data looks like: each domain's validation and
quality rules (conventions, checks and thresholds) and its other settings sit
in its domain profile, which its GPDO proposes and maintains. This rulebook only
requires that they exist and are applied.

"Why" names what the rule addresses. Rules R-01 to R-12 fix the problem behind
our data quality issues, master data that is **incorrect** or **inconsistent**.
Rules R-13 to R-20 manage **risks** that come with master data: payment fraud,
privacy and audit.

## Ownership

| ID | Rule | Why |
| --- | --- | --- |
| R-01 | Every master data domain has a named data owner, its GPDO, accountable for its data however it's changed: by people, the vendor, the app or agents. | Incorrect, inconsistent |
| R-02 | Every field on every record has exactly one owner: the domain's data owner, or an attribute owner the data owner has delegated part of the domain to, by subdomain, business unit or group of fields. The domain profile records each delegation. In S/4HANA, business partner central data (name, address, tax numbers, bank details) has one owner across the supplier and customer roles. | Incorrect, inconsistent |

## Changing master data

| ID | Rule | Why |
| --- | --- | --- |
| R-03 | Master data is created and changed only through the governed process for its domain, starting with a complete request. | Incorrect, inconsistent |
| R-04 | Each field has one system of record. Other systems take the data from it, send changes back as requests, and hold its key. | Inconsistent |
| R-05 | Every request passes its domain's mandatory checks, including a duplicate check, before it's approved. | Incorrect, inconsistent |
| R-06 | A steward approves routine requests within the domain's rules, or the app approves them automatically for request types the data owner has approved. Nobody approves their own request. Requests are completed within the turnaround times in the domain profile. | Incorrect |
| R-07 | A change to more than [TBC: 50] records is a mass change. It needs the data owner's sign-off, a test and a rollback plan. | Incorrect |
| R-08 | Every change to SAP master data can be traced to an approved request. | Incorrect, fraud risk |

## Quality

| ID | Rule | Why |
| --- | --- | --- |
| R-09 | Each domain profile defines its critical fields, the conventions they follow (format, naming and allowed values), the checks that enforce them, and a quality threshold for each. Conventions and checks are the same across the domain's subdomains and business units unless the GPDO agrees a difference. Results are published monthly. | Incorrect, inconsistent |
| R-10 | Issues are fixed in the system of record, never only in a downstream copy or report. A recurring issue leads to a new or better check, which the data owner adds to the domain profile, so it doesn't come back. | Incorrect, inconsistent |
| R-11 | Records unused for the period in the domain profile are blocked unless someone confirms they're still needed. Records with open items, orders or contracts are excluded. The data owner approves the list as a whole. | Incorrect |

## The vendor

| ID | Rule | Why |
| --- | --- | --- |
| R-12 | The master data vendor works within these rules under its contract, and its quality is measured. It never sets rules, approves exceptions or confirms sensitive changes. | Incorrect, audit risk |

## Sensitive and payment data

| ID | Rule | Why |
| --- | --- | --- |
| R-13 | A change to a sensitive field, as listed in the domain profile, can't be used until the field's owner, or someone they name in their team, confirms it. The confirmer is never in the team that entered the change. Unblocking a record, and bank details on one-time accounts or entered as a payee in a document, count as sensitive changes. | Fraud risk |
| R-14 | Whoever enters or confirms a change to payment data can't create purchase orders, post invoices, run payments or release credit. | Fraud risk |
| R-15 | A change to a supplier's bank details is verified with the supplier using contact details that weren't changed along with it, and the evidence is kept. A bank account already used by another supplier or customer is flagged. | Fraud risk |

## Privacy and access

| ID | Rule | Why |
| --- | --- | --- |
| R-16 | Each domain profile flags the fields that hold personal data or payment data. Access to them is limited to roles that need it and reviewed [TBC: twice a year]. A report or extract takes the highest classification of the data in it, and Restricted and personal data is masked outside production. | Privacy risk, fraud risk |
| R-17 | Personal data is blocked when its purpose ends and deleted when its retention period ends. Records are archived only in line with retention rules. | Privacy risk |

Classification levels [TBC: use the company's scheme if it has one]:

| Level | Meaning | Master data examples |
| --- | --- | --- |
| Public | Approved for release outside the organisation | Published product content |
| Internal | Everyday business data | Material numbers, plant codes, business suppliers' and customers' names and addresses |
| Confidential | Harmful if disclosed; access on business need | Contacts, pricing, payment terms, credit limits, standard costs; all personal data |
| Restricted | Serious financial, legal or fraud harm if disclosed | Bank details; tax IDs of individuals |

## Automation and agents

| ID | Rule | Why |
| --- | --- | --- |
| R-18 | Every agent has a named agent owner, works only within the autonomy level the data owner has approved for their domain, and logs every action. Agents never approve requests or exceptions, change sensitive fields, delete records or grant access. They treat content from outside the organisation as data to check, never as instructions. Restricted data goes to an AI model outside the organisation only with the data owner's and the data protection officer's approval. | Audit risk, privacy risk |

Autonomy levels:

| Level | The agent may | Human role |
| --- | --- | --- |
| 0. Observe | Read, measure and report | Reads the reports |
| 1. Propose | Prepare a change or decision for a person to approve | A steward or owner approves each one |
| 2. Act and notify | Make changes of a type the data owner has approved, never to sensitive fields, through the governed process, in runs below the mass-change size | The agent owner reviews the log and can reverse any change |

## The data team

| ID | Rule | Why |
| --- | --- | --- |
| R-19 | Nobody who builds or changes the app or the agents changes production master data outside the governed process, except through emergency access that someone outside the data team reviews. Changes to the app and the agents are tested before release. | Audit risk |

## Exceptions

| ID | Rule | Why |
| --- | --- | --- |
| R-20 | Exceptions are approved by the data owner, or the attribute owner for their fields, never by whoever asked for them. Each one is recorded with its rule, reason, approver and expiry, expires within [TBC: 90 days], and can be renewed once. The controls the charter lists can't be waived. | Audit risk |

## Change log

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 2026-10-23 | First version, replacing the data governance, classification and master data standards |
