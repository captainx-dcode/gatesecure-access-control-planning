# 05 — Planning Exit Criteria

**Purpose:** Prevent premature coding before the project has a sufficiently clear problem, scope, risk posture, and path into requirements analysis.

Planning is complete only when the project owner reviews the evidence below and explicitly approves the next phase. An unchecked item is not automatically satisfied.

## 1. Planning completion checklist

### Problem and business

- [ ] Problem statement reviewed and approved.
- [ ] Initial target customer segment is explicitly selected or marked as an unvalidated hypothesis.
- [ ] Customer discovery plan exists and includes a way to test/falsify the market hypotheses.
- [ ] Primary user, buyer, approver, operator, and affected data subjects are identified as far as currently known.
- [ ] Value proposition is distinguished from assumptions about willingness to pay.
- [ ] Success outcomes are identified; targets still requiring research are marked as pending.

### Scope and feasibility

- [ ] MVP scope, exclusions, and deferred features are documented.
- [ ] Physical access, identity, authentication, authorization, enforcement, audit, and administrative responsibilities are distinguished.
- [ ] Real hardware use is prohibited until safety and integration requirements are reviewed.
- [ ] Outage and emergency scenarios are listed for requirements analysis.
- [ ] Hardware/vendor compatibility is treated as an open feasibility question, not an assumption.

### Security, privacy, risk, compliance

- [ ] Initial assets, threat scenarios, and risks are documented.
- [ ] Risk owners and treatment approach are identified for high-priority risks.
- [ ] Preliminary data inventory has been reviewed for unnecessary collection.
- [ ] Privacy/legal applicability questions are recorded.
- [ ] Proposed standards are mapped to actual project needs; inapplicable standards are not claimed.
- [ ] Secret handling and repository hygiene rules are documented.
- [ ] Initial trust boundaries and security principles are agreed.

### Delivery and governance

- [ ] Secure SDLC phases and expected artifacts are documented.
- [ ] Decision log and change-control process are ready.
- [ ] Repository visibility has been confirmed by the owner.
- [ ] Planning documents have been reviewed for contradictions and unsupported claims.
- [ ] Open questions are assigned to an owner or scheduled for requirements analysis.
- [ ] Project owner approves transition to Requirements Analysis.

## 2. Planning deliverables

Minimum deliverables:

1. Product charter / product description.
2. Planning work register and initial risk register.
3. Preliminary data inventory and privacy questions.
4. Secure SDLC and standards/methodology proposal.
5. Planning exit checklist.
6. A documented list of open decisions and assumptions.

The following are normally developed in the next phase rather than guessed during planning:

- Detailed functional requirements.
- Detailed non-functional requirements and numeric service targets.
- User stories and acceptance criteria.
- Data dictionary and approved retention schedule.
- Detailed threat model and data-flow diagrams.
- Detailed architecture and technology decisions.
- API contracts and database schema.
- Final security test plan and CI/CD quality gates.

## 3. Approval record

- **Planning decision:** Pending
- **Approver:**
- **Date:**
- **Conditions or unresolved risks:**
- **Authorized next phase:** Requirements Analysis / Not approved
- **Review date:**

## 4. First tasks after approval

1. Conduct stakeholder interviews and record evidence.
2. Convert validated workflows into use cases and abuse cases.
3. Draft and prioritize functional and non-functional requirements.
4. Define requirement IDs and traceability to risks, controls, and tests.
5. Validate data purposes and privacy/legal obligations.
6. Review requirements with security, operations, and relevant hardware stakeholders.
7. Baseline the requirements before secure design begins.
