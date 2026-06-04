# Initial Architecture

## System Boundary

The MVP is an agentic workflow, not a full procurement platform. It should produce review packets that a human can inspect and submit into existing tools.

## Components

### Intake Layer

Accepts a structured software request:

- Vendor name.
- Product URL.
- Requesting team.
- Intended use.
- Data types involved.
- Business urgency.
- Whether customer data, source code, credentials, or regulated data are involved.

### Orchestrator

Owns workflow state and step transitions:

- intake validation
- evidence plan
- evidence collection
- policy evaluation
- gap handling
- decision package generation

The orchestrator must persist enough state to resume after a model or tool failure.

### TrueFoundry AI Gateway

Routes model calls and provides fallback behavior. The demo should show a primary model failure and a fallback model continuing the workflow.

### MCP Tool Layer

Candidate tools:

- web search
- web scraper
- document fetcher
- PDF/document parser
- company policy lookup
- vendor evidence cache
- ticket draft tool
- email draft tool

Tools should be read-only by default. Drafting external communication is allowed; sending requires human approval.

### Guardrail Layer

Guardrails should run at multiple points:

- input guardrail for malicious or sensitive requests
- pre-tool guardrail for unsafe arguments
- post-tool guardrail for sensitive outputs, prompt injection, and document poisoning
- output guardrail for unsupported approvals, missing citations, and policy violations

### Decision Engine

The decision engine converts evidence into a structured result:

- decision state
- confidence
- policy checks
- missing evidence
- citations
- audit log
- human review reason

## State Model

Each run should store:

- request metadata
- current step
- collected evidence
- failed tools and retry count
- fallback model usage
- guardrail violations
- final recommendation

## MVP Constraint

Do not build user management, billing, or a full ticketing system in the first prototype.

