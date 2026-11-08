# Business Email Compromise (BEC) Playbook

**Severity:** High (SEV-2); escalate to SEV-1 if funds were transferred or an executive/finance account is involved
**Owner:** {{SECURITY_OPERATIONS_LEAD}}

## 1. Triggers

- User reports a suspicious payment/wire request, invoice change, or "urgent" executive ask
- Mailbox rules detected that forward, delete, or hide messages (classic persistence)
- Impossible-travel or anomalous sign-in on a finance, HR, or executive mailbox
- Partner/customer reports receiving phishing from one of our addresses
- Vendor reports a bank-detail change they didn't request

## 2. First 30 minutes

1. **Stop the money.** If a payment is pending or recently sent, contact the bank's fraud line immediately and request a recall/SWIFT freeze. Time matters more than anything else in this playbook.
2. **Contain the account:** force sign-out of all sessions, reset password, revoke refresh tokens and app passwords, re-register MFA.
3. **Remove persistence:** delete malicious inbox rules, forwarding addresses, delegated access, and OAuth app consents.
4. **Preserve evidence:** export mailbox audit logs, sign-in logs, and the phishing/lure messages with full headers.

## 3. Scope

- Which mailboxes did the attacker read, send from, or set rules on?
- Were any **other** accounts compromised via internal phishing from the first account?
- Was sensitive data accessed (payroll, contracts, customer PII)? This drives notification obligations.
- Were any look-alike domains registered to impersonate us? (Check certificate transparency and domain monitoring.)

## 4. Eradication

- Hunt for the same lure across the organization and purge from all mailboxes
- Block sender domains/IPs and the attacker's payment-redirect indicators
- Validate conditional-access policies (block legacy auth, require phishing-resistant MFA for finance and executives)
- Review and tighten who can change vendor bank details and the verification required (callback to a known number — never one from the email)

## 5. Financial recovery

- File a complaint with the FBI IC3 (US) within 72 hours — the Recovery Asset Team can freeze funds in many domestic cases
- Notify cyber-insurance carrier (social-engineering / funds-transfer coverage often has short notice windows)
- Coordinate with receiving bank through our bank's fraud team

## 6. Communications

- Finance and AP teams: what happened, what to verify, heightened-vigilance period
- Affected vendors/customers: that our account was compromised and what messages to disregard
- Legal: breach-notification assessment if personal data was accessed
- Executives: summary, exposure, and control changes

## 7. Decision log

| Time (UTC) | Decision | Decided by | Rationale |
|---|---|---|---|
| | | | |

## 8. Prevention checklist (post-incident)

- [ ] Phishing-resistant MFA (FIDO2/passkeys) for executives, finance, HR, IT admins
- [ ] Block automatic external forwarding; alert on new inbox rules
- [ ] DMARC at `p=reject` for all sending domains
- [ ] Dual-control and out-of-band verification for all payment-detail changes
- [ ] Executive impersonation banners / external-sender tagging
- [ ] Quarterly BEC tabletop with Finance
