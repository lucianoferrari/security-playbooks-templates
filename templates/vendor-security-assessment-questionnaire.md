# Vendor Security Assessment Questionnaire

A right-sized third-party risk questionnaire. Long questionnaires get low-quality answers; this one is tiered so low-risk vendors answer 12 questions and high-risk vendors answer them all.

**Vendor:** {{NAME}} · **Service:** {{DESCRIPTION}} · **Business owner:** {{NAME}} · **Assessment date:** {{DATE}}

## Step 1 — Inherent risk tiering (completed by us, not the vendor)

| Factor | Score |
|---|---|
| Data sensitivity accessed (None=0, Internal=1, Confidential=2, Regulated PII/PCI/PHI=3) | |
| Integration depth (None=0, File exchange=1, API=2, Network/identity integration=3) | |
| Business criticality (Low=0, Medium=1, High=2, Mission-critical=3) | |
| User population affected (Internal team=0, Company-wide=1, Customers=2) | |
| AI/ML processing of our data (No=0, Yes=2) | |

**Total:** ___ → **Tier 1 (Low):** 0–3 · **Tier 2 (Medium):** 4–7 · **Tier 3 (High):** 8+

Tier 1 vendors answer Section A only. Tier 2 answer A–C. Tier 3 answer all sections and provide evidence.

---

## Section A — Core (all vendors)

1. Do you hold a current SOC 2 Type II, ISO 27001, PCI DSS AOC, or equivalent? Please attach.
2. Do you have a named security leader and a documented information security program?
3. Is multi-factor authentication enforced for all employee access to systems that handle customer data?
4. Is customer data encrypted in transit (TLS 1.2+) and at rest?
5. Do you perform at least annual third-party penetration testing? Date of last test and summary of critical/high findings status.
6. Do you have a documented incident response plan, and will you notify us of a security incident affecting our data within {{72}} hours?
7. Where is our data stored and processed (countries/regions)?
8. Do you use subprocessors with access to our data? Provide the list.
9. Do you have a vulnerability management program with defined remediation SLAs?
10. Do you carry cyber liability insurance? Coverage amount?
11. Have you experienced a security breach affecting customer data in the past 36 months? Describe.
12. Will you agree to our standard security and data-protection contract terms?

## Section B — Access and data handling (Tier 2+)

13. Describe role-based access control and the joiner/mover/leaver process for your staff.
14. Is privileged access to production logged, reviewed, and time-bound?
15. How is customer data logically segregated from other customers' data?
16. What is your data retention and deletion process at contract end? Will you certify deletion?
17. Do you conduct background checks on staff with access to customer data?
18. Describe security awareness training frequency and content.

## Section C — Engineering and operations (Tier 2+)

19. Describe your secure development lifecycle (code review, SAST/DAST, dependency scanning).
20. How are secrets managed (no hard-coded credentials, rotation)?
21. Describe logging and monitoring coverage and retention for security events.
22. What are your RTO/RPO targets and when was your DR plan last tested?
23. Describe change-management controls for production.

## Section D — AI and emerging risk (Tier 3, or any vendor using AI on our data)

24. Do you use our data to train or fine-tune AI/ML models? Can we opt out?
25. Which AI model providers or sub-processors receive our data? Under what contractual terms?
26. How do you prevent prompt injection, data leakage, and unauthorized actions in AI features?
27. Is there human review for AI-driven decisions that affect our customers or operations?
28. How are AI features logged and auditable?

## Section E — Evidence requested (Tier 3)

- [ ] SOC 2 Type II report (with bridge letter if >12 months)
- [ ] Penetration test executive summary
- [ ] Information security policy summary
- [ ] Business continuity / DR test summary
- [ ] Subprocessor list and data-flow diagram
- [ ] Insurance certificate

---

## Scoring and decision (completed by us)

| Area | Rating (Satisfactory / Needs improvement / Unsatisfactory) | Notes |
|---|---|---|
| Governance & compliance | | |
| Access control | | |
| Data protection | | |
| Secure engineering | | |
| Resilience | | |
| Incident response | | |
| AI risk | | |

**Residual risk:** Low / Medium / High
**Decision:** Approve / Approve with conditions / Reject
**Conditions / remediation required:** {{LIST}}
**Reassessment due:** {{DATE — annually for Tier 3, every 2 years for Tier 2, on renewal for Tier 1}}

**Assessed by:** ______________ **Business owner acceptance:** ______________
