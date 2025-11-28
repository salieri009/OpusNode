# 17. User Profile / Settings

**Document:** TailCamp PRD - Page Design: User Profile / Settings  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The User Profile / Settings page allows users to manage their account information, update password, adjust privacy settings, and view their activity history.

**Page Type:** Authenticated  
**Complexity:** ⚡ Medium  
**Priority:** P1 (Post-MVP)

**Related Documents:**
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Design system
- **Feature:** None (Infrastructure: User account management)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
├─────────────────────────────────────────┤
│                                         │
│  Profile & Settings                      │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │ Profile Picture                    │ │
│  │ [Upload] [Remove]                  │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Name: [________________]              │
│  Email: [________________]              │
│                                         │
│  Change Password:                       │
│  Current: [________________]            │
│  New:     [________________]            │
│  Confirm: [________________]            │
│                                         │
│  Privacy Settings:                      │
│  ☐ Share assessment results with team  │
│  ☐ Allow profile visibility            │
│                                         │
│  [Save Changes]                         │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Sections

### 3.1 Profile Information
- Name, email
- Profile picture upload
- Bio/description (optional)

### 3.2 Password Change
- Current password
- New password
- Confirm password
- Strength indicator

### 3.3 Privacy Settings
- Share assessment results
- Profile visibility
- Contact information sharing

### 3.4 Account Management
- Delete account
- Download data (GDPR)
- Export portfolio

---

## 4. Related Pages

- **Previous:** Any authenticated page (via settings menu)
- **Next:** Returns to previous page after save

---

## 5. Acceptance Criteria

- [ ] Profile updates work correctly
- [ ] Password change works
- [ ] Privacy settings save correctly
- [ ] Account deletion works with confirmation
- [ ] Data export works

---

**Next Step:** Review [01-UX-UI-Principles](../01-UX-UI-Principles.md) for form design patterns.

