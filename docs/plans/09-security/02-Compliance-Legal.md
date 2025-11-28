# Legal, Compliance & Privacy

**Document:** TailCamp PRD - Legal & Compliance  
**Version:** 1.0  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document outlines the legal and regulatory requirements for TailCamp, covering data privacy, content moderation, intellectual property, and terms of service.

**Critical:** These items are **blockers for public launch**. Private beta may proceed with basic ToS/Privacy Policy.

---

## 2. Data Privacy & Protection

### GDPR Compliance (EU Users)

**Scope:** Applies if targeting EU users or processing EU citizen data.

| Requirement | Implementation | Timeline |
|:------------|:---------------|:---------|
| **Lawful Basis** | Consent for marketing; Legitimate Interest for service delivery | Month 1 |
| **Right to Access** | User dashboard with "Download My Data" feature | Month 2 |
| **Right to Erasure** | "Delete Account" with 30-day grace period | Month 2 |
| **Data Portability** | Export as JSON/CSV | Month 3 |
| **Privacy by Design** | Minimize data collection, pseudonymization for analytics | Month 1 |
| **DPO Appointment** | Required if >250 employees OR high-risk processing | N/A (small scale) |
| **Cookie Consent** | Banner for non-essential cookies | Month 1 |

**Action Item:** Draft Privacy Policy using [GDPR.eu template](https://gdpr.eu/privacy-notice/).

### CCPA Compliance (California Users)

**Scope:** Applies if >$25M revenue OR >50K CA consumers OR >50% revenue from selling data.

-   **Likely NOT applicable for MVP** - Monitor threshold.
-   If applicable: "Do Not Sell My Info" link, disclosure of data categories.

### Data Retention Policy

| Data Type | Retention Period | Rationale |
|:----------|:-----------------|:----------|
| User accounts (active) | Indefinite | Ongoing service |
| User accounts (deleted) | 30 days (soft delete) | Allow recovery |
| Chat logs | 90 days | Debugging, compliance |
| Assessment results | 2 years | ML training, user history |
| Analytics (anonymized) | 3 years | Business intelligence |

---

## 3. Content Moderation & User Safety

### Chat Moderation

-   **Automated Filtering:** Profanity filter, hate speech detection (e.g., Perspective API).
-   **User Reporting:** "Report Message" button, reviewed within 24 hours.
-   **Sanctions:** Warning → 7-day suspension → Permanent ban.

### Code of Conduct

Required for group interactions:
-   No harassment, discrimination, or hate speech.
-   No sharing of illegal content or copyrighted materials without permission.
-   No spam, phishing, or malicious code.

**Action Item:** Create `Terms of Service > Community Guidelines` section.

### COPPA (Children's Privacy)

**Scope:** If users <13 years old.

-   **Recommendation:** Set minimum age to 13+ to avoid COPPA requirements.
-   Add age gate: "You must be 13 or older to use TailCamp."

---

## 4. Intellectual Property

### User-Generated Content

**License Grant:** Users grant TailCamp a non-exclusive, royalty-free license to display their projects/portfolios.

**Ownership:** Users retain all rights to their code and content.

**Portfolio Visibility:** Users control public/private status.

### Third-Party Content

-   **Learning Resources:** Links to external content (YouTube, blogs) with attribution.
-   **Fair Use:** Snippets for educational purposes with proper citation.
-   **DMCA Compliance:** Designated agent, takedown process for copyright claims.

**Action Item:** Register DMCA agent with U.S. Copyright Office.

---

## 5. Terms of Service (ToS)

### Required Sections

1.  **Service Description:** What TailCamp provides.
2.  **User Accounts:** Registration requirements, account security.
3.  **Acceptable Use:** Prohibited activities.
4.  **Disclaimers:** "As-is" service, no guarantees on job placement.
5.  **Limitation of Liability:** Cap damages to subscription fees (if paid).
6.  **Dispute Resolution:** Arbitration clause (if in US).
7.  **Governing Law:** Specify jurisdiction (e.g., Delaware, US).
8.  **Termination:** Right to suspend/terminate accounts.

**Action Item:** Use [Termly](https://termly.io) or attorney to draft ToS by Month 1.

---

## 6. Accessibility & Inclusion

### WCAG 2.1 AA Compliance

-   **Legal Requirement:** ADA (US), AODA (Canada), EN 301 549 (EU).
-   **Minimum Standard:** Color contrast 4.5:1, keyboard navigation, screen reader support.

**Action Item:** Accessibility audit before public launch (Month 3).

---

## 7. International Considerations

### Multi-Jurisdiction Strategy

| Region | Key Laws | Launch Priority |
|:-------|:---------|:----------------|
| **US** | COPPA, CAN-SPAM | Phase 1 (Month 3) |
| **EU** | GDPR, ePrivacy | Phase 1 (Month 3) |
| **UK** | UK GDPR, DPA 2018 | Phase 2 (Month 6) |
| **Canada** | PIPEDA | Phase 2 (Month 6) |
| **Australia** | Privacy Act 1988 | Phase 3 (Month 9+) |

**Recommendation:** Start with US + EU only for MVP.

---

## 8. Compliance Checklist (Pre-Launch)

- [ ] Privacy Policy published and linked in footer
- [ ] Terms of Service published and linked in footer
- [ ] Cookie consent banner (GDPR)
- [ ] Age gate (13+) on signup
- [ ] "Download My Data" feature (GDPR)
- [ ] "Delete Account" feature (GDPR)
- [ ] DMCA agent registered (if hosting user content)
- [ ] Content moderation process documented
- [ ] Incident response plan for data breaches (72-hour GDPR requirement)

---

**Next Step:** Review [Security & Privacy](security-privacy.md) for technical implementation.
