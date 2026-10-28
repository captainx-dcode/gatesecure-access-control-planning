# 03 — Preliminary Data Governance and Inventory

**Status:** Preliminary planning inventory; not an approved data schema or legal assessment.

## 1. Purpose

Identify likely data categories before implementation and ask why each category is needed, who supplies it, how it is used, who can access it, where it is stored, how it is protected, and when it is deleted.

The inventory follows data minimization: a field is not collected merely because it may be useful someday. Each field requires a defined purpose and an approved necessity decision.

## 2. Preliminary data inventory

| Data category | Possible fields/examples | Likely source | Purpose | Sharing/access | Storage/retention decision |
|---|---|---|---|---|---|
| Identity/account | Internal user ID, display name, account status | User, authorized administrator, approved property system | Identify an account and manage its lifecycle | Authorized administrators; relevant access services | Define minimal fields, correction process, and retention |
| Household/tenant relationship | Household ID, membership, relationship category, effective dates | Primary tenant, property manager, verified source where appropriate | Scope permissions and delegated authority | Only authorized household/property administrators and policy service | Define validity, review, and removal when relationship ends |
| Contact details | Email or phone, only if needed | User or authorized administrator | Notifications, account recovery, invitation workflow | Restricted support/notification components | Avoid collecting both if one is sufficient; define deletion |
| Credential metadata | Credential ID, type, status, issue/expiry/revocation timestamps | Enrollment process | Recognize and revoke registered credentials | Authentication service and authorized administrators | Do not store secrets in logs; define secure storage and revocation |
| Authentication secrets | PIN verifier, password verifier, cryptographic credential material where applicable | User/device enrollment | Verify credential possession or knowledge | Highly restricted authentication component | Never store plaintext passwords/PINs; use appropriate salted password hashing or secure credential design |
| Access policy | Role, access point, permitted action, schedule, conditions | Authorized administrator/policy workflow | Decide whether an access request is permitted | Authorization service and approved administrators | Version policies and record changes |
| Visitor invitation | Invitation ID, inviter, access scope, validity window, status | Authorized resident or operator | Time-limited visitor access | Inviter, relevant operator, authorization service | Collect minimum visitor information; expire and delete per approved policy |
| Access request/event | Event ID, identity/credential reference, access point, action, time, decision, reason code | System-generated | Operations, investigations, audit | Restricted operations/security roles | Retention period must be justified and configurable where appropriate |
| Enforcement event | Controller ID, command reference, acknowledgement, sensor-confirmed state if available | Controller/integration service | Distinguish decision, command, and physical outcome | Operations/security roles | Preserve correlation without treating command as proof of opening |
| Administrative audit | Actor, action, target, timestamp, outcome, reason | System-generated | Accountability and change investigation | Restricted auditors/security administrators | Protect against alteration; never log reusable secrets |
| Device/controller inventory | Device ID, type, firmware/version, connectivity state, integration metadata | Installer, controller, administrator | Manage integrations and operational risk | Engineering/operations | Avoid unnecessary network or location exposure in public documentation |
| Security telemetry | Failed attempts, rate-limit events, controller disconnects, integrity alerts | System-generated | Detect abuse and investigate incidents | Restricted security/operations roles | Minimize personal data; define alert and retention rules |
| Biometric data (future candidate) | Template or match result, if ever selected | Biometric device/provider | Possible identity verification | Not approved; highly restricted if ever justified | Excluded from MVP planning by default pending necessity, legal, privacy, spoofing, and vendor assessment |
| CCTV/image data (future integration) | Video or image references | Separate camera system | Potential incident investigation | Separate authorization and governance required | Out of initial scope; do not copy video into IAM by default |
| Payment data | Card/payment credentials | Not needed for current access objective | None identified | None | Out of scope; do not collect |

This table is a hypothesis inventory. The source, purpose, lawful basis, controller/processor roles, exact fields, retention, hosting location, and sharing arrangements must be confirmed for the chosen deployment model.

## 3. Data lifecycle questions

For every approved field or data category, answer:

1. **Need:** What business/security purpose requires it?
2. **Source:** Who supplies it, and how is accuracy checked?
3. **Authority:** Who is permitted to create, view, change, export, or delete it?
4. **Use:** Which components consume it, and for which decisions?
5. **Sharing:** Which vendors, property operators, or third parties receive it, and why?
6. **Storage:** Which environment and region store it? Is it encrypted and backed up?
7. **Retention:** What event or period triggers deletion or anonymization?
8. **Rights and requests:** How will applicable access, correction, objection, deletion, or other data-subject requests be handled?
9. **Audit:** What evidence records access to or changes in sensitive data?
10. **Breach response:** How is unauthorized access detected, assessed, escalated, and documented?

## 4. Preliminary data protection rules

- Use synthetic identities and access events in development, tests, demos, and public examples.
- Do not collect identity-document numbers, home addresses, biometrics, or visitor photographs by default.
- Do not place PINs, passwords, tokens, API keys, private keys, credential material, or full personal records in logs.
- Use appropriate password hashing (for example, Argon2id or another reviewed password-hashing scheme) for passwords; plain SHA-256 is not appropriate for password storage.
- Treat PINs as low-entropy secrets: use rate limiting, attempt controls, secure verification, expiry/rotation rules where appropriate, and avoid storing them in plaintext.
- Protect data in transit and at rest using appropriately configured, maintained cryptography and managed keys.
- Separate application logs from audit events where their purposes and access requirements differ.
- Restrict access to logs because access histories can reveal household routines.
- Define backup retention and deletion; deleting a record from the main database does not necessarily remove it from backups immediately.
- Do not claim that encryption alone makes processing lawful or compliant.
- Do not use real residents' data without a documented purpose, authority, appropriate notices, safeguards, and approvals.

## 5. Kenya privacy and legal review

The Kenya Data Protection Act, 2019 and applicable regulations/guidance are important starting points if the product processes personal data in the Kenyan context. Applicability depends on the deployment, roles, processing purposes, and other facts.

Before a real pilot, determine:
- Who acts as data controller and/or data processor.
- The lawful basis and purpose for each processing activity.
- Whether a Data Protection Impact Assessment (DPIA) is required, including whether high-risk processing is likely.
- Whether biometric or systematic monitoring features are necessary and proportionate.
- Notice, consent where relevant, data-subject rights, retention, security, breach response, processor contracts, and cross-border transfer requirements.
- Whether registration or other obligations apply to the relevant parties.

Official starting points:
- Office of the Data Protection Commissioner (Kenya): https://www.odpc.go.ke/
- Kenya Data Protection Act, 2019: https://kenyalaw.org/kl/fileadmin/pdfdownloads/Acts/2019/TheDataProtectionAct__No24of2019.pdf

This document is not legal advice. Obtain qualified privacy/legal review before real-world deployment.

## 6. Approval gate

No personal-data field is approved solely because it appears in this draft. The data inventory must be reviewed with product, engineering, operations, and privacy/legal stakeholders before requirements are baselined.
