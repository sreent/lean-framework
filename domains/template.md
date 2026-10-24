# Domain Profile Template

Each GPDO approves a profile for their own domain, using this template, and
agrees any data shared with another domain with that domain's GPDO. The
governance coordinator agent can draft it from the starters and the data as it
stands. Once the unified app holds profiles as settings, the profile lives
there, and owners approve changes to it in the app.

The [starter material](starters/) has common SAP checks, conventions and
settings for customer, pricing, material, production, supplier and finance
data. Use, change or ignore it: the breakdown is the GPDO's call.

## How to break a domain down

A domain can be split by subdomain (such as customer and pricing), by business
unit, by group of fields, or a mix. Four things keep any split working:

- **One owner for each piece of data.** For any field on any record, it must
  be clear who owns it (R-02). In SAP, a common split is that general data,
  shared by every business unit, has one owner, while data for a business
  unit's own company codes, sales organisations or plants is owned by that
  business unit.
- **One set of rules for the domain.** Conventions and checks stay the same
  across subdomains and business units unless the GPDO agrees a difference
  (R-09). Otherwise, splitting ownership brings back the inconsistency we're
  fixing.
- **One steward, unless volume needs more.** The GPDO names one steward for
  the domain from their own team, or one for each part where volume needs it.
  The [charter](../charter.md) says what stewards do.
- **Include data outside SAP.** List every system that holds your domain's
  data, such as recipe systems, PLM or spreadsheets, even if it comes into the
  framework later. Ownership, classification and access apply to it now
  (R-01, R-02, R-16, R-21, R-22).

---

# [Domain] Profile

**Status:** Approved by the [domain] GPDO on [date] · **Rules:** [Rulebook](../rulebook.md)

## Breakdown

| Part of the domain (subdomain, business unit or field group) | Data covered | System | Owner | Steward | In scope from |
| --- | --- | --- | --- | --- | --- |
| [e.g. customer general data] | [e.g. name, address, tax numbers] | [e.g. SAP] | [the GPDO, or a named attribute owner] | [a named person or team] | [now, or a later date] |
| [e.g. customer sales data, business unit A] | [e.g. sales area data for its sales organisations] | [e.g. SAP] | [a named attribute owner] | [a named person or team] | [now, or a later date] |
| [e.g. recipes] | [e.g. formulas and process parameters] | [e.g. the recipe system] | [a named attribute owner] | [a named person or team] | [e.g. owned and protected now; the other rules later] |

Shared with other domains: [data split with another GPDO's domain, such as
views of the material master, and the split agreed with that GPDO]

## Settings

The settings the rulebook refers to, for each subdomain:

| Setting | Rule | [Subdomain] |
| --- | --- | --- |
| Governed process | R-03 | |
| Request types | R-03 | |
| System of record | R-04 | |
| Turnaround times | R-06 | |
| Critical fields and their conventions | R-09 | |
| Mandatory checks | R-05, R-09 | |
| Quality thresholds | R-09 | |
| Duplicate match rules | R-05 | |
| Inactivity period, block and exclusions | R-11 | |
| Sensitive fields | R-13, R-14 | |
| One-time accounts and payee in document | R-13 | |
| Confidential and Restricted fields, marking personal data, payment data and trade secrets | R-14, R-16, R-21 | |
| Request types approved automatically | R-06 | |
| Agent changes approved at level 2 | R-18 | |
