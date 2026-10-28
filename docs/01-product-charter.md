# 01 — Product Charter and Description

**Document status:** Draft for planning  
**Version:** 0.1  
**Project:** GateSecure Access Control  
**Owner:** Product Owner / Project Lead (to be named)  
**Reviewers:** Software Engineering, Security, Privacy/Legal, Operations, representative customers (to be identified)

## 1. Executive description

GateSecure is a proposed physical-access Identity and Access Management (IAM) platform for managing identities, credentials, household or organizational relationships, access policies, and auditable access decisions for physical gates and doors.

The platform's central purpose is to decide whether a person is authorized to perform a particular action at a particular access point under defined conditions, then securely communicate an approved decision to a compatible enforcement controller. It should preserve a traceable record of the decision and distinguish a command being issued from the physical gate or door actually opening.

The initial market hypothesis is managed residential estates and apartment communities in Kenya. This segment is a starting point for customer discovery, not a validated market selection. Commercial property and enterprise use may be considered later.

## 2. Problem statement

Residential estates and apartment communities need to manage residents, household members, domestic workers, visitors, contractors, and other people who may request access to shared gates and doors. Permissions can change over time and may differ by access point, direction of travel, schedule, household relationship, or approval status.

Where identity records, visitor approvals, access devices, and physical controllers are managed through fragmented or manual processes, the organization may struggle to enforce consistent permissions, revoke access reliably, investigate incidents, and demonstrate who approved access and why.

The project will investigate whether these problems are frequent and costly enough in the target market to justify a dedicated solution. No claim about their prevalence or customers' willingness to pay is considered confirmed until supported by research.

## 3. Core product objective

Design and eventually implement a secure, privacy-conscious, auditable IAM system that grants physical access only when a request satisfies defined authentication, authorization, and operational safety requirements.

## 4. Secondary objectives

1. Support a clear identity and credential lifecycle, including enrollment, changes, suspension, revocation, and deactivation.
2. Represent household or tenant relationships and delegated authority without granting unnecessary administrative privileges.
3. Apply access rules by identity, household/tenant, access point, requested action, schedule, and applicable conditions.
4. Support visitor access through an explicit approval and expiry workflow.
5. Record access requests, authentication outcomes, authorization decisions, policy references, administrative changes, controller acknowledgements, and confirmed physical outcomes when sensors make them available.
6. Make access failures, unavailable controllers, and incomplete revocation visible to authorized operators.
7. Minimize personal-data collection and provide configurable access restrictions and retention controls.
8. Design for integration with compatible physical access hardware without assuming all controllers are interchangeable.
9. Provide a maintainable and testable software foundation suitable for a learning prototype and possible future commercial evaluation.

## 5. Intended users and stakeholders

| Stakeholder | Likely needs / concerns | Status |
|---|---|---|
| Estate/property manager | Oversight, user administration, reports, exception handling | Hypothesis to validate |
| Primary tenant / household administrator | Manage household members and approved visitors | Proposed user role |
| Resident / household member | Convenient, reliable access within assigned permissions | Proposed user role |
| Child or dependent | Restricted access appropriate to policy and guardianship arrangements | Proposed scenario; policy needs research |
| Domestic worker / contractor | Access limited to approved locations, tasks, and times | Proposed user role |
| Visitor / delivery person | Clear, time-limited access process | Proposed user role |
| Security guard / gate operator | Quick verification, clear instructions, safe exception handling | Hypothesis to validate |
| Hardware installer / access-control vendor | Safe, documented integration with supported equipment | Partner to investigate |
| Data controller / processor roles | Defined responsibility for personal-data processing | Legal and operational roles to determine |
| Emergency responders | Safe and lawful emergency access procedures | Requires stakeholder and safety review |

## 6. Initial scope hypothesis

### In scope for discovery and MVP planning

- Identity records and account status.
- Credential registration and revocation.
- Household/tenant grouping and delegated administration.
- Access requests for pedestrian and vehicle gates, including entry and exit as supported by the eventual hardware.
- Policy-based authorization by access point, action, schedule, and role/relationship.
- Visitor invitations, approval, validity windows, and expiry.
- An auditable decision and administrative event history.
- A defined policy for network/service outages and emergency procedures.
- A simulated access controller for early development and testing.
- Security and privacy requirements, risk tracking, and evidence-based acceptance criteria.

### Candidate features, not yet committed to MVP

- Mobile application and mobile credentials.
- PIN fallback and individual household PINs.
- RFID/NFC or other physical credentials.
- Biometrics.
- CCTV, intercom, television, or broader IoT integrations.
- Gym, pool, and other shared-facility access.
- Property listings, emergency/3D estate maps, and unrelated property-management functions.
- Enterprise directory integration, multi-estate portfolio management, and advanced analytics.

Each candidate feature requires feasibility, security, privacy, cost, and market review before inclusion.

### Out of scope for the planning phase

- Connecting to or operating a real gate, door, lock, relay, or motor.
- Selecting a specific hardware vendor or claiming universal compatibility.
- Collecting real residents' or visitors' personal information.
- Storing real biometric templates.
- Processing payment-card data.
- Claiming legal or regulatory compliance certification.
- Building a production deployment or promising production availability.
- Treating automated access decisions as a replacement for physical safety controls or emergency release mechanisms.

## 7. Product principles

1. **Deny by default:** Requests are denied when required identity, policy, or authorization information is missing or invalid, subject to separately defined emergency and life-safety procedures.
2. **Least privilege:** Users and services receive only the permissions necessary for their roles.
3. **Separate authentication from authorization:** A valid credential does not automatically imply permission to use every access point.
4. **Server-side enforcement:** Client-supplied identity, tenant, role, or access-point values must not be trusted without validation against authoritative records.
5. **Explicit trust boundaries:** Application services, controllers, and physical equipment have separate responsibilities and security controls.
6. **Privacy by design and default:** Collect the minimum information needed, define purposes, limit access, and establish retention rules.
7. **Auditable decisions:** Record who/what requested access, the policy decision, relevant approvals, and enforcement outcomes without logging secrets.
8. **Resilience with explicit trade-offs:** Outage behavior must be designed and tested; fail-open or fail-closed behavior must not be chosen casually.
9. **Safe physical operation:** Software must not bypass certified controller safety features, obstruction detection, emergency release, or applicable installation requirements.
10. **Evidence over claims:** Security, usability, and compliance-supporting claims must be backed by test results, documented procedures, or qualified assessment.

## 8. Success definition

Success is not merely a gate opening when a recognized person approaches. Success means the system can enforce intended policy correctly, reject unauthorized requests, preserve useful evidence, protect personal data, and behave predictably under failure.

Provisional success measures to turn into testable requirements later:

| Outcome | Proposed measure | Target-setting status |
|---|---|---|
| Correct authorization | All approved test cases allow only policy-authorized requests; all defined negative cases deny | Thresholds and test suite to be defined in requirements analysis |
| Tenant isolation | Cross-household/tenant access attempts are rejected in all defined tests | Mandatory security acceptance criterion to formalize |
| Revocation | Revocation is propagated or explicitly reported as pending/unconfirmed at each relevant controller | Timing target depends on architecture and hardware |
| Auditability | Every test access request has a correlated decision record; enforcement outcome is separately represented | Required; schema and completeness criteria to define |
| Privacy | Each collected data field has a documented purpose, access rule, and retention/disposal decision | Data inventory must be approved |
| Resilience | Network, power, controller, and service failures follow documented behavior | Failure scenarios and thresholds to define |
| Usability | Representative users complete core tasks with measured completion time and error rate | Baseline and target to establish through research |
| Business value | Customer discovery identifies a repeated high-impact problem and a plausible buyer/budget | Evidence required before product-market claims |
| Maintainability | Automated tests, dependency review, documented setup, and reproducible development environment | Quality gates to define before implementation |

No numerical performance, adoption, revenue, or compliance target is approved yet.

## 9. Business and governance hypotheses

- Property managers may value reduced manual administration and better visibility into access permissions.
- Estate operators may need stronger evidence of visitor approvals, access changes, and incident timelines.
- Reliable revocation and detection of stale permissions may be a differentiator.
- Hardware compatibility and installation cost may determine commercial viability.
- Data protection and responsible handling of access histories may influence purchasing decisions.
- Customers may prefer integration with existing hardware over full hardware replacement.

These hypotheses must be tested through interviews, competitor analysis, workflow observation, and a controlled prototype evaluation.

## 10. Assumptions and constraints

### Assumptions to validate

- The initial target market is managed residential estates/apartment communities in Kenya.
- A simulated controller can be used before real hardware integration.
- The system will eventually need multiple identities, access points, and roles.
- Some installations may experience internet or power outages.
- The product may need to coexist with third-party access-control equipment.

### Constraints

- No real personal data in development/test environments.
- No secrets in source control.
- No real-hardware actuation during planning and early simulation.
- Hardware and safety behavior depend on the selected installation.
- Applicable legal duties depend on actual processing, jurisdiction, customer role, and deployment.
- Scope must be kept small enough to validate the core IAM and authorization model before adding broad IoT features.

## 11. Project approach and next phase

This project follows a risk-driven Secure SDLC. The planning phase defines the problem, objectives, scope hypotheses, stakeholders, data concerns, standards, risks, and success criteria.

The next phase is **Requirements Analysis**. It will convert validated stakeholder needs into prioritized, uniquely identified, testable functional requirements, non-functional requirements, abuse cases, data requirements, acceptance criteria, and traceability links. Architecture and implementation choices should follow those requirements rather than precede them.

## 12. Open decisions

- Which customer segment has the strongest validated need and purchasing authority?
- Which authentication methods belong in the MVP?
- Which controller/hardware interfaces can be supported safely and affordably?
- What is the required behavior during network, power, and central-service outages?
- Who is the data controller and who is the processor in each deployment model?
- What data is strictly necessary for visitor approval and identity assurance?
- What retention periods are justified for access events and visitor data?
- What role, household, and delegation rules are legally and operationally appropriate?
- What service availability, response-time, and revocation targets are needed?
- What pricing and support model is commercially viable?

These are not silently resolved by this charter.
