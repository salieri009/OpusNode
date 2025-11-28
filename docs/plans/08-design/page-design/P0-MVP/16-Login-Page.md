# 16. Login Page

**Document:** TailCamp PRD - Page Design: Login Page  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Login Page allows existing users to authenticate and access their account. It includes email/password login and social authentication options.

**Page Type:** Public (No authentication required)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-Sign-Up](02-Sign-Up.md) - Similar form structure
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Design system
- **Feature:** None (Infrastructure: User authentication)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│                                         │
│  Welcome Back                            │
│                                         │
│  Email: [________________]              │
│  Password: [________________] [👁]      │
│                                         │
│  ☐ Remember me                          │
│  [Forgot Password?]                      │
│                                         │
│  [Sign In]                               │
│                                         │
│  ─────────── or ───────────             │
│                                         │
│  [Continue with Google]                 │
│  [Continue with GitHub]                 │
│                                         │
│  Don't have an account?                 │
│  [Sign Up]                               │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Form Fields

### 3.1 Email
- **Type:** Email input
- **Validation:** Real-time email format validation

### 3.2 Password
- **Type:** Password input with visibility toggle
- **Forgot Password:** Link to password reset

### 3.3 Remember Me
- **Type:** Checkbox
- **Purpose:** Keep user logged in

---

## 4. Interactions

### 4.1 Social Authentication
- **Google OAuth:** Redirect to Google
- **GitHub OAuth:** Redirect to GitHub

### 4.2 Form Submission
- **Loading:** Spinner on submit button
- **Success:** Redirect to dashboard
- **Error:** "Invalid email or password"

---

## 5. Related Pages

- **Next:** [18-Solo-Dashboard](18-Solo-Dashboard.md) - After successful login
- **Alternative:** [02-Sign-Up](02-Sign-Up.md) - User clicks "Sign Up"

---

## 6. Acceptance Criteria

- [ ] Email/password login works
- [ ] Social authentication works
- [ ] Error messages are clear
- [ ] Forgot password link works
- [ ] Remember me checkbox works

---

**Next Step:** Review [02-Sign-Up](02-Sign-Up.md) for similar form patterns.

