# GateSecure Open Questions and Validation Plan

This document separates unresolved assumptions from decisions already proposed in the product-information document.

## 1. Customer and operating model

| Question | Why it matters | Suggested validation |
|---|---|---|
| Which property type is the first target: managed estate or apartment complex? | Changes roles, access points, buying process, and workflows | Interview property managers and observe an actual workflow |
| Who signs the contract and controls the budget? | Determines sales and pricing model | Interview owners, management companies, and relevant resident representatives |
| What is the current visitor workflow? | Establishes the problem and baseline | Map registration, calls, approvals, gate operation, and exceptions |
| Which problems are most frequent or costly? | Helps prioritize MVP | Collect examples and baseline measurements |

## 2. Hardware and connectivity

| Question | Why it matters | Suggested validation |
|---|---|---|
| Which gate-controller models are common in the target estates? | Determines integration feasibility | Survey pilot sites and identify controller models/interfaces |
| Can the controller provide acknowledgement and physical-state feedback? | Determines what GateSecure can accurately report | Review documentation and test hardware |
| What happens when internet or power is lost? | Affects safety and availability | Document each installation's behavior and conduct approved tests |
| What local fallback is acceptable? | May affect access policy and physical risk | Agree with property management and qualified hardware installers |

## 3. Identity, visitor data, and privacy

| Question | Why it matters | Suggested validation |
|---|---|---|
| Which visitor fields are genuinely necessary? | Determines privacy risk and UX | Test the workflow and document purpose for each field |
| When is identity-document verification required? | Affects legal, operational, and storage requirements | Review customer policy and applicable law |
| How long should visitor and access records be retained? | Affects storage, privacy, and investigations | Define purpose-specific retention with appropriate advice |
| Should one person identity be reused across estates? | Can reduce duplication but create cross-estate privacy risks | Define consent, visibility, matching, and access boundaries before implementing |
| Who can see camera feeds and recordings? | Camera access is sensitive and can be abused | Define explicit roles, purposes, audit, and retention |

## 4. Authentication and authorization

| Question | Why it matters | Suggested validation |
|---|---|---|
| Which authentication methods are needed for residents and administrators? | Affects security and user experience | Threat-model account takeover and test user needs |
| How should visitors receive and use temporary credentials? | Affects hardware compatibility and credential sharing | Test selected methods with a simulator and pilot hardware |
| How quickly must revocation take effect? | Depends on controller connectivity and cached credentials | Test online and offline revocation scenarios |
| Which guard exceptions are allowed? | Affects physical security and accountability | Agree on written policy with estate management |
| What extra approval is needed for high-impact changes? | Prevents misuse of administrator privileges | Identify actions that warrant dual control |

## 5. Commercial model

| Question | Why it matters | Suggested validation |
|---|---|---|
| What are the current costs of visitor operations and access equipment? | Establishes a comparison baseline | Interview customers and collect realistic cost estimates |
| Which pricing unit is easiest to procure: estate, household, or access point? | Affects packaging and predictable revenue | Test pricing concepts with prospective buyers |
| Who pays for hardware and installation? | Affects margin and deployment risk | Compare partner-installed and customer-supplied options |
| What support level do customers expect? | Affects operating costs | Discuss response expectations and failure ownership |

## 6. Pilot readiness checklist

Before a physical pilot, confirm:
- [ ] A named property owner or authorized manager has approved the pilot.
- [ ] Current workflows and baseline measures are documented.
- [ ] The selected controller and its failure behavior are understood.
- [ ] Resident, guard, and administrator roles are agreed.
- [ ] The visitor data fields and retention rules are approved.
- [ ] Guard exceptions and manual override procedures are documented.
- [ ] Emergency egress and physical safety have been reviewed by qualified parties.
- [ ] Revocation has been tested, including offline conditions where applicable.
- [ ] Audit records do not expose credentials or unnecessary personal data.
- [ ] Pilot success criteria and rollback procedures are agreed.
- [ ] Users know how to report errors and obtain assistance.

## Working rule

If an assumption affects safety, authorization, privacy, cost, or the core architecture, validate it before treating it as a fixed requirement.
