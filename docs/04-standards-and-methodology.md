# 04 — Secure SDLC, Standards, Frameworks and Methods

**Status:** Proposed baseline for planning; applicability must be confirmed.

## 1. Development approach

Use an iterative, risk-driven Secure SDLC.
Maintain a lightweight backlog and decision log, but do not skip formal security and privacy checkpoints. Security work is integrated into each phase.

| SDLC phase | Main activities | Required evidence / exit artifact |
|---|---|---|
| 1. Planning | Problem definition, business case hypotheses, scope, stakeholders, data categories, initial risks, repository policy | Approved product charter, planning register, preliminary data inventory, exit review |
| 2. Requirements analysis | Stakeholder interviews, functional/non-functional requirements, abuse cases, privacy requirements, acceptance criteria, traceability | Prioritized requirements baseline, data requirements, acceptance criteria, updated risk register |
| 3. Secure design | Architecture, trust boundaries, data flows, threat model, authorization model, failure modes, privacy design | Architecture decision records, data-flow diagrams, threat model, mitigation plan |
| 4. Implementation | Secure coding, peer review, dependency controls, secrets handling, small changes | Reviewed code, tests, dependency inventory, change history |
| 5. Verification | Unit/integration/system tests, negative authorization tests, SAST, dependency scans, DAST/API testing when available, security review | Test reports, findings, remediation evidence, release decision |
| 6. Release/deployment | Secure configuration, least privilege, migration/rollback plan, deployment verification, operator documentation | Release checklist, configuration baseline, rollback and recovery plan |
| 7. Operations/maintenance | Monitoring, access reviews, incident response, patching, backups, vulnerability management, privacy requests | Operational procedures, incident records, patch evidence, periodic reviews |
| 8. Retirement | Revoke credentials, disable integrations, export/retain records lawfully, delete data and secrets safely | Decommissioning plan and completion evidence |

## 2. Proposed frameworks and standards

Use standards as purposeful references, not as a long list of compliance claims.

### Secure development

- **NIST SP 800-218, Secure Software Development Framework (SSDF):** Proposed primary secure-development process reference.
- **OWASP Application Security Verification Standard (ASVS):** Proposed source for testable web-application security requirements; select a suitable version and verification level during requirements/design.
- **OWASP Top 10:** Awareness and risk communication for common web application risks; not a complete security requirements standard.
- **OWASP API Security Top 10:** Relevant to object-level authorization, authentication, resource consumption, and API inventory risks.
- **OWASP Software Assurance Maturity Model (SAMM):** Optional maturity model if the project later needs structured process improvement.
- **CWE:** Useful vocabulary for classifying software weakness types.

### Risk and security management

- **NIST Cybersecurity Framework (CSF) 2.0:** Useful for organizing governance, identification, protection, detection, response, and recovery outcomes.
- **NIST SP 800-30:** Reference for risk assessment methodology.
- **ISO/IEC 27001:** Possible organizational information-security management reference if the business and customer context justifies it. Following selected controls is not certification.
- **OWASP threat modeling guidance / STRIDE:** Candidate methods for structured threat identification. STRIDE is a modeling aid, not a complete risk-management framework.

### Identity and access control

- **NIST SP 800-63 series:** Reference for digital identity, authentication, and federation concepts where applicable; do not assume every recommendation maps directly to a physical gate.
- **Least privilege, deny by default, separation of duties, and server-side authorization:** Core engineering principles.
- **Zero Trust concepts:** Use as an architectural mindset—explicit verification, least privilege, and assumed breach—not as a claim that the product is “Zero Trust compliant.”

### Privacy and legal

- **Kenya Data Protection Act, 2019**, applicable regulations and current ODPC guidance: Starting point for Kenyan deployments that process personal data.
- **Privacy by design/default and data minimization:** Product design principles.
- **GDPR:** Assess only if the actual organization, people, processing, or territorial scope makes it applicable. Do not include it as a generic compliance claim.
- **PCI DSS:** Not applicable to the current stated scope unless payment-card data or a relevant payment environment is introduced.
- **HIPAA:** Not applicable merely because the product controls doors; assess only if the actual deployment and role bring it within scope.
- **ISA/IEC 62443 and NIST SP 800-82:** Future references only if the scope expands to industrial control/OT environments. Residential gate control is not automatically an OT deployment under these standards.

Official references:
- NIST SSDF: https://csrc.nist.gov/Projects/ssdf
- NIST CSF: https://www.nist.gov/cyberframework
- OWASP ASVS: https://owasp.org/www-project-application-security-verification-standard/
- OWASP API Security: https://owasp.org/www-project-api-security/
- OWASP SAMM: https://owaspsamm.org/
- Kenya ODPC: https://www.odpc.go.ke/
- Kenya Data Protection Act: https://kenyalaw.org/kl/fileadmin/pdfdownloads/Acts/2019/TheDataProtectionAct__No24of2019.pdf

Check current versions during implementation planning; this document does not freeze version numbers.

## 3. Secure engineering principles

1. Security and privacy requirements are documented and testable.
2. Threat modeling begins before detailed architecture is approved and is updated when the design changes.
3. Authentication, authorization, policy administration, controller enforcement, and audit are separate responsibilities.
4. Tenant/household boundaries are enforced server-side for every relevant object and operation.
5. Use least privilege for people, services, database accounts, and controllers.
6. Fail safely according to an explicit per-scenario policy; do not assume “fail open” or “fail closed” is universally correct.
7. Physical safety systems remain independent and authoritative for safety functions.
8. Use secure defaults, validated inputs, parameterized database queries, safe error handling, and appropriate rate limits.
9. Use modern, maintained cryptographic protocols and managed keys; never invent cryptography.
10. Keep secrets out of source control, logs, screenshots, and test fixtures.
11. Record security-relevant decisions without storing credentials or unnecessary personal data.
12. Make audit events tamper-resistant to the degree justified by the deployment and threat model.
13. Treat third-party dependencies, firmware, and hardware interfaces as part of the attack surface.
14. Define a vulnerability-reporting, patching, and incident-response process before production use.

## 4. Threat modeling and risk method

Proposed method:

1. Identify assets and security objectives.
2. Draw data-flow diagrams and trust boundaries.
3. Identify actors, entry points, external dependencies, and privileged operations.
4. Use STRIDE or a comparable method to generate threat scenarios.
5. Rate likelihood and impact using a documented scale.
6. Identify existing controls and gaps.
7. Select mitigations and assign owners.
8. Define tests or other evidence that demonstrate mitigation.
9. Track residual risk and obtain an explicit decision from the appropriate owner.
10. Revisit the model when scope, architecture, hardware, or data processing changes.

Likely assets include identities, credentials, household relationships, access policies, visitor invitations, administrative accounts, audit records, controller commands, and physical safety functions.

## 5. Proposed testing strategy

- **Unit tests:** Policy evaluation, expiry, role boundaries, validation, state transitions.
- **Integration tests:** Identity service, database, controller simulator, audit pipeline.
- **Negative authorization tests:** Cross-household access, privilege escalation, revoked/expired credentials, unauthorized access points/actions.
- **Abuse-case tests:** Replay attempts, brute-force/rate-limit behavior, tampered identifiers, duplicate requests, expired invitations.
- **Reliability tests:** Timeouts, controller disconnects, service/database failures, clock skew, retry behavior.
- **Privacy tests:** Excess data collection, unauthorized access to records, retention/deletion workflows, secrets in logs.
- **Static analysis and dependency checks:** Introduce with the implementation toolchain.
- **Dynamic/API security tests:** Run against controlled test deployments, never against third-party systems without authorization.
- **Hardware safety validation:** Required before any real controller or gate is connected; involve qualified hardware/installation specialists.

## 6. Definition of Done — proposed baseline

A change is not done merely because it runs.

- Acceptance criteria are met.
- Relevant tests pass, including negative authorization tests.
- Code has been reviewed.
- No unresolved critical/high security issue is accepted without documented risk decision and authorized approval.
- Dependency and secret checks are completed as appropriate.
- Logs do not expose secrets or unnecessary personal data.
- Documentation and threat model are updated where behavior or trust boundaries change.
- Failures and rollback behavior are considered.
- Changes are traceable to a requirement, risk, or approved maintenance task.

Exact severity thresholds, exceptions, and CI quality gates will be approved before implementation.
