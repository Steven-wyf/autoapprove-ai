# AutoApprove AI

AutoApprove AI is a resilient software procurement and compliance approval agent for the TrueFoundry Resilient Agents hackathon.

When an employee requests a new SaaS tool such as Cursor, Claude, OpenAI, Notion, or Slack, the agent collects vendor trust evidence, checks security and compliance requirements, identifies missing materials, drafts follow-up requests, and produces an auditable approval recommendation.

The project is intentionally scoped around evidence-gated decisions: the agent may recommend approval only when required evidence exists, citations are attached, and guardrails pass.

## Hackathon Fit

- **TrueFoundry AI Gateway:** model routing, fallback, observability, and governed LLM access.
- **MCP Gateway:** controlled access to web search, document fetching, document parsing, policy lookup, ticketing, and email-draft tools.
- **Guardrails:** block unsupported approvals, prompt injection, sensitive-data leakage, unsafe tool arguments, and risky external communications.
- **Resilience:** preserve workflow state and degrade safely when models, tools, vendor sites, or documents fail.

## MVP Scope

The first prototype should support one narrow workflow:

1. Intake a software request.
2. Collect vendor evidence from trusted sources or uploaded documents.
3. Evaluate the request against a company policy rubric.
4. Identify missing evidence and draft vendor follow-up.
5. Produce an auditable decision package:
   - Approve
   - Conditional Approve
   - Needs Security Review
   - Reject

## Non-Goals

- No autonomous purchasing.
- No automatic external email sending without human approval.
- No approval without cited evidence.
- No broad GRC platform in the first prototype.

## Repository Map

- `docs/hackathon-requirements.md` - requirements collected from Luma and Discord.
- `docs/product-brief.md` - product positioning and MVP boundaries.
- `docs/architecture.md` - initial architecture sketch.
- `docs/demo-failure-matrix.md` - resilience scenarios for the 3-minute demo.
- `docs/policy-rubric.md` - initial approval policy model.
- `examples/requests/` - sample software intake requests.
- `examples/vendors/` - sample vendor evidence fixtures.

## Collaboration

This repo starts framework-free on purpose. Add implementation code only after the team agrees on the agent runtime, tool interfaces, and demo path.

