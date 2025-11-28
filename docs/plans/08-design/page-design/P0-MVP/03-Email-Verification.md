# 03. Email Verification

**Document:** TailCamp PRD - Page Design: Email Verification  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Email Verification page confirms that users have access to their email address. It displays verification status and provides options to resend the verification email.

**Page Type:** Public (No authentication required, but email required)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.3
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Design system
- **Feature:** None (Infrastructure: Email verification)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│                                         │
│         ✉️ Check Your Email             │
│                                         │
│  We've sent a verification link to:    │
│  user@example.com                      │
│                                         │
│  Click the link in the email to        │
│  continue.                              │
│                                         │
│  [Resend Email] (disabled for 60s)     │
│                                         │
│  Didn't receive it?                    │
│  - Check spam folder                   │
│  - Verify email address                │
│                                         │
│  [Change Email Address]                 │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. States

### 3.1 Initial State
- **Resend Email Button:** Disabled with 60-second countdown
- **Countdown Display:** "Resend in 59... 58... 57..."
- **Email Address:** Displayed (masked for privacy: u***@example.com)

### 3.2 After 60 Seconds
- **Resend Email Button:** Enabled
- **Button Text:** "Resend Email"

### 3.3 After Resend
- **Success Toast:** "Email sent! Check your inbox."
- **Countdown Reset:** Button disabled again for 60 seconds

### 3.4 Verified
- **Success Message:** "Email verified! Redirecting..."
- **Auto-redirect:** To Interest Selection after 2 seconds

### 3.5 Link Expired
- **Error Message:** "This verification link has expired."
- **Options:** [Resend Email] [Change Email Address]

---

## 4. Interactions

### 4.1 Resend Email
- **Initial:** Button disabled, countdown visible
- **After 60s:** Button enabled, clickable
- **On Click:** API call to resend email, success toast, countdown reset

### 4.2 Change Email Address
- **Action:** Opens modal or navigates to email change page
- **Validation:** New email format validation
- **Confirmation:** Requires password confirmation

### 4.3 Email Link Click
- **Auto-verification:** Link contains token, auto-verifies on page load
- **Success State:** Shows verification success, auto-redirects

---

## 5. Edge Cases

### 5.1 User Closes Tab
- **On Return:** Show "Resend" option if not verified
- **State Persistence:** Remember email address and verification status

### 5.2 Email Bounces
- **Error Display:** "Email delivery failed. Please check your email address."
- **Action:** Allow email address change

### 5.3 Multiple Resend Attempts
- **Rate Limiting:** Max 3 resends per hour
- **Error:** "Too many resend attempts. Please wait 1 hour."

---

## 6. Design Specifications

### 6.1 Components Used
- **Icon:** Email icon (✉️)
- **Button:** Primary (Resend Email), Secondary (Change Email)
- **Toast Notification:** Success message
- **Countdown Timer:** Visual countdown display

### 6.2 Visual Feedback
- **Success:** Green checkmark, success message
- **Error:** Red error message, retry option
- **Loading:** Spinner on button during API call

---

## 7. Accessibility

- **Screen Reader:** "Verification email sent to [email]. Check your inbox."
- **Keyboard Navigation:** Tab to Resend button, Enter to activate
- **Focus Management:** Focus on Resend button when enabled

---

## 8. Related Pages

- **Previous:** [02-Sign-Up](02-Sign-Up.md) - User just signed up
- **Next:** [04-Interest-Selection](04-Interest-Selection.md) - After email verified
- **Alternative:** [02-Sign-Up](02-Sign-Up.md) - User clicks "Change Email Address"

---

## 9. Acceptance Criteria

- [ ] Email address is displayed correctly
- [ ] Resend button countdown works correctly
- [ ] Email resend functionality works
- [ ] Verification link auto-verifies on click
- [ ] Auto-redirect works after verification
- [ ] Error states are handled gracefully

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.3 for detailed flow context.

