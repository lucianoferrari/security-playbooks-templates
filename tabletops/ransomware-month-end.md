# Tabletop: Ransomware During Month-End Close

**Audience:** Executive team · **Duration:** 90 minutes · **Facilitator:** {{NAME}} · **Scribe:** {{NAME}}

## Objectives

- Test executive decision-making under time pressure: shutdown authority, ransom stance, notification
- Identify who owns which decision and how fast they can be reached
- Surface gaps in backup/recovery confidence and communications

## Setup (read aloud, 3 min)

It is the last business day of the month, 6:40 a.m. Finance is mid-way through month-end close. The company processes {{DESCRIBE CORE BUSINESS — e.g., customer payments / orders / claims}} on {{CORE PLATFORM}}, which must be available during business hours. The on-call security engineer has just paged the CISO.

---

## Inject 1 — 6:45 a.m. (10 min)

> EDR has flagged mass file encryption on three file servers in the corporate environment. A ransom note is present. Several employees arriving early report they cannot open shared drives. The core platform appears unaffected so far.

**Discussion prompts**
- Who declares this an incident, and what happens in the next 15 minutes?
- Who is in the room (or on the bridge) by 7:00? How do you reach them if email and chat may be compromised?
- Does anyone have authority to isolate the corporate network from the production platform right now? Who?

**Decisions to record:** Incident declared (Y/N, by whom) · Out-of-band channel · Who is notified first

---

## Inject 2 — 7:30 a.m. (15 min)

> The IR team confirms the attacker had domain-admin credentials and was active for at least nine days. They see evidence of lateral movement toward the production environment but no encryption there yet. Backups for the corporate file servers are intact; backups for the production database are on a system the attacker had access to, and their integrity is unknown.

**Discussion prompts**
- Do you take the production platform offline pre-emptively to protect it? Who makes that call, and what does it cost per hour?
- What do you tell employees at 8:00 a.m. when they arrive?
- Do you engage the cyber-insurance carrier and outside IR firm now? Does anyone know the policy's notice requirements?

**Decisions to record:** Platform offline (Y/N, by whom, when) · Staff message · Carrier/IR firm engaged

---

## Inject 3 — 9:15 a.m. (15 min)

> The ransom note names the threat-actor group and demands {{AMOUNT}} in cryptocurrency within 72 hours, threatening to publish stolen data. The IR firm finds evidence that roughly 40 GB was exfiltrated, including a directory that appears to contain customer records and HR files. A journalist has emailed the comms team asking about "reports of an outage."

**Discussion prompts**
- Who owns the ransom decision? What inputs do they need (sanctions check, recovery feasibility, legal view, insurer position)?
- Is this now a reportable data breach? Who decides, and what are the clocks (regulators, customers, partners, SEC if applicable)?
- What is the holding statement for the journalist, and who approves it?
- Does the board need to know now? Who tells them and how?

**Decisions to record:** Ransom stance and owner · Breach determination and notification plan · Media statement owner · Board notified (when/how)

---

## Inject 4 — Day 2, 2:00 p.m. (15 min)

> Production backups have been verified clean as of 11 days ago. Restoring means losing 11 days of transaction data unless it can be reconstructed from other sources. The platform has been offline for 30 hours. Three major customers are threatening contractual penalties. The attacker has posted a sample of the stolen data on a leak site.

**Discussion prompts**
- Restore from the 11-day-old backup and reconstruct, or continue forensic recovery of the live systems? Who decides and on what basis?
- How do you prioritize which customers and services come back first?
- What do you tell the customers threatening penalties, and who talks to them?
- What is the employee and public communication now that data is confirmed leaked?

**Decisions to record:** Recovery approach · Restoration priority · Customer communication owner · Public statement

---

## Inject 5 — Day 10 (10 min)

> Systems are restored. The regulator has opened an inquiry. The board has asked for a briefing on what happened, why, and what it will cost to prevent recurrence. Two senior engineers have given notice.

**Discussion prompts**
- What are the three things you tell the board, and what do you ask for?
- How do you support the team and prevent further attrition?
- What changes in the next 90 days?

---

## Debrief (20 min)

1. Which decisions had no clear owner?
2. Where did we lack information we would need in reality (backup status, insurance terms, contract penalties, notification clocks)?
3. What took longer than it should have?
4. What one change would have most reduced impact?

## Gaps this exercise commonly surfaces

- No pre-agreed authority to take production offline
- Ransom position never discussed before the incident
- Insurance notice requirements unknown to the people who would need to act
- Backup integrity assumed, not tested
- No out-of-band communication channel
- Board notification expectations undefined
