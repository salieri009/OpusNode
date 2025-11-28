# 02. Sign Up

**Document:** TailCamp PRD - Page Design: Sign Up  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Sign Up page allows new users to create an account. It includes form validation, password strength checking, and social authentication options.

**Page Type:** Public (No authentication required)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.2
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Design system
- **Feature:** None (Infrastructure: User authentication)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
│                                         │
│  Create Your Account                    │
│                                         │
│  Email: [________________]              │
│  Name:  [________________]              │
│  Password: [________________] [👁]      │
│  Confirm:  [________________]           │
│                                         │
│  ☐ I agree to Terms & Privacy Policy   │
│                                         │
│  [Create Account]                       │
│                                         │
│  ─────────── or ───────────             │
│                                         │
│  [Continue with Google]                 │
│  [Continue with GitHub]                 │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Form Fields

### 3.1 Email
- **Type:** Email input
- **Validation:** Real-time email format validation
- **Error:** "This email is already registered. [Sign in instead]"

### 3.2 Name
- **Type:** Text input
- **Validation:** 2-50 characters, alphanumeric + spaces
- **Error:** "Name must be 2-50 characters"

### 3.3 Password
- **Type:** Password input with visibility toggle
- **Validation:** Min 8 chars, 1 uppercase, 1 number
- **Feedback:** Strength indicator (Weak/Medium/Strong)
- **Error:** Show requirements checklist

### 3.4 Confirm Password
- **Type:** Password input
- **Validation:** Must match password field
- **Error:** "Passwords do not match"

### 3.5 Terms Checkbox
- **Type:** Checkbox
- **Required:** Yes
- **Link:** Opens Terms & Privacy modal/page

---

## 4. Interactions

### 4.1 Real-time Validation
- ✅ Green checkmark when field is valid
- ❌ Red error message below invalid field
- Password strength updates as user types

### 4.2 Social Authentication
- **Google OAuth:** Redirect to Google, callback to app
- **GitHub OAuth:** Redirect to GitHub, callback to app

### 4.3 Form Submission
- Button shows loading spinner on submit
- Success: "Account created! Check your email."
- Auto-redirect to email verification after 2 seconds

---

## 5. States

### 5.1 Default
- All fields empty, submit button disabled
- Placeholder text visible

### 5.2 Validating
- Real-time validation feedback
- Submit button enabled when all fields valid

### 5.3 Submitting
- Loading spinner on submit button
- All fields disabled
- "Creating account..." message

### 5.4 Success
- Success message displayed
- Auto-redirect countdown (2 seconds)

### 5.5 Error
- Error message displayed
- Fields remain editable
- Retry button available

---

## 6. Error Handling

### 6.1 Validation Errors
- **Email exists:** "This email is already registered. [Sign in instead]"
- **Weak password:** Show requirements checklist
- **Network error:** "Connection failed. Please try again."

### 6.2 Field-level Errors
- Error message appears below invalid field
- Field border turns red
- Error icon displayed

---

## 7. Design Specifications

### 7.1 Components Used
- **Input Fields:** Text, Email, Password with validation
- **Checkbox:** Terms agreement
- **Buttons:** Primary (Create Account), Social (Google, GitHub)
- **Back Button:** Navigate to previous page

### 7.2 Responsive Design
- **Mobile:** Full-width inputs, stacked layout
- **Desktop:** Centered form, max-width container

---

## 8. Accessibility

- **Keyboard Navigation:** Tab order through all fields
- **Screen Reader:** Labels associated with inputs
- **Focus Indicators:** 2px blue outline on focus
- **Error Announcements:** Screen reader announces errors

---

## 9. Related Pages

- **Previous:** [01-Landing-Page](01-Landing-Page.md) - User came from landing
- **Next:** [03-Email-Verification](03-Email-Verification.md) - After successful signup
- **Alternative:** [16-Login-Page](16-Login-Page.md) - User clicks "Sign in instead"

---

## 10. Acceptance Criteria

- [ ] All form validations work correctly
- [ ] Password strength indicator updates in real-time
- [ ] Social authentication redirects work
- [ ] Error messages are clear and actionable
- [ ] Form is fully keyboard accessible
- [ ] Mobile layout is responsive

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.2 for detailed flow context.

