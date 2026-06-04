# Hackathon Requirements

Source context: TrueFoundry Resilient Agents online hackathon, Luma page, and Discord channel notes.

## Hard Requirements

- Use **TrueFoundry AI Gateway** as part of the solution.
- Build a resilient agent that keeps working when providers slow down, model calls break, tools fail, or intermediate outputs are bad.
- Submit through BuilderBase.
- Include a GitHub repository.
- Include a TrueFoundry tenant URL in the format `<tenant-name>.truefoundry.cloud`.
- Include a 3-minute working prototype recording that explains how the system is set up for resilience and how the agent withstands infrastructure failures.

## Strong Scoring Criteria

- AI Gateway setup: routing, fallback, observability, and control.
- MCP Gateway usage: safe tool access, scoped permissions, auth, and auditability.
- Guardrails: checks that block, redact, or validate risky LLM and tool behavior.
- Resilience: retries, fallback behavior, state preservation, and graceful degradation.
- Usefulness: a real problem for a clear user.
- Demo clarity: show what failed, how the agent recovered, and why it worked.

## Failure Modes To Demonstrate

- Rate limits.
- Model or provider outages.
- Slow responses.
- Tool failures.
- Bad intermediate outputs.
- Cascading errors across multiple steps.

## Discord Notes

- Public GitHub repos should be linked in the BuilderBase submission.
- Private repos should invite `sai@truefoundry.com`.
- Free TrueFoundry tier was described as sufficient for the hackathon.
- Every project is expected to be reviewed; winners may take a day or two to announce.

