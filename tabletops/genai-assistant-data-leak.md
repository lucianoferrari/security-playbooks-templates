# Tabletop: GenAI Assistant Leaks Customer Data

**Audience:** Executive team + Product + Engineering leadership · **Duration:** 75 minutes · **Facilitator:** {{NAME}} · **Scribe:** {{NAME}}

## Objectives

- Test whether the organization can contain an AI feature quickly (kill switch, feature flag, tool disable)
- Clarify ownership of AI incidents between Security, Product, Engineering, Legal, and the AI governance committee
- Surface gaps in AI system inventory, logging, and vendor contracts

## Setup (read aloud, 3 min)

Six months ago {{COMPANY}} launched {{ASSISTANT NAME}}, a GenAI assistant for customers. It answers account questions using retrieval over customer data, and it can perform two actions through tools: update contact details and open a support ticket. It runs on a third-party model provider under a commercial agreement. It went through a security review before launch.

---

## Inject 1 — Monday 10:20 a.m. (10 min)

> A customer posts a screenshot on social media: they asked the assistant a routine question and the response included another customer's name, email address, and partial account details. The post is gaining traction. Support has received two similar complaints over the weekend that were closed as "AI being weird."

**Discussion prompts**
- Who owns this incident right now: Security, Product, Engineering, or the AI governance committee?
- Do you turn the assistant off? Who has the authority, and how long does it take? Is there a kill switch or does it require a deployment?
- What do you say publicly in the next hour, if anything?

**Decisions to record:** Incident owner · Assistant disabled / degraded / left running (by whom) · Holding statement

---

## Inject 2 — Monday 1:00 p.m. (15 min)

> Engineering traces the issue: the retrieval index is shared across all customers and relies on the model to "only use documents for the current customer." A change three weeks ago to improve answer quality widened the retrieval window. Logs show the assistant returned other customers' data in roughly 0.4% of conversations since then — about 1,900 conversations. Full prompts and responses were logged, so the exposure can be enumerated.

**Discussion prompts**
- Is this a data breach? Who decides, and what regulators and contracts are in play?
- 1,900 conversations: how do you determine which customers' data was shown to whom?
- The change was reviewed and approved. What failed: the review, the architecture, the test suite, or the assumption that the model enforces authorization?
- Does the model provider need to be notified under contract? Did they retain any of this data?

**Decisions to record:** Breach determination · Notification scope and owner · Root cause statement · Provider notification

---

## Inject 3 — Tuesday 9:00 a.m. (15 min)

> While reviewing logs, the team finds a second issue: a security researcher had been probing the assistant for two weeks. In one session they embedded instructions in their own account's "notes" field; when a support agent later asked the assistant to summarize that customer, it followed the embedded instruction and opened a support ticket containing text the researcher chose. The researcher has now emailed asking about a bug bounty.

**Discussion prompts**
- This is indirect prompt injection reaching a tool action. How serious is it compared to the data leak, and why?
- Do you have a responsible-disclosure policy and a way to respond to the researcher today?
- The assistant was "reviewed before launch." Did the review test for this? Who would know?
- What is the blast radius of the ticket-creation tool? What *could* it have done?

**Decisions to record:** Researcher response owner · Tool permissions reviewed · Scope of re-review

---

## Inject 4 — Thursday (10 min)

> Customer notifications have gone out. A regulator has requested documentation of how the AI system was governed: risk assessment, testing evidence, approval records, and monitoring. The CEO has asked whether every other AI feature in the company has the same problem — and nobody can say how many there are.

**Discussion prompts**
- What can you actually produce for the regulator today? What is missing?
- How do you answer the CEO's question, and how long would a real answer take?
- Do you re-launch the assistant? Under what conditions and who approves?

**Decisions to record:** Evidence package owner · AI inventory action · Re-launch criteria and approver

---

## Debrief (20 min)

1. How long did it take, in the scenario, to disable the feature? Is that realistic?
2. Who owned the incident, and was that clear at the start or only by inject 3?
3. Did anyone know whether the model provider retains data, or what the contract says?
4. Could you have enumerated exposure without the full logs? Should those logs exist in that form?
5. Does a current inventory of AI systems exist?

## Controls this exercise typically produces

- Feature flag / kill switch for every AI feature, with named owners who can use it
- Tenant-aware authorization enforced in the retrieval layer, never delegated to the model
- Least-privilege, per-user credentials for agent tools; confirmation for consequential actions
- AI system inventory with risk tier and owner
- Adversarial regression tests (including indirect injection) run on every prompt, model, or retrieval change
- Clear incident ownership for AI features, documented in the IR plan
- Model-provider contract review: retention, training, breach notification

Related: [GenAI incident playbook](../playbooks/genai-security-incident-playbook.md) · [LLM application security review checklist](../templates/llm-application-security-review-checklist.md)
