# Policy Rubric

This is a simple MVP rubric for demo purposes. It should be replaced with a real company policy later.

## Required Evidence

For every SaaS request:

- Vendor security page or trust center.
- Privacy policy.
- Data processing agreement or equivalent terms.
- Subprocessor list.
- Data retention or deletion policy.
- Contact path for security/compliance questions.

For tools handling customer data, source code, credentials, or regulated data:

- SOC 2 Type II or equivalent evidence.
- Encryption in transit and at rest.
- Access control and audit logging posture.
- AI training / data usage policy.
- Data residency statement when relevant.

## Decision Rules

### Approve

All required evidence exists, citations are attached, no high-risk conflicts remain, and guardrails pass.

### Conditional Approve

The use case is low risk, data sensitivity is low, and only non-critical evidence is missing.

### Needs Security Review

Use this when:

- customer data, source code, credentials, or regulated data are involved
- required evidence is missing
- evidence conflicts
- tools failed during collection
- prompt injection or document poisoning was detected
- model output lacks citations or confidence

### Reject

Use this when:

- vendor terms conflict with company policy
- vendor claims unrestricted training on customer data
- required deletion or privacy commitments are absent for high-risk data
- guardrails detect a severe violation that cannot be remediated

## Output Requirements

Every final recommendation must include:

- decision
- summary
- evidence table
- missing evidence
- risk rationale
- citations
- audit log
- human review trigger, if any

