# Tabletop Exercise Pack

Four ready-to-run tabletop exercises for executive and technical audiences. Each scenario is a 60–90 minute facilitated discussion with timed injects, discussion prompts, and the decisions the group must make. No technology is required beyond a timer and someone taking notes.

| Scenario | Audience | Time | Primary playbook exercised |
|---|---|---|---|
| [Ransomware during month-end close](ransomware-month-end.md) | Executive | 90 min | [Ransomware response](../playbooks/ransomware-response-playbook.md) |
| [Business email compromise: the redirected payout](bec-redirected-payout.md) | Executive + Finance | 60 min | [BEC playbook](../playbooks/business-email-compromise-playbook.md) |
| [GenAI assistant leaks customer data](genai-assistant-data-leak.md) | Executive + Product + Engineering | 75 min | [GenAI incident playbook](../playbooks/genai-security-incident-playbook.md) |
| [Critical vendor breached](vendor-breach.md) | Executive + Legal + Procurement | 60 min | [Vendor questionnaire](../templates/vendor-security-assessment-questionnaire.md) |

## How to run one

**Before**
- Pick the scenario and tailor the bracketed details (`{{SYSTEM}}`, `{{VENDOR}}`) to your environment. Realism is what makes people engage.
- Invite the people who would actually be in the room: CEO or COO, CFO, General Counsel, CISO/CIO, Head of Comms, and the business owner of the affected system. Eight to twelve people is ideal.
- Assign a **facilitator** (reads injects, keeps time, asks the questions) and a **scribe** (records decisions, open questions, and gaps). The CISO should not facilitate their own exercise; they should participate.
- Send a one-paragraph pre-read: purpose, ground rules, duration. Do not send the scenario.

**During**
- Ground rules: no blame, no "we'd never let that happen," assume the inject is true, decisions are made with the information available at that moment.
- Read each inject aloud. Give the group the time allotted. Ask the discussion prompts. Push for an actual decision before moving on.
- The scribe captures every decision and every moment someone says "I don't know who owns that."

**After**
- Within a week, circulate a one-page after-action report: what went well, gaps found, owners and dates for fixes.
- Update the relevant playbook with what you learned.
- Put the next exercise on the calendar. Twice a year for executives; quarterly rotation of scenarios for the security team.

## Facilitator tips

- The goal is to find gaps, not to pass. A tabletop where everything goes smoothly was too easy.
- When the group stalls, ask: "Who makes that call? What do they need to know to make it? How do they find that out right now?"
- Watch for decisions that require someone who is not in the room (a board member, outside counsel, the bank). Note how long it would take to reach them.
- Keep the ransom-payment, customer-notification, and take-the-system-offline debates going longer than is comfortable. Those are the decisions that are hardest in real life.

## After-action report template

```
Exercise:            {{SCENARIO}} — {{DATE}}
Participants:        {{ROLES}}
What went well:      •
Gaps identified:     •  (owner, due date)
Decisions made:      •
Open questions:      •
Playbook updates:    •
Next exercise:       {{DATE}} — {{SCENARIO}}
```
