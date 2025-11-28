# 19. Error Page

**Document:** TailCamp PRD - Page Design: Error Page  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Error Page handles 404 (Not Found) and other error states. It provides clear messaging and navigation options to help users recover from errors.

**Page Type:** Public/Authenticated (Context-dependent)  
**Complexity:** 🟢 Low  
**Priority:** P2 (Future)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 4 (Error States)
- **Feature:** None (Infrastructure: Error handling for all pages)

---

## 2. Page Structure

### 2.1 Layout (404)

```
┌─────────────────────────────────────────┐
│                                         │
│           404                            │
│         Page Not Found                  │
│                                         │
│  The page you're looking for           │
│  doesn't exist.                         │
│                                         │
│  [Go Home]                              │
│  [Back to Previous Page]                │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Error Types

### 3.1 404 Not Found
- **Message:** "Page not found"
- **Actions:** Go Home, Back button

### 3.2 500 Server Error
- **Message:** "Something went wrong"
- **Actions:** Retry, Go Home, Contact Support

### 3.3 403 Forbidden
- **Message:** "You don't have permission"
- **Actions:** Go Home, Contact Admin

---

## 4. Design Specifications

### 4.1 Visual
- **Icon:** Error icon or illustration
- **Message:** Clear, friendly error message
- **Actions:** Primary CTA (Go Home), Secondary (Back)

### 4.2 Accessibility
- **Screen Reader:** "Error 404. Page not found."
- **Keyboard Navigation:** Tab to action buttons

---

## 5. Related Pages

- **Primary:** [01-Landing-Page](01-Landing-Page.md) - "Go Home" action
- **Alternative:** Browser back button

---

## 6. Acceptance Criteria

- [ ] Error messages are clear
- [ ] Navigation actions work
- [ ] Page is accessible
- [ ] Mobile layout is responsive

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 4 for error handling patterns.

