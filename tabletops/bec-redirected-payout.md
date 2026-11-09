# Tabletop: Business Email Compromise — The Redirected Payout

**Audience:** Executive team + Finance/AP leadership · **Duration:** 60 minutes · **Facilitator:** {{NAME}} · **Scribe:** {{NAME}}

## Objectives

- Test the speed of the "stop the money" response
- Validate payment-change verification controls as actually practiced, not as documented
- Clarify notification duties to the affected partner and to insurers/law enforcement

## Setup (read aloud, 2 min)

{{COMPANY}} pays {{VENDORS / MERCHANTS / PARTNERS}} by bank transfer on a regular schedule. The AP team handles bank-detail change requests by email. The CFO is traveling.

---

## Inject 1 — Tuesday 4:10 p.m. (10 min)

> A long-standing partner, {{PARTNER}}, calls their account manager: their expected payout of {{AMOUNT}} did not arrive. AP checks and finds the payment was sent on schedule, to a new bank account that was updated two weeks ago following an email from the partner's finance contact requesting the change.

**Discussion prompts**
- What happens in the next 30 minutes? Who calls the bank, and do they know the fraud line number?
- Who is told, in what order?
- Is the partner's email compromised, or ours? How would you find out?

**Decisions to record:** Bank recall initiated (by whom, when) · Incident declared · Investigation owner

---

## Inject 2 — Tuesday 5:30 p.m. (10 min)

> The bank says the funds left the receiving account within hours; a recall request is filed but recovery is unlikely. The security team finds that the change-request email came from a look-alike domain ({{partner-name.co}} instead of .com). The AP specialist followed the written procedure: she replied to the email to confirm, and received a confirmation.

**Discussion prompts**
- Is this our loss or the partner's? Who has the contractual answer?
- Was the procedure followed? Was the procedure adequate? How do you separate those two questions in front of the AP team?
- Do you notify cyber insurance tonight? Does the social-engineering / funds-transfer coverage have a notice window?

**Decisions to record:** Insurance notified · Legal engaged · Partner communication owner

---

## Inject 3 — Wednesday 9:00 a.m. (10 min)

> Reviewing mailbox logs, security finds that two other vendor bank-change requests were processed in the last 60 days from similar look-alike domains. One payment is scheduled for Friday. Separately, the CFO's assistant reports that the CFO's mailbox has a forwarding rule nobody created, sending copies of all email to an external address.

**Discussion prompts**
- The Friday payment: who stops it, and how do you verify the correct bank details now?
- The CFO's mailbox: what does the attacker know, and for how long? What else did they read?
- Is this now a data-breach notification question (HR data, customer data, contract terms in the CFO's email)?
- Do you report to law enforcement (FBI IC3 or equivalent)? Who files it?

**Decisions to record:** Friday payment held · Scope of mailbox exposure · Breach determination · Law-enforcement report

---

## Inject 4 — Wednesday 3:00 p.m. (10 min)

> {{PARTNER}} has sent a formal letter asking {{COMPANY}} to make them whole for the missed payout and threatening to pause the relationship. The AP specialist is distraught and has asked whether she will be fired. A board member has heard about the loss from the CFO and wants to know whether "this can happen again."

**Discussion prompts**
- What is the position with the partner, and who delivers it?
- What do you say to the AP specialist, and who says it?
- What is the honest answer to the board member?

---

## Debrief (15 min)

1. How many minutes elapsed in the scenario between discovery and the bank being called? What would it be in reality?
2. Does the bank-detail change procedure require an out-of-band callback to a **known, previously recorded** number? Is it followed?
3. Who approves payments above a threshold, and is dual control real or a formality?
4. Did anyone know the insurance notice requirements and the IC3 process without looking them up?

## Controls this exercise typically produces

- Mandatory callback verification to a phone number on file (never from the email) for any payment-detail change
- Dual control for bank-detail changes and payments above a threshold
- Phishing-resistant MFA for finance, executives, and assistants
- Alerting on new mailbox forwarding rules; block external auto-forward
- Look-alike domain monitoring for key partners
- A pre-written, pre-approved communication for partners in this situation
