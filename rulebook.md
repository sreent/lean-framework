# Master Data Rulebook

**Status:** Draft v0.10 · **Approved by:** the Head of Data, AI & Development · **Under:** [Master data governance charter](charter.md)

Each rule says what must be true, not how it's enforced; the
[controls catalogue](controls.md) covers how. The business owns what good data
looks like: each domain's validation and quality rules (conventions, checks and
thresholds) and its other settings sit in its domain profile, which its GPDO
and attribute owners approve and maintain. This rulebook only requires that
they exist and are applied.

"Why" names what the rule addresses. Rules R-01 to R-12 fix the problem behind
our data quality issues, master data that is **incorrect** or **inconsistent**.
Rules R-13 to R-22 manage **risks** that come with master data: trade
secrets, payment fraud, privacy and audit. Rule IDs follow the order the rules
were added, so R-21 and R-22 sit with the rules they're closest to.

"Data owner" in these rules means the owner of the part of the domain
concerned: its attribute owner, or the GPDO for a part they keep. The GPDO
stays accountable for the whole domain (R-01). "Delegate" means someone from
the data owner's team whom the owner names to decide the cases the app can't,
where a rule allows it.

The rules apply to the systems the framework governs: SAP now, and other
systems as they come in (see the data landscape in the
[operating model](operating-model.md)). Five rules apply to all data from the
start, wherever it's held: ownership (R-01, R-02), classified fields and
access (R-16), trade secrets (R-21) and AI tools (R-22).

The rules apply to new and changed records from the effective date in the
charter. Existing records are brought into line domain by domain, in the order
the [roadmap](roadmap.md) sets. Until then, gaps in existing records are
tracked on the scorecards rather than treated as breaches.

The rules describe the target setup. Until a request type moves to the unified
master data app, the [interim arrangements](interim.md) say how its rules are
applied.

## Ownership

| ID | Rule | Why |
| --- | --- | --- |
| R-01 | Every master data domain has a named data owner, its GPDO, accountable for its data however it's changed: by people, third parties, the app or agents. | Incorrect, inconsistent |
| R-02 | Every field on every record has exactly one owner: the attribute owner its GPDO has delegated its part of the domain to, by subdomain, business unit or group of fields, or the GPDO for a part they keep. The domain profile records each delegation. In S/4HANA, business partner central data (name, address, tax numbers, bank details) has one owner across the supplier and customer roles. | Incorrect, inconsistent |

## Changing master data

| ID | Rule | Why |
| --- | --- | --- |
| R-03 | Master data is created and changed only through the governed process for its domain, starting with a complete request. | Incorrect, inconsistent |
| R-04 | Each field has one system of record. Other systems take the data from it, send changes back as requests, and hold its key. | Inconsistent |
| R-05 | Every request passes its domain's mandatory checks, including a duplicate check, before it's approved. A change to an existing record must pass the checks on the fields it changes and on the record's critical fields. | Incorrect, inconsistent |
| R-06 | Requests other than mass changes (R-07) are approved within the domain's rules: automatically by the unified app for request types the data owner has approved, and otherwise by the data owner for the part the request touches, or their delegate. Nobody approves their own request. Requests are completed within the turnaround times in the domain profile. | Incorrect |
| R-07 | A change to more than [TBC: 50] records is a mass change. It needs the data owner's sign-off, a test and a rollback plan. | Incorrect |
| R-08 | Every change to master data in a governed system can be traced to an approved request. | Incorrect, fraud risk |

## Quality

| ID | Rule | Why |
| --- | --- | --- |
| R-09 | Each domain profile defines its critical fields, the conventions they follow (format, naming and allowed values), the checks that enforce them, and a quality threshold for each. Conventions and checks are the same across the domain's subdomains and business units unless the GPDO agrees a difference. Results are published monthly. | Incorrect, inconsistent |
| R-10 | Issues are fixed in the system of record, never only in a downstream copy or report. A recurring issue leads to a new or better check, which the data owner adds to the domain profile, so it doesn't come back. | Incorrect, inconsistent |
| R-11 | Records unused for the period in the domain profile are blocked unless someone confirms they're still needed. Records with open items, orders or contracts are excluded. The data owner approves the list as a whole. | Incorrect |

## Third parties

| ID | Rule | Why |
| --- | --- | --- |
| R-12 | Any third party that maintains master data works within these rules under its contract, and its quality is measured. It never sets rules, approves exceptions or confirms sensitive changes. | Incorrect, audit risk |

## Sensitive and payment data

| ID | Rule | Why |
| --- | --- | --- |
| R-13 | A change to a sensitive field, as listed in the domain profile, can't be used until its data owner, or their delegate, confirms it. Nobody confirms a change they requested or entered. Unblocking a record, and bank details on one-time accounts or entered as a payee in a document, count as sensitive changes. | Fraud risk |
| R-14 | Payment data fields, as marked in the domain profile, are always sensitive fields (R-13). Whoever confirms a change to them, or can change them directly in SAP, can't create purchase orders, post invoices, run payments or release credit. Requesters may hold those rights, because their changes can't be used until confirmed. | Fraud risk |
| R-15 | A change to a supplier's bank details is verified with the supplier using contact details that weren't changed along with it, and the evidence is kept. A new supplier's bank details are verified the same way, using contact details from a source other than the request [TBC: such as its registered website]. A bank account already used by another supplier or customer is flagged. | Fraud risk |

## Trade secrets, privacy and access

| ID | Rule | Why |
| --- | --- | --- |
| R-16 | Each domain profile lists the fields that are Confidential or Restricted, as its data owner decides, and marks those that hold personal data, payment data or trade secrets. Access to them is limited to roles that need it, as the data owner approves, and reviewed [TBC: twice a year], in every system that holds them. A report or extract takes the highest classification of the data in it, and Restricted and personal data is masked outside production. | Trade secret risk, privacy risk, fraud risk |
| R-17 | Personal data is blocked when its purpose ends and deleted when its retention period ends. Records are archived only in line with retention rules. | Privacy risk |
| R-21 | Trade secrets, such as formulas, recipes and process parameters, are Restricted wherever they're held, in SAP or not. They're copied, extracted or made available to people or agents only as the data owner approves, and never go to an AI model outside an environment the organisation controls, under terms that stop the provider keeping or training on them. | Trade secret risk |

Classification is about who can see data, and sensitive fields (R-13) are
about which changes need confirming, so a supplier's address can be Internal
and still sensitive.

Classification levels [TBC: use the company's scheme if it has one]. The
examples show where common data usually sits; each data owner decides how
their own fields are classified, and records it in their domain profile
(R-16):

| Level | Meaning | Examples |
| --- | --- | --- |
| Public | Approved for release outside the organisation | Published product content |
| Internal | Everyday business data | Material numbers, plant codes, business suppliers' and customers' names and addresses |
| Confidential | Harmful if disclosed; access on business need | Contacts, prices and margins, supplier prices, payment terms, credit limits, standard costs; all personal data |
| Restricted | Serious financial, legal, competitive or fraud harm if disclosed | Bank details; tax IDs of individuals; formulas, recipes, process parameters and own product specifications |

## Automation and agents

| ID | Rule | Why |
| --- | --- | --- |
| R-18 | Every agent is recorded in the agent register with a named agent owner, works only within the autonomy level the data owner has approved for their part, and logs every action. At any level, agents may remind, chase and route, because that changes no data. They change master data only through the unified app, at level 2. They never approve requests or exceptions, confirm sensitive changes, change sensitive fields, delete records or grant access. | Audit risk |
| R-22 | Agents and the AI tools people use treat content from outside the organisation as data to check, never as instructions. Confidential and Restricted data goes to an AI model outside the organisation only with the data owner's approval, and the data protection officer's for personal data. Trade secrets follow R-21. | Trade secret risk, privacy risk |

Autonomy levels:

| Level | The agent may | Human role |
| --- | --- | --- |
| 0. Observe | Read, measure and report | Reads the reports |
| 1. Propose | Prepare a change or decision for a person to approve | The data owner or their delegate approves each one |
| 2. Act and notify | Make changes of a type the data owner has approved, never to sensitive fields, through the unified app, in runs below the mass-change size | The agent owner reviews the log and can reverse any change |

## The data team

| ID | Rule | Why |
| --- | --- | --- |
| R-19 | Nobody who builds or changes the app or the agents changes production master data outside the governed process, except through emergency access that internal controls reviews. Changes to the app and the agents are tested before release. | Audit risk |

## Exceptions

| ID | Rule | Why |
| --- | --- | --- |
| R-20 | Exceptions are approved by the data owner, never by a delegate or by whoever asked for them. Each one is recorded with its rule, reason, approver and expiry, expires within [TBC: 90 days], and can be renewed once. The controls the charter lists can't be waived. | Audit risk |

## Change log

| Version | Date | Change |
| --- | --- | --- |
| 0.10 | 2026-10-24 | Draft. Replaces the data governance, classification and master data standards. This version drops the data steward: data owners, or their delegates, decide what the app can't. Drafts 0.1 to 0.9 are in the repository history. |
