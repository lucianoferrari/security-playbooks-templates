# Tabletop: Critical Vendor Breached

**Audience:** Executive team + Legal + Procurement + IT · **Duration:** 60 minutes · **Facilitator:** {{NAME}} · **Scribe:** {{NAME}}

## Objectives

- Test how quickly the organization can determine *what a vendor has* and *what the vendor can reach*
- Validate contractual notification terms and the practical ability to invoke them
- Decide when a vendor incident becomes our customer-notification obligation

## Setup (read aloud, 2 min)

{{VENDOR}} provides {{SERVICE — e.g., HR/payroll platform, customer-support SaaS, managed IT, marketing automation}} to {{COMPANY}}. They hold {{DESCRIBE DATA}} and have {{DESCRIBE INTEGRATION — e.g., SSO integration, API access to our CRM, VPN into our network}}. They were assessed at onboarding three years ago.

---

## Inject 1 — Thursday 8:00 a.m. (10 min)

> A news article reports that {{VENDOR}} has suffered a "cybersecurity incident" affecting an unspecified number of customers. {{VENDOR}} has not contacted {{COMPANY}}. Their status page says "investigating."

**Discussion prompts**
- Who owns this on our side? Security, the business owner of the vendor relationship, Procurement, Legal?
- What do we actually know about what {{VENDOR}} holds and can access? Who can answer that in the next hour, and from what source?
- Do we proactively contact them? Who, and through what channel?

**Decisions to record:** Internal owner · Data/access inventory source · Vendor contact made

---

## Inject 2 — Thursday 2:00 p.m. (10 min)

> {{VENDOR}} sends a generic notice to all customers: attackers accessed "certain customer environments" via a compromised support credential. They cannot yet say which customers. They recommend rotating any API keys or credentials shared with them. Our integration uses a service account with {{DESCRIBE PRIVILEGES}} in our environment.

**Discussion prompts**
- Do you rotate credentials and cut the integration now, knowing it will break {{BUSINESS PROCESS}}? Who decides, and what is the business impact per day?
- What should we be looking for in our own logs? Does anyone know what "normal" looks like for that service account?
- What does our contract say about notification timelines and our right to information? Who has the contract?

**Decisions to record:** Integration disabled / credentials rotated (Y/N, by whom) · Threat hunt initiated · Contract terms confirmed

---

## Inject 3 — Friday 11:00 a.m. (15 min)

> {{VENDOR}} confirms {{COMPANY}} was among the affected customers. Attackers had access to our tenant for approximately 12 days and exported data including {{DESCRIBE — e.g., employee records / customer contact data / support tickets containing customer information}}. Our own log review finds the service account authenticated from an unfamiliar location on two occasions during that window, but the actions taken are unclear because logging for that integration was minimal.

**Discussion prompts**
- Is this now our data breach? Who determines our notification obligations to employees, customers, and regulators, and what are the clocks?
- What can we say about what the attacker did inside *our* environment? Is "we don't know" acceptable, and to whom?
- Does {{VENDOR}}'s notification satisfy our obligations, or do we notify independently?
- Do you invoke indemnification or other contractual remedies now, or wait?

**Decisions to record:** Breach determination and scope · Notification owner and plan · Legal position with vendor · Logging gap remediation

---

## Inject 4 — Following week (10 min)

> Customers are asking whether their data was affected. The board asks how many other vendors have this level of access and when they were last assessed. The answer, after two days of searching, is "about forty, and we're not sure."

**Discussion prompts**
- What do you tell customers, and how fast can you be accurate?
- What is the honest answer to the board, and what do you ask for?
- Do you keep {{VENDOR}}? What would it take to trust them again?

---

## Debrief (15 min)

1. How long did it take to determine what the vendor holds and can access? Where did that information come from?
2. Did the contract have the notification terms we needed? Could anyone find it quickly?
3. Was the integration credential scoped to what the vendor needed, and was it monitored?
4. Do we have a current inventory of vendors with data access or network/identity integration, with risk tiers and reassessment dates?

## Controls this exercise typically produces

- Vendor inventory with data held, integration type, privileges, risk tier, owner, and last assessment
- Least-privilege, monitored, rotatable credentials for every vendor integration
- Contract clauses: notification within a fixed window, right to audit/information, data-return and deletion
- Pre-agreed decision rights for cutting a vendor integration
- Reassessment cadence by tier (see [vendor questionnaire](../templates/vendor-security-assessment-questionnaire.md))
- Customer-communication template for third-party incidents
