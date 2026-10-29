# GateSecure Decision Log

**Status:** Initial proposed decisions  
**Version:** 0.1  
**Last updated:** 29 October 2026

This log records current product decisions and why they were selected. Decisions remain open to revision when customer discovery, technical feasibility, security analysis, or pilot evidence provides a reason to change them.

| ID | Topic | Proposed decision | Rationale | Status |
|---|---|---|---|---|
| D-001 | Estate governance | GateSecure operates the platform; each estate has independent administration and policies | Supports multiple estates while isolating their records and responsibilities | Proposed |
| D-002 | Resident onboarding | Landlord/property manager is a primary verifier, with estate approval where required | Matches tenancy responsibilities while supporting different governance arrangements | Proposed |
| D-003 | Household accounts | Individual identities with household administration and role-appropriate credentials | Improves accountability and makes individual revocation possible | Proposed |
| D-004 | Children | Support configurable age-appropriate restrictions for selected facilities | Enables estate policy enforcement without claiming to guarantee safety | Proposed |
| D-005 | Worker management | Distinguish estate-contracted, household-contracted, and one-time service providers | Clarifies who sponsors access and which areas are permitted | Proposed |
| D-006 | Worker identity | Where justified, reuse one identity across independently scoped access grants | Reduces duplicate registration while protecting cross-household privacy | Proposed |
| D-007 | Guard authority | Guards have limited operational permissions; account and policy administration is restricted | Separates operational work from administrative authority | Proposed |
| D-008 | Visitor lookup | Support approved lookup methods without exposing a public resident directory | Balances visitor usability and resident privacy | Proposed |
| D-009 | Visitor data | Require only justified fields; omit photograph by default and review mandatory gender/ID collection | Reduces unnecessary personal-data collection | Proposed |
| D-010 | Revocation | Combine automated lifecycle events, authorized human oversight, and emergency revocation | Prevents stale access while retaining governance and accountability | Proposed |
| D-011 | MVP | Prioritize visitor management, resident management, guard operations, and auditability | Tests the core product value without overloading the first release | Proposed |
| D-012 | Hardware strategy | Software-first, simulator-first, then compatible hardware integration | Reduces initial hardware investment and enables controlled testing | Proposed |
| D-013 | Alternative access | Design for mobile, web, guard-assisted processes, and defined outage handling | Avoids assuming every user or site has the same devices or connectivity | Proposed |
| D-014 | Vehicles | Share the authorization model; introduce vehicle automation later | Keeps the architecture extensible while limiting initial complexity | Proposed |
| D-015 | Apartments/facilities | Main gate first; apartment and facility access later | Establishes the core workflow before broadening scope | Proposed |
| D-016 | Notifications | Configurable channels and fallback; silence never equals approval | Improves reachability without weakening authorization | Proposed |
| D-017 | Business model | Evaluate estate subscription plus optional integration and support | Aligns likely procurement with estate-level operations; requires validation | Hypothesis |
| D-018 | Competitive position | Treat differentiation as unvalidated until market research is completed | Avoids claiming common access-control features are unique | Open validation |

## Change process

When a decision changes:
1. Update the relevant section of `product-information.md`.
2. Add a new row or revision note here, including the reason.
3. Identify requirements, workflows, security controls, and tests affected by the change.
4. Reassess any risks or assumptions that depended on the previous decision.

Do not silently change a material product decision in implementation without updating the documentation.
