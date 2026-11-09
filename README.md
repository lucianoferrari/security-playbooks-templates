# Security Playbooks & Templates

Practical, ready-to-adapt playbooks, policies, and reporting templates I use when building and running security programs — from incident response to AI governance and board reporting.

Everything here is vendor-neutral and written to be copied into your own wiki or GRC tool and edited. Replace the `{{PLACEHOLDERS}}`, delete what you don't need, and own it.

## Incident response playbooks

| Playbook | Use when |
|---|---|
| [Ransomware response](playbooks/ransomware-response-playbook.md) | Encryption, extortion note, or mass file modification detected |
| [Business email compromise (BEC)](playbooks/business-email-compromise-playbook.md) | Account takeover, payment redirection, or executive impersonation |
| [GenAI / LLM application incident](playbooks/genai-security-incident-playbook.md) | Prompt injection, data leakage through an AI assistant, or an agent taking an unintended action |

## Governance & program templates

| Template | Purpose |
|---|---|
| [CISO first 90 days plan](templates/ciso-first-90-days-plan.md) | Structured assess → prioritize → deliver plan for a new security leader |
| [Board security report](templates/board-security-report-template.md) | One-page-plus-appendix format for board and audit committee updates |
| [AI acceptable use policy](templates/ai-acceptable-use-policy.md) | Employee-facing rules for using GenAI tools with company data |
| [LLM application security review checklist](templates/llm-application-security-review-checklist.md) | Pre-production review for apps that embed LLMs, RAG, or agents |
| [Vendor security assessment questionnaire](templates/vendor-security-assessment-questionnaire.md) | Right-sized third-party risk questionnaire with scoring guidance |

## Tabletop exercises

Four facilitated, 60–90 minute scenarios with timed injects, discussion prompts, decisions to record, and a debrief. Built for executive audiences; each one exercises a playbook or template above. See the [tabletop pack](tabletops/README.md) for how to run them.

| Scenario | Audience |
|---|---|
| [Ransomware during month-end close](tabletops/ransomware-month-end.md) | Executive team |
| [BEC: the redirected payout](tabletops/bec-redirected-payout.md) | Executive team + Finance |
| [GenAI assistant leaks customer data](tabletops/genai-assistant-data-leak.md) | Executive + Product + Engineering |
| [Critical vendor breached](tabletops/vendor-breach.md) | Executive + Legal + Procurement |

## How I use these

- **Playbooks** live in the IR runbook and are exercised at least twice a year using the [tabletop pack](tabletops/README.md). Each one has a *decision log* section because the thing you'll be asked about afterward is *why* you made a call, not just *what* you did.
- **Templates** are starting points. The board report, for example, is deliberately short: directors want risk posture, trend, and asks — not a vulnerability count.
- The **AI** material reflects the governance work I've done inside a regulated fintech and the testing approach behind [AI Risk Inspector](https://youtu.be/0Lm11OSdJnw) and my [Break the Bot](https://lufsec.com) red-teaming workshop.

## Contributing

Issues and PRs are welcome — especially real-world refinements from people who've run these in anger.

## License

MIT — use freely, attribution appreciated.

---

**Luciano Ferrari** · CISSP, CISM, CRISC, C|CISO, C|RAGE · [LinkedIn](https://www.linkedin.com/in/lucianoferrari) · [LufSec](https://lufsec.com) · [YouTube](https://youtube.com/@lufsec)
