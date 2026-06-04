# ADR 0001: Runtime Guardrails And Deterministic Approval Gates

## Status

Accepted for hackathon prototype.

## Context

AutoApprove AI handles software procurement and compliance review. The workflow may process vendor trust pages, privacy policies, subprocessors, employee software requests, source-code exposure descriptions, customer-data descriptions, and draft vendor follow-up messages.

This creates three security risks:

1. Vendor evidence is untrusted input and may contain prompt injection.
2. The model may recommend approval without enough evidence.
3. Tools may create external side effects if email or ticket actions are not controlled.

The hackathon also rewards resilience. The system must keep moving when models, tools, documents, or guardrails fail, but it must not silently approve high-risk software when safety controls are degraded.

## Options

### Option A: LLM-Only Policy Review

Use the model to read evidence and decide whether the request should be approved.

Pros:

- Fast to prototype.
- Minimal code.

Cons:

- Weak auditability.
- Easy to approve without evidence.
- Vulnerable to prompt injection in vendor pages.
- Poor fit for the hackathon's guardrail scoring criteria.

### Option B: Akto / Gateway Guardrails Only

Attach guardrails to LLM and MCP traffic and rely on them for safety.

Pros:

- Strong runtime detection for prompt injection, leakage, and unsafe actions.
- Clear TrueFoundry integration story.

Cons:

- Generic guardrails do not know AutoApprove's business rule: no evidence, no approval.
- Guardrail outages need domain-aware degradation.
- Approval logic still needs deterministic checks.

### Option C: Layered Controls

Use TrueFoundry AI Gateway and Akto-style runtime guardrails for traffic inspection, and implement deterministic approval gates in AutoApprove code.

Pros:

- Strong security story.
- Clear separation between generic runtime security and domain approval policy.
- Better resilience under partial failures.
- Easy to demo: prompt injection is blocked by guardrails; unsupported approval is blocked by deterministic gates.

Cons:

- Requires more structure in evidence and decision objects.
- More up-front design work.

## Decision

Use Option C.

AutoApprove AI will use:

- **TrueFoundry AI Gateway** for model routing, fallback, and gateway-level observability.
- **Akto / runtime guardrails** at LLM input, LLM output, MCP pre-tool, and MCP post-tool hooks.
- **Deterministic approval gates** in application code for evidence completeness, citation requirements, trusted-source status, human approval requirements, and final decision validity.

## Consequences

- A model response cannot directly become an approval.
- Every final decision must pass a structured validator.
- Tool results must carry provenance and guardrail status before they can be used as evidence.
- If guardrails are unavailable during a required stage, the workflow can continue, but the final decision must downgrade to `Needs Security Review`.
- External communication remains a draft-only action in the MVP unless explicit human approval is added later.

