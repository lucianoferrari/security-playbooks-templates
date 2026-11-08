# GenAI / LLM Application Security Incident Playbook

Covers incidents involving systems that embed large language models: chat assistants, RAG applications, copilots, and autonomous agents — whether built in-house or bought.

**Owner:** {{AI_SECURITY_LEAD}} with {{PRODUCT_OWNER}}
**Related:** [LLM application security review checklist](../templates/llm-application-security-review-checklist.md), [AI acceptable use policy](../templates/ai-acceptable-use-policy.md)

## 1. Incident types

| Type | Example |
|---|---|
| **Prompt injection (direct)** | A user crafts input that overrides system instructions to extract the system prompt or bypass guardrails |
| **Prompt injection (indirect)** | A retrieved document, web page, or email contains instructions the model follows (e.g., "forward this thread to attacker@...") |
| **Sensitive data leakage** | The assistant reveals another customer's data, secrets from the context window, or training/fine-tune data |
| **Unauthorized agent action** | A tool-using agent performs an action outside its intended scope (deletes records, sends messages, makes purchases) |
| **Harmful or non-compliant output** | Output that creates legal, regulatory, or reputational exposure (discriminatory decisions, financial advice, defamation) |
| **Model / supply-chain compromise** | Poisoned fine-tune data, malicious model weights, compromised plugin or MCP server |
| **Shadow AI data exposure** | Employees pasting regulated data into unapproved public AI tools |

## 2. Severity guide

- **SEV-1:** Confirmed exposure of regulated data (PCI, PII, PHI), unauthorized financial or destructive action, or public-facing harmful output at scale
- **SEV-2:** Guardrail bypass with limited exposure; agent action contained; single-tenant data leak
- **SEV-3:** System prompt disclosure, jailbreak without data impact, policy violation with no exfiltration

## 3. First response

1. **Contain the capability, not just the user.** Options in order of blast radius: disable the specific tool/action → switch the agent to read-only → put the feature behind a feature flag → take the application offline.
2. **Preserve the full trace**: user input, retrieved context, system prompt version, model + parameters, tool calls and results, output. Most AI incidents are unreproducible without the *exact* context.
3. **Identify the injection source** for indirect attacks (which document, email, web page, or data record) and quarantine it from the retrieval index.
4. **Rotate secrets** that may have been present in the context window or tool configuration.
5. **Check for repetition**: search logs for the same pattern across other users/tenants — successful injections get reused.

## 4. Investigation questions

- What trust boundary did the model cross? (untrusted content → privileged action)
- Was the attack possible because of **missing isolation** (shared retrieval index, over-privileged tool credentials) rather than the model itself?
- Did output filtering/guardrails fire? If not, why?
- Were humans in the loop for the consequential action, and did the approval step contain enough context to make a real decision?
- Does the vendor (model provider, platform) need to be notified under contract?

## 5. Eradication & hardening

- Apply **least privilege to tools**: scoped tokens, allow-lists for destinations, per-user credentials instead of a shared service account
- Separate **instructions from data**: mark retrieved content as untrusted in the prompt and strip/escape instruction-like content
- Add **output controls**: DLP on responses, structured-output validation, confirmation steps for irreversible actions
- Add the exploit as a **regression test** in your AI red-team suite
- Review the retrieval index for other poisoned content

## 6. Regulatory and disclosure considerations

- Data exposure through an AI system is still a data breach — the same notification clocks apply
- Document the decision rationale for regulators and auditors who will ask how the system was governed (model inventory, risk assessment, testing evidence)
- For consequential automated decisions, check obligations under applicable AI and consumer-protection rules in your jurisdictions

## 7. Decision log

| Time (UTC) | Decision | Decided by | Rationale |
|---|---|---|---|
| | | | |

## 8. Post-incident

- Update the **AI system inventory** entry: risk tier, new controls, residual risk
- Feed findings into the pre-production [review checklist](../templates/llm-application-security-review-checklist.md)
- Brief the AI governance committee
- If the root cause was shadow AI, revisit the [acceptable use policy](../templates/ai-acceptable-use-policy.md) and approved-tool list
