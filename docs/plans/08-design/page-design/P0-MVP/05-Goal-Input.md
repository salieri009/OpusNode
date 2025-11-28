# 05. Goal Input

**Document:** TailCamp PRD - Page Design: Goal Input  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Goal Input page collects users' learning objectives for the next 3 months. This information is used to personalize the assessment and curriculum recommendations.

**Page Type:** Authenticated  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.5
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Section 2.1 (Goal Input)
- **[F-001: AI Assessment](../../../03-features/F-001-AI-Assessment.md)** - Feature: Goal input used for personalized assessment and curriculum recommendations

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
│                                         │
│  What do you want to achieve            │
│  in the next 3 months?                  │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │                                    │ │
│  │  [Type your goal here...]          │ │
│  │                                    │ │
│  │                                    │ │
│  └───────────────────────────────────┘ │
│  150 characters minimum                 │
│  (0/150)                                │
│                                         │
│  💡 Examples:                           │
│  • Build a full-stack e-commerce app   │
│  • Contribute to open source projects  │
│  • Land a job as a backend developer  │
│                                         │
│  [Continue to Assessment] (disabled)   │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Form Field

### 3.1 Textarea
- **Type:** Multi-line text input
- **Auto-expand:** Up to 6 lines, then scrolls
- **Character Limit:** 
  - Minimum: 150 characters
  - Maximum: 500 characters
- **Placeholder:** "Type your goal here..."

### 3.2 Character Counter
- **Display:** "(X/150)" or "(X/500)"
- **Color:** 
  - Gray: 0-149 characters
  - Red: < 150 characters (invalid)
  - Green: 150-500 characters (valid)
  - Red: > 500 characters (invalid)

---

## 4. Interactions

### 4.1 Real-time Validation
- **Character Counter:** Updates as user types
- **Visual Feedback:**
  - Valid: Green checkmark, green border
  - Invalid: Red border, error message
- **Button State:** Enabled when 150-500 characters

### 4.2 Suggestions
- **Context-Aware:** Based on selected interests
- **Examples:**
  - If "Backend" selected → "Build REST APIs", "Learn Node.js"
  - If "Frontend" selected → "Build React apps", "Learn TypeScript"
- **Display:** Below textarea, clickable to insert

### 4.3 Auto-expand
- **Behavior:** Textarea grows up to 6 lines
- **After 6 Lines:** Textarea becomes scrollable
- **Animation:** Smooth height transition

---

## 5. States

### 5.1 Empty
- Placeholder text visible
- Character counter: "(0/150)"
- Button disabled
- No suggestions shown

### 5.2 Typing (< 150 chars)
- Character counter updates
- Counter turns red when < 150
- Suggestions appear based on interests
- Button disabled
- Error message: "Please enter at least 150 characters"

### 5.3 Valid (150-500 chars)
- Green checkmark appears
- Character counter green
- Button enabled
- Suggestions still visible

### 5.4 Invalid (> 500 chars)
- Red border on textarea
- Character counter red
- Button disabled
- Error message: "Maximum 500 characters. Please summarize your goals."

---

## 6. Error Messages

### 6.1 Too Short
- **Message:** "Please enter at least 150 characters to help us understand your goals."
- **Display:** Below textarea, red text

### 6.2 Too Long
- **Message:** "Maximum 500 characters. Please summarize your goals."
- **Display:** Below textarea, red text

---

## 7. Design Specifications

### 7.1 Components Used
- **Textarea:** Multi-line input with validation
- **Character Counter:** Real-time character count display
- **Suggestions:** Clickable suggestion chips
- **Button:** Primary CTA (Continue to Assessment)
- **Back Button:** Navigate to previous step

### 7.2 Visual Feedback
- **Valid State:** Green border, checkmark icon
- **Invalid State:** Red border, error icon
- **Typing Indicator:** Character counter updates smoothly

---

## 8. Accessibility

- **Keyboard Navigation:** Tab to textarea, type to input
- **Screen Reader:** "Goal input field. 150 characters minimum. Currently 0 characters."
- **Focus Indicators:** 2px blue outline on focus
- **Error Announcements:** Screen reader announces errors

---

## 9. Related Pages

- **Previous:** [04-Interest-Selection](04-Interest-Selection.md) - After interest selection
- **Next:** [06-Assessment-Intro](06-Assessment-Intro.md) - User clicks "Continue to Assessment"
- **Back:** [04-Interest-Selection](04-Interest-Selection.md) - User clicks back button

---

## 10. Acceptance Criteria

- [ ] Character counter updates in real-time
- [ ] Validation works correctly (min 150, max 500)
- [ ] Suggestions appear based on selected interests
- [ ] Button enables/disables based on validation
- [ ] Error messages are clear and helpful
- [ ] Textarea auto-expands correctly

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.5 for detailed flow context.

