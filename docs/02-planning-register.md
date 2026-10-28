# 02 — Planning Work Register

**Status:** In progress  
**Purpose:** Track planning activities, decisions, risks, and unanswered questions before Requirements Analysis.

## 1. Planning work items

| ID | Work item | Purpose / expected evidence | Status |
|---|---|---|---|
| PLAN-001 | Define problem statement | Agreed problem statement and boundaries | Drafted |
| PLAN-002 | Define product objective and outcomes | Product charter with measurable success areas | Drafted; targets pending |
| PLAN-003 | Identify target market and buyer | Customer segments, buyer/user map, evidence from interviews | Open |
| PLAN-004 | Validate market pain points | Interview notes, observed workflows, competitor comparison | Open |
| PLAN-005 | Define MVP boundaries | Approved in-scope, out-of-scope, and candidate features | Draft hypothesis |
| PLAN-006 | Identify stakeholders and trust relationships | Stakeholder map and authority assumptions | Drafted |
| PLAN-007 | Inventory data and purposes | Data inventory with purpose, source, use, sharing, storage, retention, access | Preliminary |
| PLAN-008 | Determine privacy/legal applicability | Processing-role analysis and qualified legal/privacy review as needed | Open |
| PLAN-009 | Identify security and operational risks | Initial risk register with owner, likelihood, impact, treatment | Open |
| PLAN-010 | Select standards and development methods | Standards applicability matrix and rationale | Proposed |
| PLAN-011 | Define preliminary success measures | Measurable security, usability, reliability, and business outcomes | Drafted; thresholds pending |
| PLAN-012 | Define system boundaries | Application, identity service, controller, physical equipment, external systems | Preliminary |
| PLAN-013 | Review outage and emergency assumptions | Failure scenarios and safety stakeholder input | Open |
| PLAN-014 | Decide repository visibility | Private/public decision and release conditions | Recommendation: private |
| PLAN-015 | Approve planning exit | Review all artifacts and authorize Requirements Analysis | Not started |

## 2. Initial risk register

Scales: Likelihood and impact are currently qualitative. Do not treat these labels as a completed quantitative assessment.

| ID | Risk | Initial level | Proposed treatment | Owner |
|---|---|---|---|---|
| RISK-001 | Market need is assumed rather than validated | High | Interview target buyers; document evidence and counter-evidence | Product Owner |
| RISK-002 | Scope expands into too many IoT/property features | High | Freeze an MVP hypothesis; require change review | Product Owner |
| RISK-003 | Incorrect authorization permits cross-household access | High | Define tenant isolation and object-level authorization requirements; test negative cases | Security Lead |
| RISK-004 | Revocation does not reach an offline controller | High | Define bounded offline behavior, acknowledgements, and operational alerting | Engineering/Security |
| RISK-005 | Access logs expose household routines or sensitive personal data | High | Minimize data, restrict access, set retention, assess privacy impact | Privacy Owner |
| RISK-006 | Compromised application can issue direct gate commands | High | Define controller trust boundary, authenticated commands, network restrictions | Security/Engineering |
| RISK-007 | Internet/power outage causes unsafe or unacceptable access behavior | High | Define per-site failure and life-safety requirements; validate with hardware specialists | Operations/Safety |
| RISK-008 | Hardware compatibility is overestimated | Medium/High | Inventory candidate hardware and protocols; prototype only in simulation initially | Engineering |
| RISK-009 | Sensitive secrets or sample personal data enter Git history | High | Private repository, `.gitignore`, synthetic fixtures, secret scanning, rotation plan | Repository Maintainer |
| RISK-010 | Compliance is claimed without validating applicability or controls | High | Map obligations to actual processing/deployment; obtain appropriate review | Product/Privacy |
| RISK-011 | Logging records a command as proof that a gate opened | Medium/High | Separate decision, command acknowledgement, sensor-confirmed state | Engineering |
| RISK-012 | Vendor dependency or unsupported hardware limits deployment | Medium | Document integrations, compatibility tests, and exit strategy | Product/Engineering |

## 3. Decision log

Use this format for future decisions:

- **Decision ID:**
- **Date:**
- **Question:**
- **Options considered:**
- **Decision:**
- **Rationale and evidence:**
- **Security/privacy/business consequences:**
- **Owner/approver:**
- **Revisit trigger:**

### Current decisions / recommendations

| ID | Decision or recommendation | Rationale | Status |
|---|---|---|---|
| DEC-001 | Use `GateSecure Access Control` as the working project name | Existing project context; name may change after branding review | Provisional |
| DEC-002 | Keep repository private during planning and early development | Planning documents may expose architecture assumptions and security decisions; easier to control release | Recommended; owner to confirm |
| DEC-003 | Start with managed residential estates/apartments in Kenya as a market hypothesis | Focuses customer discovery; not yet a validated market choice | Hypothesis |
| DEC-004 | Use a simulated access controller before real hardware | Safer and easier to test policy behavior before actuation | Recommended |
| DEC-005 | Separate identity, authentication, authorization, enforcement, and audit responsibilities | Supports clearer security boundaries and testability | Proposed design principle |
| DEC-006 | Defer detailed technology selection until requirements and feasibility are clearer | Avoids choosing tools before understanding the requirements | Agreed working approach |

## 4. Customer discovery evidence log

For each interview or observation, record only what is needed and obtain appropriate permission. Do not add names, phone numbers, identity documents, or other unnecessary personal information to the repository.

- **Evidence ID:**
- **Date and customer segment:**
- **Role of participant (avoid identifying details unless necessary and authorized):**
- **Workflow or incident described:**
- **Current workaround:**
- **Frequency and impact (reported vs independently measured):**
- **Current solution/vendor, if disclosed voluntarily:**
- **Buying authority/budget signal:**
- **What would falsify our hypothesis:**
- **Follow-up action:**

## 5. Change control

Changes to the problem statement, MVP boundary, data collection, authentication model, hardware control, or compliance assumptions must be recorded in the decision log. A feature request is not automatically accepted into scope. Consider its user value, threat impact, privacy impact, operational risk, cost, and testability before approving it.
