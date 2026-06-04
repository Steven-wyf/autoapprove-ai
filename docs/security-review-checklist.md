# Security Review Checklist

Use this checklist before merging any implementation PR.

## Secrets

- [ ] No API keys, bearer tokens, OAuth secrets, webhook secrets, SOC 2 PDFs, customer data, or private vendor documents are committed.
- [ ] `.env` and `.env.*` are ignored.
- [ ] `.env.example` contains only empty placeholders.
- [ ] `AGENTS.md` remains ignored.

## Input Validation

- [ ] Every employee software request is parsed through a schema.
- [ ] Vendor URLs must use `https://`.
- [ ] Vendor URLs are normalized and stored with the evidence record.
- [ ] File uploads, if added, are restricted by size, extension, and MIME type.
- [ ] Error messages do not leak secrets or internal stack traces.

## Tool Safety

- [ ] MCP tools are read-only by default.
- [ ] Web fetch tools reject private IP ranges, localhost, and non-HTTP protocols.
- [ ] Email tools only draft messages in the MVP.
- [ ] Any future send or ticket mutation tool requires `human_approved: true`.
- [ ] Tool arguments are validated before invocation.
- [ ] Tool outputs are treated as untrusted until guardrails pass.

## Evidence Safety

- [ ] Every evidence item stores source URL, retrieval timestamp, content hash, extraction method, and guardrail status.
- [ ] Quarantined evidence cannot satisfy required evidence checks.
- [ ] Prompt-injected documents are logged and excluded from model context.
- [ ] Conflicting evidence forces `Needs Security Review`.
- [ ] Missing required evidence prevents `Approve`.

## LLM Safety

- [ ] LLM calls go through TrueFoundry AI Gateway.
- [ ] Model fallback events are recorded in the audit log.
- [ ] LLM input guardrails are applied to user requests and retrieved evidence.
- [ ] LLM output guardrails are applied before the response reaches the decision engine.
- [ ] The model is not allowed to execute tools outside the orchestrator's approved step.

## Decision Safety

- [ ] The final decision object is validated by deterministic code.
- [ ] `Approve` requires complete trusted evidence and citations.
- [ ] If required guardrails fail or are unavailable, final decision is downgraded.
- [ ] External communication is never sent automatically.
- [ ] Every final packet includes decision, evidence table, missing evidence, citations, risks, and audit log.

## Demo Security Cases

- [ ] Prompt-injected vendor page is quarantined.
- [ ] Unsupported approval without citations is blocked.
- [ ] Broken SOC 2 link downgrades decision.
- [ ] Primary model failure triggers fallback.
- [ ] Tool failure creates partial report instead of silent success.

