# 20. Terms & Privacy

**Document:** TailCamp PRD - Page Design: Terms & Privacy  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Terms & Privacy page displays legal documents including Terms of Service and Privacy Policy. It's required for GDPR compliance and user consent.

**Page Type:** Public (No authentication required)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP - Legal requirement)

**Related Documents:**
- [09-Security: Compliance](../../../09-security/02-Compliance-Legal.md) - Legal requirements
- **Feature:** None (Infrastructure: Legal compliance requirement)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
├─────────────────────────────────────────┤
│                                         │
│  Terms of Service & Privacy Policy      │
│                                         │
│  [Terms of Service] [Privacy Policy]    │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │                                   │ │
│  │  [Legal Document Content]          │ │
│  │                                   │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Last Updated: 2025-11-28              │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Content Sections

### 3.1 Tab Navigation
- **Terms of Service:** Legal terms
- **Privacy Policy:** Data handling, GDPR

### 3.2 Document Display
- **Format:** Scrollable text content
- **Sections:** Numbered sections, headings
- **Last Updated:** Date display

### 3.3 Consent (If accessed from signup)
- **Checkbox:** "I agree to Terms & Privacy Policy"
- **Link:** Opens this page

---

## 4. Design Specifications

### 4.1 Components Used
- **Tabs:** Switch between Terms and Privacy
- **Scrollable Content:** Long legal text
- **Back Button:** Return to previous page

### 4.2 Typography
- **Legal Text:** Readable font, proper line spacing
- **Headings:** Clear hierarchy

---

## 5. Related Pages

- **From:** [02-Sign-Up](02-Sign-Up.md) - Terms checkbox link
- **Back:** Any page (via back button)

---

## 6. Acceptance Criteria

- [ ] Terms and Privacy content displays correctly
- [ ] Tab switching works
- [ ] Content is readable
- [ ] Last updated date is accurate
- [ ] Mobile layout is responsive

---

**Next Step:** Review [09-Security: Compliance](../../09-security/02-Compliance-Legal.md) for legal requirements.

