# Ransomware Response Playbook

**Severity:** Critical (SEV-1) by default
**Owner:** {{INCIDENT_COMMANDER_ROLE}}
**Last exercised:** {{DATE}}

## 1. Triggers

Activate this playbook when any of the following is confirmed or strongly suspected:

- Ransom note, wallpaper change, or extortion email referencing company data
- Mass file renames/encryption observed by EDR, file-integrity monitoring, or users
- Backup jobs failing or backup repositories deleted/encrypted
- Known ransomware precursors: Cobalt Strike beacons, mass `vssadmin delete shadows`, disabled EDR sensors, unusual domain-admin activity at odd hours

## 2. Roles

| Role | Responsibilities |
|---|---|
| Incident Commander (IC) | Owns decisions, timeline, and comms cadence |
| Technical Lead | Directs containment, forensics, and recovery |
| Communications Lead | Internal updates, customer/partner comms, media holding statement |
| Legal / Privacy | Breach-notification analysis, law-enforcement liaison, privilege |
| Executive Sponsor | Business decisions (shutdowns, ransom stance), board updates |
| Scribe | Maintains the decision log (Section 9) |

## 3. First 60 minutes

1. **Declare** the incident and open a dedicated, out-of-band channel (assume email and chat may be compromised).
2. **Isolate** affected hosts at the network/EDR level — do **not** power them off (preserves memory for forensics).
3. **Protect backups**: disconnect or lock backup repositories, revoke backup service-account sessions, verify immutability.
4. **Freeze privileged access**: reset domain-admin and tier-0 credentials, disable suspicious accounts, revoke tokens.
5. **Engage** cyber-insurance carrier and retained IR firm per policy (many carriers require notice before engaging responders).
6. **Preserve evidence**: ransom note, sample encrypted file, EDR telemetry, firewall/VPN/IdP logs.

## 4. Scoping

- Identify patient zero and initial access vector (phishing, exposed RDP/VPN, vulnerable edge appliance, supply chain).
- Enumerate encrypted systems, dwell time, and lateral-movement paths.
- Determine **data exfiltration** indicators (large outbound transfers, cloud-storage tooling, rclone/MEGA/FTP) — this drives the notification analysis.
- Classify affected data: regulated (PCI, PII, PHI), customer, IP, credentials.

## 5. Containment

- Block C2 indicators at DNS, proxy, and firewall.
- Rotate **all** credentials for compromised tiers; assume Kerberos tickets and cached secrets are burned (consider KRBTGT double reset).
- Disable remote-access paths used by the attacker until hardened.
- Hunt for persistence: scheduled tasks, services, new accounts, GPO changes, startup items, cloud OAuth grants.

## 6. Eradication & recovery

- Rebuild from known-good images; do not "clean" encrypted hosts.
- Restore from immutable/offline backups **after** verifying restore points predate the compromise.
- Prioritize recovery by business impact (use the BIA tier list in `{{BIA_LINK}}`).
- Validate restored systems with EDR in blocking mode before reconnecting to production.

## 7. Ransom decision framework

The decision to engage with or pay a threat actor is an **executive and legal** decision, not a security one. Prepare the inputs:

- Sanctions check (OFAC) on the threat-actor group — payment to a sanctioned entity may be illegal
- Recovery feasibility and time-to-restore without decryption
- Exfiltration confirmed? (Payment rarely prevents data publication)
- Insurance carrier position and approved negotiator
- Board/regulator expectations

Document the decision and its rationale in the decision log regardless of outcome.

## 8. Communications

| Audience | Owner | Timing |
|---|---|---|
| Executive team | IC | Hourly during first 24h, then per cadence |
| All staff | Comms Lead | Within 4h — what to do, what not to touch |
| Customers / partners | Comms + Legal | As contractually required; coordinate messaging |
| Regulators | Legal | Per jurisdiction (e.g., 72h GDPR; state breach laws; PCI brand rules; SEC 8-K materiality for public companies) |
| Law enforcement | Legal | FBI/IC3 or local equivalent — early engagement is usually beneficial |
| Board | Executive Sponsor | Initial brief within 24h; written update at closure |

## 9. Decision log (required)

| Time (UTC) | Decision | Options considered | Decided by | Rationale |
|---|---|---|---|---|
| | | | | |

## 10. Post-incident

- Blameless post-incident review within 10 business days
- Root-cause and control-gap analysis mapped to a framework (NIST CSF / CIS Controls)
- Update detections, hardening baselines, and this playbook
- Brief the board on lessons learned and funded remediation

## Appendix: quick-reference commands and checks

- Confirm shadow-copy deletion attempts, EDR tamper alerts, and mass SMB write patterns in your SIEM
- Pull authentication logs for the 30 days prior to the first encryption event
- Check identity provider for new MFA devices, app registrations, and consent grants
