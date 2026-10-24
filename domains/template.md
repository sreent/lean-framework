# Domain Profile Template

Each GPDO proposes a profile for their own domain, using this template. The
GPDOs agree the proposals together at the monthly owner review, so nothing is
missed or owned twice. After that, the GPDO maintains the profile, and
attribute owners approve changes to their part of it.

The [starter material](starters/) has common SAP checks, conventions and
settings for customer, pricing, material, production, supplier and finance
data. Use, change or ignore it: the breakdown is the GPDO's call.

## How to break a domain down

A domain can be split by subdomain (such as customer and pricing), by business
unit, by group of fields, or a mix. Two things keep any split working:

- **One owner for each piece of data.** For any field on any record, it must
  be clear who owns it (R-02). In SAP, a common split is that general data,
  shared by every business unit, has one owner, while data for a business
  unit's own company codes, sales organisations or plants is owned by that
  business unit.
- **One set of rules for the domain.** Conventions and checks stay the same
  across subdomains and business units unless the GPDO agrees a difference
  (R-09). Otherwise, splitting ownership brings back the inconsistency we're
  fixing.

---

# [Domain] Profile

**Status:** Proposed by the [domain] GPDO · **Agreed:** [date, at the monthly owner review] · **Rules:** [Rulebook](../rulebook.md)

## Breakdown

| Part of the domain (subdomain, business unit or field group) | Master data covered | Owner | In scope from |
| --- | --- | --- | --- |
| [e.g. customer general data] | [e.g. name, address, tax numbers] | [the GPDO, or a named attribute owner] | [now, or a later date] |
| [e.g. customer sales data, business unit A] | [e.g. sales area data for its sales organisations] | [a named attribute owner] | [now, or a later date] |

Shared with other domains: [data split with another GPDO's domain, such as
views of the material master, and the agreed split]

## Settings

The settings the rulebook refers to, for each subdomain:

| Setting | Rule | [Subdomain] |
| --- | --- | --- |
| Governed process | R-03 | |
| System of record | R-04 | |
| Turnaround times | R-06 | |
| Contact for the stewards' questions | R-06 | |
| Critical fields and their conventions | R-09 | |
| Mandatory checks | R-05, R-09 | |
| Quality thresholds | R-09 | |
| Duplicate match rules | R-05 | |
| Inactivity period, block and exclusions | R-11 | |
| Sensitive fields, and who confirms changes to them | R-13, R-14 | |
| One-time accounts and payee in document | R-13 | |
| Personal data, payment data and trade secret fields | R-16, R-21 | |
| Request types approved automatically | R-06 | |
| Agent changes approved at level 2 | R-18 | |
