# Product Brief

## One-Line Pitch

AutoApprove AI is an evidence-gated SaaS procurement and security approval agent that safely advances software intake reviews even when models, tools, vendor sites, or documents fail.

## User

Primary users:

- IT security reviewers.
- Procurement operations.
- Legal or compliance reviewers.
- Engineering managers requesting new software.

## Problem

Enterprise software approvals are slow because security, compliance, legal, and procurement teams must collect and review vendor evidence such as SOC 2 reports, GDPR posture, DPAs, privacy policies, data residency, subprocessors, retention terms, and AI-training policies.

The process is repetitive, but risky. A weak automation can approve software without evidence, miss policy conflicts, leak sensitive data, or get tricked by vendor pages containing prompt injection.

## Proposed Workflow

1. Employee submits a SaaS request.
2. Agent identifies required evidence based on the software category and data sensitivity.
3. Agent gathers vendor evidence through controlled MCP tools.
4. Agent scores the request against a company policy rubric.
5. Guardrails validate evidence, citations, tool arguments, and recommendation text.
6. Agent emits an auditable decision package and drafts follow-up questions if evidence is missing.

## Decision States

- **Approve:** all required evidence exists and no high-risk gaps remain.
- **Conditional Approve:** low-risk use case with limited data access and minor missing evidence.
- **Needs Security Review:** high-risk data, conflicting evidence, failed tools, or insufficient confidence.
- **Reject:** clear policy violation or unacceptable vendor posture.

## Safety Principles

- No evidence, no approval.
- No external communication without human approval.
- No destructive or financial action in the MVP.
- Every decision must include citations and an audit trail.
- Failed tools should degrade the decision state, not be ignored.

