# Generative AI Acceptable Use Policy

**Policy owner:** {{CISO / AI Governance Committee}} · **Effective:** {{DATE}} · **Review cycle:** Annual · **Version:** 1.0

## 1. Purpose

{{COMPANY}} encourages the responsible use of generative AI (GenAI) tools to improve productivity and customer outcomes. This policy defines how employees, contractors, and partners may use GenAI tools so that we protect customer data, intellectual property, regulatory compliance, and our reputation.

## 2. Scope

Applies to all workforce members and to any use of GenAI tools — including chat assistants, code assistants, image/audio generators, AI features embedded in SaaS products, browser extensions, and autonomous agents — in connection with company work or using company data, devices, or accounts.

## 3. Definitions

- **Approved AI tool:** A tool listed in the AI Tool Register ({{LINK}}) that has passed security, privacy, and legal review and is configured under a company agreement.
- **Public AI tool:** Any consumer or free-tier AI service without a company agreement, where inputs may be retained or used for training.
- **Restricted data:** Customer PII, cardholder data (PCI), financial account data, health data, credentials/secrets, source code of core systems, unreleased financials, M&A information, legal-privileged material, and any data classified Confidential or above.

## 4. Policy

### 4.1 Use approved tools
Use only approved AI tools for company work. Requests for new tools go through the AI intake process ({{LINK}}). Personal accounts on public AI tools must not be used with company data.

### 4.2 Data handling
- **Never** enter Restricted data into a public AI tool.
- Restricted data may be used in approved tools **only** where the tool's register entry explicitly permits that data class.
- Do not upload documents, screenshots, recordings, or code repositories to AI tools unless the tool is approved for that content type.
- Disable training/data-retention features where the tool offers that option; approved enterprise configurations enforce this by default.

### 4.3 Human accountability
- You are responsible for AI-assisted output you use or share. Review for accuracy, bias, confidentiality, and licensing before relying on it.
- AI must not make final decisions that materially affect customers or employees (credit, employment, pricing, fraud determinations) without documented human review, unless the system has been approved for that purpose through the AI risk assessment process.

### 4.4 Code and engineering
- AI-generated code follows the same review, testing, and security scanning as human-written code.
- Do not paste secrets, keys, or production configuration into AI assistants.
- Check license compatibility of AI-suggested code and dependencies.

### 4.5 Customer-facing and external use
- Disclose AI involvement where required by law, contract, or company standards.
- Do not publish AI-generated content under the company name without editorial review.
- Do not create deepfakes, impersonations, or deceptive content.

### 4.6 Building AI systems
Teams building or integrating AI (including agents and RAG systems) must complete the AI risk assessment and the [LLM application security review](llm-application-security-review-checklist.md) before production use, and register the system in the AI inventory.

### 4.7 Prohibited uses
- Entering Restricted data into unapproved tools
- Circumventing safety controls, guardrails, or monitoring
- Using AI to harass, discriminate, or generate unlawful content
- Autonomous agents with access to production systems or funds without approved controls and human-in-the-loop checkpoints

## 5. Roles and responsibilities

| Role | Responsibility |
|---|---|
| All workforce | Comply with this policy; report incidents and suspected misuse |
| Managers | Ensure teams know the approved-tool list; approve business need for new tools |
| Security | Tool reviews, monitoring, incident response, this policy |
| Privacy / Legal | Data-protection and regulatory review of tools and use cases |
| AI Governance Committee | Risk appetite, approvals for high-risk systems, policy exceptions |

## 6. Monitoring and enforcement

Use of AI tools on company systems may be monitored and logged in accordance with the Acceptable Use Policy. Violations may result in disciplinary action up to termination, and in regulatory reporting where required.

## 7. Exceptions

Submit exception requests to {{EMAIL/FORM}}. Exceptions are time-bound, risk-assessed, and approved by the AI Governance Committee.

## 8. Reporting

Report suspected data exposure, harmful output, or policy violations immediately to {{SECURITY_CONTACT}}. Reports made in good faith will not result in retaliation.

## 9. Related documents

- Information Classification Policy · Acceptable Use Policy · Third-Party Risk Policy · Secure Development Standard · AI Risk Assessment Procedure

---

*Acknowledgement: I have read and understood the Generative AI Acceptable Use Policy.*
Name: ______________________ Date: ____________
