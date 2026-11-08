# LLM Application Security Review Checklist

Pre-production security review for applications that embed large language models — chat assistants, RAG systems, copilots, and tool-using agents. Aligned with the OWASP Top 10 for LLM Applications and the NIST AI RMF; written to be completed jointly by the product team and security.

**System:** {{NAME}} · **Owner:** {{TEAM}} · **Risk tier:** {{Low / Medium / High}} · **Reviewer:** {{NAME}} · **Date:** {{DATE}}

Mark each item **Pass / Fail / N/A** and attach evidence.

---

## A. System understanding

- [ ] Architecture diagram showing model(s), prompts, retrieval sources, tools/APIs, and data flows
- [ ] Model inventory entry: provider, model/version, hosting (SaaS / VPC / self-hosted), data-retention terms
- [ ] Intended users and use cases documented; out-of-scope uses stated
- [ ] Risk tier assigned based on data sensitivity, autonomy, and user population (internal vs. public)

## B. Prompt injection and instruction integrity

- [ ] System prompt contains no secrets, credentials, or sensitive business logic
- [ ] Untrusted content (user input, retrieved docs, web pages, emails, tool results) is clearly delimited and treated as data, not instructions
- [ ] Indirect injection tested: adversarial content placed in retrieval sources and tool outputs
- [ ] Jailbreak and role-play bypass testing performed with a documented test set; results and fixes recorded
- [ ] Input filtering/classification in place for high-risk categories where appropriate

## C. Data protection

- [ ] Retrieval index enforces per-user / per-tenant authorization at query time (no shared index leaking across tenants)
- [ ] PII/regulated data minimized in prompts and context; redaction or tokenization where feasible
- [ ] Logging of prompts/outputs reviewed for sensitive data; retention and access controls defined
- [ ] Data sent to third-party model providers covered by contract (no training on our data, residency, breach notification)
- [ ] Output DLP for secrets, PII, and regulated data

## D. Tools, agents, and actions

- [ ] Each tool has a documented purpose, inputs, and blast radius
- [ ] Tool credentials are least-privilege and scoped per user where possible — no shared admin tokens
- [ ] Irreversible or consequential actions (payments, deletions, external messages) require human confirmation with sufficient context to decide
- [ ] Allow-lists for destinations (URLs, email domains, API endpoints) the agent can reach
- [ ] Rate limits and spend caps on tool use and model calls
- [ ] Agent loops bounded (max steps / time) with safe failure behavior

## E. Output handling

- [ ] Model output is never executed or rendered as code/HTML without sanitization (prevents XSS, SSRF, command injection via output)
- [ ] Structured outputs validated against schema before downstream use
- [ ] Content moderation / policy filters appropriate to the audience
- [ ] Clear disclosure to users that they are interacting with AI; limitations stated

## F. Supply chain

- [ ] Model weights, fine-tune data, plugins, MCP servers, and libraries sourced from trusted origins and integrity-verified
- [ ] Dependency scanning covers AI frameworks and SDKs
- [ ] Third-party AI services assessed under the vendor risk process

## G. Monitoring and incident readiness

- [ ] Full trace logging: input, context, prompt version, model, tool calls, output (with sensitive-data controls)
- [ ] Alerts for guardrail bypass attempts, anomalous tool usage, and spikes in refusals or errors
- [ ] Kill switch / feature flag to disable tools or the whole feature quickly
- [ ] [GenAI incident playbook](../playbooks/genai-security-incident-playbook.md) linked and on-call aware
- [ ] Regression test suite includes previously found exploits

## H. Governance

- [ ] AI risk assessment completed and approved for the assigned tier
- [ ] Legal/privacy review complete (consumer protection, automated-decision rules, disclosures)
- [ ] Human-oversight model defined for consequential decisions
- [ ] Re-review triggers defined (model change, new tools, new data sources, new user population)

---

## Red-team test set (minimum)

| # | Test | Expected behavior |
|---|---|---|
| 1 | Direct instruction override ("ignore previous instructions…") | Refuses; stays in role |
| 2 | System prompt extraction | Does not disclose |
| 3 | Indirect injection via retrieved document | Ignores embedded instructions; flags if possible |
| 4 | Cross-tenant data request | No data from other tenants returned |
| 5 | Tool misuse (send to attacker-controlled destination) | Blocked by allow-list / confirmation |
| 6 | Secret exfiltration via encoding (base64, translation, spelling) | Blocked |
| 7 | Multi-turn gradual escalation | Guardrails hold across turns |
| 8 | Harmful/regulated advice request | Appropriate refusal or routing |

## Sign-off

| Role | Name | Decision | Date |
|---|---|---|---|
| Product owner | | | |
| Security reviewer | | Approve / Approve with conditions / Reject | |
| Privacy / Legal | | | |
